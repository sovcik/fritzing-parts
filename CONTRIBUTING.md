<<<<<<< HEAD
# Contributing a new part

Fork and clone the repository:

    git clone git@github.com:your-username/fritzing-parts.git

Create a branch for the part you want to contribute:

    git branch your-part
    git checkout your-part

Create the fzp file.  
Create the breadboard, schematic and pcb svg files.  

## FZPZ
Fzpz are ment to transfer parts between fritzing users.
Fritzing cannot work with fzpz-parts in its folder-structure.

You have to extract the fzpz:

### fzpzclean-script:
You can use a simple python clean script to split the fzpz:
https://github.com/fritzing/fritzing-parts/blob/master/part-gen-scripts/misc_scripts/fzpzclean.py
*howto is in the script*

### Handwork
*will follow soon*
    
    
## Pull-Request
Please put the svgs and the fzp-file, in the belonging directories:

- fzp -> core-folder
- breadboard svg -> svg/breadboard/ 
- schematic svg -> svg/schematic/ 
- pcb svg -> svg/pcb/ 

All parts has to have a resonable svg for each view.
We need to have a consistent database of parts.

Thanks for contributing. 

Push to your fork and [submit a pull request](https://github.com/fritzing/fritzing-parts/compare/)

# Contributing a fix
fritzing has an obsolete mechanism. 
*will follow soon*
=======
## How to contribute a new part

1. Fork and clone the repository:

        git clone git@github.com:your-username/fritzing-parts.git

2. Create a branch for the part you want to contribute:

        git branch your-part
        git checkout your-part

3. Place the `.fzp` file in the core folder and the related `.svg` in the view-specific folders:

        description.fzp -> core/
        breadboard_view.svg -> svg/breadboard/ 
        schematic_view.svg -> svg/schematic/ 
        pcb_view.svg -> svg/pcb/ 

    See below for exporting your `.fzpz` file to the correct structure.

4. Then test and push!

    In order to make Fritzing recognize the new part, run Fritzing and select _Part > Rebuild parts database..._. The part will now be included in the database/index, and become available in the library window.

## How to export your part from within Fritzing (FZPZ)

If you created your part inside the Fritzing app, you will first need to export it and then extract it into the correct structure:

1. Export a `.fzpz` bundle of the part:

   Find the part in the parts library, right-click it and select _Export Part..._

2. Extract the `.fzpz`:

   First, make sure the filename is a good and concise description of your part. If not, rename it.

   Use the [fzpzclean.py python script](https://github.com/fritzing/fritzing-parts/blob/master/scripts/fzpzclean.py) to extract the bundle into the proper structure
   
       python fzpzclean.py -f <folder-with-fzpzs> -d <fritzing-parts-folder> -o core -r

3. Give it a unique **moduleId**

   Since you now have the same part twice, they will have conflicting IDs. In the first line of the `.fzp` file, find the property `moduleId` and change it to something unique. Usually, the full part name will do (without spaces).
   

## How to make your part visible in the part library window

This is optional, because even if your part is not directly visible in one of the bins, it is still accessible via the search and as alternative to similar parts (via a property change).

Open the corresponding "bin" file, for example `bins/core.fzb` for the Core library bin. Then simply add an entry at the position where you want your part to be shown, for example:

    <instance moduleIdRef="ResistorModuleID" modelIndex="3" path=":/resources/parts/core/resistor.fzp">
        <views>
          <iconView layer="icon">
            <geometry z="-1" x="-1" y="-1"></geometry>
          </iconView>
        </views>
    </instance>
    
Note that the `modelIndex` property has no meaning. All that matters is the `moduleIdRef` and `path`.

## How to contribute a fix

fritzing has an obsoletion mechanism. 
*to do*

## Advanced part makers: Manual part creation

See the [part file format reference](https://github.com/fritzing/fritzing-app/wiki/2.1-Part-file-format) for a detailed description.


>>>>>>> master

