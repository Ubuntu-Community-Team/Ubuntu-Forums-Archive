---
title: "how to execute script"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by mthalis on 2008-03-25
#!/bin/bash
# Send-To
##########################################################################
#                        Nautilus "Send to" Script                       #
##########################################################################
#                                                                        #
# Created by Mattia Galati (Adaron)                                      #
# first improvement and translation by Christopher Bratusek (Chrispy)    #
#                                                                        #
##########################################################################
# Language Settings ---------------------------------------------------- #
destination='Choose Destination'
title_destination='Send files to:'

copy='Copying'
title_copy='Please wait...'

success='Files successfully copied'
title_success='Success'

errors='Something went wrong'
title_errors='Error'

no_writable='Destination is either not existant or writable'
title_no_writable='Error'
# End of language settings ----------------------------------------------#
##########################################################################

devices=`ls -m /media/`
vv=${devices//cdrom?, /}
vd=${vv//cdrom, /}
options=${vd//, / FALSE /media/}
destinazione=`zenity --list --title "$title_destination" --text "$destination" --radiolist --column " " --column "Device" FALSE /media/$options`
 
if [[ -w $destinazione ]]; then
	cp $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS $destinazione | zenity --progress --pulsate --auto-close --title="$title_copy" --text="$copy"
	if (( $? == 0 )); then
		zenity --info --text="$success" --title "$title_success";
	else	zenity --info --text="$errors" --title "$title_errors";
	fi
else	zenity --info --text="$no_writable" --title "$title_no_writable";
fi


I downloaded this script but i don't know how to install or use it.i don't have good knowledge about script.If some one can help me it is great help for me.I want to download more script for Ubuntu 
where i find script.I use Ubuntu 7.10.

---

### Post by aysiu on 2008-03-25
A script is basically a text file that contains code and is executable.

That looks like a Nautilus script, so you probably have to paste it into an empty text file and then save that text file in /home/mthalis/nautilus/scripts and right-click it and make it executable.

---

### Post by mthalis on 2008-03-25
/home/mthalis/nautilus/scripts and right-click it and make it executable.

In here /nautilus/scripts are normal directory am i correct?
how can i make executable - right-click but there is no option like this please help i don't have good 
knowledge.give me step by step plz.

---

### Post by ad_267 on 2008-03-25
Right click on it, select properties, click on the permissions tab at the top and then tick the box that says "Execute: Allow executing the file as a program"

---

### Post by mthalis on 2008-03-25
I did it.but after right click top option is open.i click it then it ask open in run in terminal or display like wise
when click one button give this it show this image.what's  that mean.how can i create send item like in windows.

---

