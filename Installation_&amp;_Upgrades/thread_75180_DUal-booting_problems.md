---
title: "DUal-booting problems"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by saadghauri on 2005-10-13
I messed up and now i dont know what to do . I Installed lilo om mbr and now win2000 is gone ... what do i do ? i m thinking on installing winxp over ubuntu to recover win2000 somehow , but i really want to keep using ubuntu.Please help me

---

### Post by Lord Illidan on 2005-10-13
You already opened a thread about this problem. Don't clutter the forum.

---

### Post by az on 2005-10-13
[QUOTE=saadghauri]I messed up and now i dont know what to do . I Installed lilo om mbr and now win2000 is gone ... what do i do ? i m thinking on installing winxp over ubuntu to recover win2000 somehow , but i really want to keep using ubuntu.Please help me[/QUOTE]

Why did you install lilo?  What was the problem with grub?
.

Can you install grub and add an entry for windows and try to boot it that way?

---

### Post by saadghauri on 2005-10-13
no-one helped me in that forum :( sorry , i didnt meant to clutter its just that i am really panicked right now coz my brother has to use win2000 for work and if i mess it up its bad :(

---

### Post by saadghauri on 2005-10-13
grub wouldnt install it kept giving me an error. And whatever tutorial i check its either about grub or tells me not to install lilo on mbr :( what do i do now?

---

### Post by skirkpatrick on 2005-10-13
Go to [http://www.freedos.org/](http://www.freedos.org/) and download the bootdisk image and follow the directions to make a bootable floppy.  Then boot your system with it and at the command prompt, type "fdisk /mbr".  That will restore your MBR so that W2k will run.  That will blow away your LILO and you'll need to reinstall GRUB using the Ubuntu install disc to get your Ubuntu back.

---

### Post by saadghauri on 2005-10-14
skirkpatrick , you are awesome man , i got windows 2000 back .. Now , to get ubuntu back , how do i skip other installing steps to skip directly to install grub ??

---

### Post by skirkpatrick on 2005-10-14
Here's the topic that tells you how to reinstall GRUB: [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by al7kz on 2005-10-14
IMHO all linux users should make a grub boot floppy and keep it at their elbow for such an emergency situation. With it you can boot any OS on any PC. And you can also use it to re-install grub on the mbr. To make it follow the instructions in the Grub Manual. Cheers

---

### Post by saadghauri on 2005-10-14
Good link **skirkpatrick** and thanks again. **al7kz** How do i make a boot floppy (or cd preferably) of grub ?? thanks

---

### Post by al7kz on 2005-10-15
From Grub Manual:

To create a GRUB boot floppy, you need to take the files stage1 and stage2 from the image directory, and write them to the first and the second block of the floppy disk, respectively.

Caution: This procedure will destroy any data currently stored on the floppy.

On a UNIX-like operating system, that is done with the following commands:

     # cd /usr/lib/grub/i386-pc
     # dd if=stage1 of=/dev/fd0 bs=512 count=1
     1+0 records in
     1+0 records out
     # dd if=stage2 of=/dev/fd0 bs=512 seek=1
     153+1 records in
     153+1 records out
     #

The device file name may be different. Consult the manual for your OS. 

ie do a sudo updatedb, then locate i386-pc to get the correct path for it. 
Google grub manual for more info - cheers

---

### Post by saadghauri on 2005-10-15
[QUOTE=al7kz]From Grub Manual:

To create a GRUB boot floppy, you need to take the files stage1 and stage2 from the image directory, and write them to the first and the second block of the floppy disk, respectively.

Caution: This procedure will destroy any data currently stored on the floppy.

On a UNIX-like operating system, that is done with the following commands:

     # cd /usr/lib/grub/i386-pc
     # dd if=stage1 of=/dev/fd0 bs=512 count=1
     1+0 records in
     1+0 records out
     # dd if=stage2 of=/dev/fd0 bs=512 seek=1
     153+1 records in
     153+1 records out
     #

The device file name may be different. Consult the manual for your OS. 

ie do a sudo updatedb, then locate i386-pc to get the correct path for it. 
Google grub manual for more info - cheers[/QUOTE]

Well .. but currently i don't have grub installed and i can only boot win2000 :( 
so is there anyway i can download these images from the internet and use them ?

---

### Post by al7kz on 2005-10-15
Not that I know of - you need a working linux system with grub installed (ubuntu). Reinstall grub as suggested above to get ubuntu running, then make the grub boot floppy as a backup booter.

---

### Post by skirkpatrick on 2005-10-15
Yep, you'll need Ubuntu working again.  Also, here's a little tutorial on the subject: [http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html)

---

