---
title: "Can't uninstall grub"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by techless42 on 2006-11-13
Help please,
I have winxp on a hd, and Dapper on another.  I want to uninstall Dapper.  From the forums, I understand that I need to boot the winxp install disc, and go to the Repair Console to fix the mbr, to remove the grub loader.

However, when I boot the xp disk, it does not give the option of going into the Repair Console, but goes straight to loading windows.

I also tried to install the Repair Console as a boot option, but got a popup that i386 could not be found.

If anyone can help, I'll appreciate it.

---

### Post by Irony on 2006-11-13
Should go like this;

*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

---

### Post by bulldog on 2006-11-13
Yes,well boot the WINXP disk and enter through it **till you come to the part with three options**
1:Install Windows
2:Repair Windows
3:Exit
Choose the repair windows option.
You go to a console where you have to enter your admin password.
Then type  fixmbr   and/or   fixboot   and you should be fine again.

---

### Post by techless42 on 2006-11-13
Thanks Irony & Bulldog for the replies.  Here is the problem: when I boot the xp disc, press any key to boot, I first get a black screen "setup is examining your hardware configuration".  This goes to a blue screen headed "windows setup", at the bottom of which it states "setup is loading files".  It start loading a bunch of files, at which point I eject the disc to prevent windows reloading.  I do not get the screen where I get to select the recovery console.  

If I allow it to go on loading files, will it eventually get to the  recovery option, or will it just reload windows?

---

### Post by bulldog on 2006-11-13
Just let it load,it installs nothing,till you get to the discribed options.
Choose R to repair a windows and than you will be taken to recovery console.

It's a nice black screen with the option to choose which windows you want to repair.
I presume you have just one windows so choose the number in front of it and enter your admin password if needed.

Than fixmbr  and fixboot

That should do it.
Just reboot and GRUB should be gone.

---

### Post by techless42 on 2006-11-13
Thanks, Bulldog, that info was what I needed to know.  It worked.:p

---

### Post by BlueEraser on 2007-10-18
I also used the fixmbr in windows repair, and was scared to death of the warning message, but really had no other choice.  fixmbr repaired the boot record, and grub no longer gives the the error 15 message.  ok, on to a fresh install of Gibbon!!

---

