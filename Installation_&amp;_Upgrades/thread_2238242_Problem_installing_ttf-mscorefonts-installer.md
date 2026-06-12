---
title: "Problem installing ttf-mscorefonts-installer"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by william44 on 2014-08-06
Im trying to install this program but when I do i get this message

[COLOR=#000000][FONT=Cantarell][SIZE=2]Failure to download extra data files
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.[/SIZE]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]ttf-mscorefonts-installer[/SIZE]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.[/SIZE]
[SIZE=2]Then when i run the action I get this message
[/SIZE][COLOR=#000000][FONT=Cantarell][SIZE=2]Data files for some packages could not be downloaded
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]ttf-mscorefonts-installer
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Cantarell][SIZE=2]This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem[/SIZE]
[/FONT][/COLOR]


[/FONT][/COLOR]

---

### Post by oldos2er on 2014-08-06
Try ```
sudo dpkg --configure -a
``` If/when the EULA comes up, use the Tab and Enter keys to agree to it and continue the installation.

---

### Post by yancek on 2014-08-06
I' m quite sure the EULA will come up and the default is NOT to accept so you do need to use tab to highlight to select Yes or OK.

---

### Post by william44 on 2014-08-06
I tried it and the prompt for the EULA didn't show up, it just starts another command line

---

### Post by yancek on 2014-08-07
Which version of Ubuntu are you using?
What software are you trying to install that requires mscorefonts?
What is the 'it' you are referring to that you tried?
Do you have a working internet connection?

---

### Post by oldos2er on 2014-08-07
> **william44 said:**
> I tried it and the prompt for the EULA didn't show up, it just starts another command line

That would indicate APT thinks there are no packages to configure. After you've provided the info yancek asked for, try ```
sudo apt-get install --reinstall ttf-mscorefonts-installer
``` If there are any errors please copy and paste all the terminal output here.

---

