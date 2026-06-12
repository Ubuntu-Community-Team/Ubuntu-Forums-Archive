---
title: "GRUB no kernel exists"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by stefslon on 2009-12-05
Basically, in the boot menu I have the choice between Ubuntu Netbook Remix and Windows XP Professional, but when I click Ubuntu Netbook remix, the Grub bash menu comes up. I type in "boot" but it responds with "no kernel exists". I'm kind of new to Linux and I don't know what to do. Any help would be nice, thanks.

{EDIT} It also just happened after I ran the Update Manager and restarted.

---

### Post by jarrarist on 2010-01-28
same thing happened to me :( dunno what to do. ubuntu is dead now.

---

### Post by Leppie on 2010-01-28
hi and welcome to the community,

please type the output of the command "ls" (with lower case L)

---

### Post by presence1960 on 2010-01-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. See below (thanks to meierfra) for more info on boot info script:

boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system or Live CD with an Internet connection.
    * Download the Boot Info Script
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

