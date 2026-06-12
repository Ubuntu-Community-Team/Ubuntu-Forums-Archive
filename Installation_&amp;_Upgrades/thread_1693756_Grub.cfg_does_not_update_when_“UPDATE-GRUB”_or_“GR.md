---
title: "Grub.cfg does not update when “UPDATE-GRUB” or “GRUB-MKCONFIG –O /BOOT/GRUB/GRUB.CFG”"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2011-02-23
[FONT=Times New Roman][SIZE=3]I have Update grub 1.99~rc1, I have also followed the instruction to purge all data found here. [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3][COLOR=#800080]http://ubuntuforums.org/showthread.php?t=1448978[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1448978")
[COLOR=black][FONT=Verdana]sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]and I am still unable to update  grub.cfg and have it reconge the new wallpaper ling in 05_debian_them.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR]**[SIZE=3][FONT=Times New Roman]/ect/grub.d/05_debian_theme[/FONT][/SIZE]**
[SIZE=3][FONT=Times New Roman]!/bin/sh -e[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]. /usr/lib/grub/grub-mkconfig_lib[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]# this allows desktop-base to override our settings[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]f=/usr/share/desktop-base/grub_background.sh[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]if test -e ${f} ; then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  . ${f}[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]else[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  #WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  **[COLOR=red]WALLPAPER="/usr/share/images/Eclipse.png"[/COLOR]**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  COLOR_NORMAL="black/black"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  COLOR_HIGHLIGHT="magenta/black"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Would appreciate any insight, thank you![/SIZE][/FONT]

---

### Post by enebre on 2011-02-23
Hey, purge  need remove --purge ??

---

### Post by ylafont on 2011-02-23
unclear, not sure what you mean. can you clarify?

---

### Post by Quackers on 2011-02-23
Have a look at section 8 in this guide by drs305. The inclusion of splashimages varies with the version of grub in use.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ylafont on 2011-02-23
Still nothing.
 
I don't get why this entry needs to be place manually, as it is removed whenever update-grub  or grub-mkconfig are excuted. 
 
I tried to see the splash image on the local pc and a usb drive with the following
 

set pager=1
insmod font
loadfont /boot/grub/LiberationMono-Regular.pf2
insmod video
insmod vbe
insmod gfxterm
gfxmode=1024x768x32
terminal_output gfxterm
color_normal=yellow/black
GRUB_BACKGROUND="/boot/grub/Eclipse.png"
 
on both accounts, grub did not dipslay the image.

---

### Post by Quackers on 2011-02-23
It isn't removed when grub is updated if it's in the right place. Is your chosen 
splashimage in /boot/grub????
Read the guide again, would be my suggestion.

---

### Post by ylafont on 2011-02-23
[FONT=Times New Roman][SIZE=3]I know I am  supposed to RTMF initially,  but I can’t  really be this  much of an idiot (have to laugh at myself).  OK, re-read the guide again. Followed the instruction son Section 2. specifically[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[LIST]
[*][COLOR=black][FONT=Verdana]A pre-made custom file, ''/etc/grub.d/40_custom'', is available in which users can place their own entries. This file will *not* be overwritten by Grub updates. [/FONT][/COLOR]
[/LIST][COLOR=black][FONT=Verdana]Also, Section 8 says.  “the user can now include the background image designation directly into */etc/default/grub**.  Which I did, the entry was*[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**[/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]* GRUB_BACKGROUND="usr/share/images/Eclipse.png"  and was placed along with the other grub commands.*[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**[/FONT][/COLOR] 
[SIZE=3][FONT=Times New Roman] I also  placed the entry  [/FONT][/SIZE]*[COLOR=purple][FONT=Verdana]echo "Adding 40_custom menu entries." >&2 [/FONT][/COLOR]*[FONT=Verdana]*as described in section 6 to see if grub-update was  processing the file 40_custom.. it did not**. My result were:***[/FONT]
[FONT=Verdana]**[/FONT] 
[SIZE=3][FONT=Times New Roman]ylafont@ubuntu:/etc/grub.d$ sudo update-grub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Generating grub.cfg ...[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found linux image: /boot/vmlinuz-2.6.35-25-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found initrd image: /boot/initrd.img-2.6.35-25-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found linux image: /boot/vmlinuz-2.6.35-22-generic[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Found initrd image: /boot/initrd.img-2.6.35-22-generic[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I inspected grub.cfg, my entries were not there.  And when i place the entries manually, the image still does not appear.  This was new installation of ubuntu 10.10  and upgrade to grub 1.99 that I did just for this purpose. Did I miss something?[/SIZE][/FONT]

---

### Post by Quackers on 2011-02-23
I would also suggest that you try to do only one thing at a time.
Where is the image that you want to become a splashimage? It appears that you were telling grub to look in /boot/grub earlier on. Now you're telling grub to look in usr/share/images. (which should have a / before usr, to signify root file system).

---

### Post by ylafont on 2011-02-23
I do, for ever change I make I run update-grub to see if it works and reboot.  The frustrating part, is that i do not receive error messages to at lest see where the problem is. 

The splash images on the local pc are stored in /usr/share/images and the grub configuration files point there. I have also made a usb  boot drive to see if i get different results. on the usb drive the images are stored in /boot/grub.

i get the same result on both setup.

---

### Post by Quackers on 2011-02-23
If the image is in that file then you may just need the missing / before usr in the command. (I edited my last post to include that)

---

### Post by ylafont on 2011-02-23
Had already tried that without success. 

That also does not explain why update-grub does not inform you that it is processing[I][COLOR=purple][FONT=Verdana] [COLOR=Black]40_custom menu entries. 

I am rebuilding a new box to see if i get different results.  is it recommended to stay with grub 1.98 or to upgrade to 1.99?  


[/COLOR][/FONT][/COLOR][/I]

---

### Post by ylafont on 2011-02-24
Sometimes you have to start from the beginning.   After a new instllation of Ubuntu 10.10, everthing (at least grub2) is working the way it is supposed to. I can't belive i wasted three days ont his for no reason.

---

### Post by nerd-guy on 2011-05-20
> **ylafont said:**
> Sometimes you have to start from the beginning.   After a new instllation of Ubuntu 10.10, everthing (at least grub2) is working the way it is supposed to. I can't belive i wasted three days ont his for no reason.

I am not a GRUB expert, but you could try:

sudo grub-mkconfig -o  /boot/grub/grub.cfg

The man page says that it needs to go to a file.

Good luck,  Howard

---

