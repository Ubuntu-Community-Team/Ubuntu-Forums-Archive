---
title: "Shutdown Problem - Ubuntu 9.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by FaLL3N_G0D on 2010-10-25
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Arial Black][SIZE=2]Ok I just installed Ubuntu 9.10 this morning, so bare with me and my lack of knowledge. I have one problem that I cannot seem to fix. Every time I try to shut down my computer, it properly shuts down EXCEPT for the fact that the power button is still lit and the screen is black (still on, but black).[/SIZE][/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Arial Black][SIZE=2]I am currently running Vista on my Toshiba Laptop. Vista is on my internal hard drive and I installed Ubuntu 9.10 on my 250gb external hard drive. The installation works and is successful. However, I cannot seem to fix the shutdown. I have tried the following:[/SIZE][/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]1. (In the terminal) sudo shutdown -h now -> did not work, same result as the GUI[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]2. Terminal sudo gedit /etc/init.d/halt and add rmmod snd-hda-intel -> didn’t work[/SIZE][/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black][SIZE=2]3. Terminal sudo gedit /etc/default/grub in this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" I added acpi=force[/SIZE][/COLOR][/FONT]
[SIZE=2][FONT=Verdana][COLOR=black]so the line should look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" then save then do in terminal update-grub -> didn’t work[/COLOR][/FONT][/SIZE]
 
[FONT=Verdana][COLOR=black][SIZE=2]4. Terminal sudo gedit /etc/rc6.d/S40umountfs Moved the cursor to the line fstab-decode umount -f -r -d $WEAK_MTPTS and remove the -f form this line Now move the cursor to the second line and remove the -f from this line as well then SAVE the file and reboot. One last thing I left all these changes in affect -> didn’t work[/SIZE][/COLOR][/FONT]
 
[SIZE=2][FONT=Verdana][COLOR=black]5. Terminal sudo gedit /etc/default/grub I changed the line from GRUB_CMDLINE_LINUX="" to this GRUB_CMDLINE_LINUX="reboot=b" save it and reboot -> didn’t work[/COLOR][/FONT][/SIZE]
 
[COLOR=black][FONT=Verdana][SIZE=2]I have NO idea what to do. . .[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=5][FONT=Arial Black][COLOR=red]IF ANYONE HAS ANY SUGGESTIONS PLEASE LET ME KNOW!!![/COLOR][/FONT][/SIZE][/FONT][/COLOR]

---

