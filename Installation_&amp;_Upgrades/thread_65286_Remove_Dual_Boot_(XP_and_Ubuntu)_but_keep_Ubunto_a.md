---
title: "Remove Dual Boot (XP and Ubuntu) but keep Ubunto and start with floppy/cdrom"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by oti0 on 2005-09-13
I installed Ubuntu Hoary in addition to (after)  Windows XP on my office-notebook and it works quite well using dual boot.

But now I realised that I offenced against  the network/security policy of my company.

Therefor, I want to "hide" ubuntu by removing the dual boot option but keeping ubuntu on my notebook

Is there any possibility to

(1) remove the dual boot option AND
(2) keep ubuntu and all the software/data on the ubuntu-partition AND
(3) start ubuntu via ubuntu live-cd or ubuntu installation cd?

OR do I have to remove all  ubunto from my notebook?

thank you in advance

oti

---

### Post by djib on 2005-09-13
[QUOTE=oti0]I installed Ubuntu Hoary in addition to (after)  Windows XP on my office-notebook and it works quite well using dual boot.

But now I realised that I offenced against  the network/security policy of my company.

Therefor, I want to "hide" ubuntu by removing the dual boot option but keeping ubuntu on my notebook

Is there any possibility to

(1) remove the dual boot option AND
(2) keep ubuntu and all the software/data on the ubuntu-partition AND
(3) start ubuntu via ubuntu live-cd or ubuntu installation cd?

OR do I have to remove all  ubunto from my notebook?

thank you in advance

oti[/QUOTE]
 I know how to do (1) and (2).
I'm sure you can do (3) but I don't know how.

If you have a MS Win cd, you can boot with it. Then you can 'debug' an installation. When you are in the windows console, type fixmbr.

---

### Post by sir_mud on 2005-09-13
[Here]("http://os.inf.tu-dresden.de/%7Efm3/grub.html") is a bootdisk creator, just tell it where your menu.lst is, probaly hd0,1 if its on the second partition on the first disk.

---

### Post by oti0 on 2005-09-14
[QUOTE=djib]I know how to do (1) and (2).
I'm sure you can do (3) but I don't know how.

If you have a MS Win cd, you can boot with it. Then you can 'debug' an installation. When you are in the windows console, type fixmbr.[/QUOTE]


thanks a lot!

it worked fine, no problems, no more dual boot !

---

### Post by oti0 on 2005-09-14
[QUOTE=sir_mud][Here]("http://os.inf.tu-dresden.de/%7Efm3/grub.html") is a bootdisk creator, just tell it where your menu.lst is, probaly hd0,1 if its on the second partition on the first disk.[/QUOTE]

thanks a lot for your reply. unfortunately my office-notebook has no floppy-drive built in (i have to appologize for not mentioning this yesterday - but i was at home at my private computer and thought, that there is a floppy-drive on my notebook).

as i understand, the methodology you described does only work with floppies. is there an possibility to use a cd-rom instead?

oti

---

### Post by leezer3 on 2005-09-14
Hiya,
Use that to create a working boot floppy with your desktop PC, and then find the trial of WinIso. In the BootableCD menu, use the option to make boot file from floppy. Then create a new iso, and tell it to use the boot info that you just extracted from the floppy. Finally, copy all the files from the floppy into the iso, & burn to the CD- One boot CD. (Remember to burn to a CDRW as opposed to a CDR, as it may well take you several tries to get the menu.lst etc right.)

Cheers

-Leezer-

---

### Post by oti0 on 2005-09-17
[QUOTE=sir_mud][Here]("http://os.inf.tu-dresden.de/%7Efm3/grub.html") is a bootdisk creator, just tell it where your menu.lst is, probaly hd0,1 if its on the second partition on the first disk.[/QUOTE]

thanks for your answer. i followed your instructions (I used menu.lst - file to get information about the correct hd/partition-information) and created the image-file using your tool.

when trying to boot from floppy the boot-procedure stopped and a grub-prompt appeared on the screen.  it took me some time and tries but at the end I was successful by typing in the relevant commands (root, kernel, initrd, boot) using the parameters that were written in the menu.lst - file.  although this solution works fine for me (at least if I am workung with a pc  equipped with a floppy-drive): do you have any further suggestions?

kind regards, oti

---

### Post by oti0 on 2005-09-17
thanks for your answer.

unfortunately I was not successful following your hints.

**make boot file from floppy** worked fine. winiso produced a *.wbt - file

**create a new iso, and tell it to use the boot info that you just extracted from the floppy** this I have done by adding the previously generated *.wbt - file haveing a size of 1.474.560 bytes

**Finally, copy all the files from the floppy into the iso, & burn to the CD- One boot CD**: there are no more files on the floppy respectively winiso could not access the floppy for adding additional files 

as I could not find additional files I burnt the iso-image on cd

the funny thing is, that the boot-cd I created wants to install ubuntu on my computer instead of interpreting grub (commands) or starting grub

do you have an idea why the result is that odd?

kind regards,

oti



[QUOTE=leezer3]Hiya,
Use that to create a working boot floppy with your desktop PC, and then find the trial of WinIso. In the BootableCD menu, use the option to make boot file from floppy. Then create a new iso, and tell it to use the boot info that you just extracted from the floppy. Finally, copy all the files from the floppy into the iso, & burn to the CD- One boot CD. (Remember to burn to a CDRW as opposed to a CDR, as it may well take you several tries to get the menu.lst etc right.)

Cheers

-Leezer-[/QUOTE]

---

### Post by oti0 on 2005-09-18
on [http://ubuntuforums.org/archive/index.php/t-19428.html](http://ubuntuforums.org/archive/index.php/t-19428.html) I came across the  easiest solution for my problem. 

first step ist to remove the mbr as described in this thread

second step ist to use isolinux and follow the procedure described on the link above


oti



[QUOTE=oti0]I installed Ubuntu Hoary in addition to (after)  Windows XP on my office-notebook and it works quite well using dual boot.

But now I realised that I offenced against  the network/security policy of my company.

Therefor, I want to "hide" ubuntu by removing the dual boot option but keeping ubuntu on my notebook

Is there any possibility to

(1) remove the dual boot option AND
(2) keep ubuntu and all the software/data on the ubuntu-partition AND
(3) start ubuntu via ubuntu live-cd or ubuntu installation cd?

OR do I have to remove all  ubunto from my notebook?

thank you in advance

oti[/QUOTE]

---

