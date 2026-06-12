---
title: "Ubuntu 10.0.4 Live cd doesn't start and installation does not start"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by bram100 on 2010-09-08
I installed Ubuntu beside a windows xp system. But now it won't reboot anymore and gets stuck in a command line.

Tried the live cd or usb again but it won't start either and it hangs in the splash screen with the dots.

After hitting esc (in splash) I get a command line with error message unable to open 'dev/sda'.

Xp still starts fortunately, so I am able to open the disks..

How do I fix this, please help ?

---

### Post by thegod_slayer on 2010-09-08
please post your rig configuration.

or try formating the pc full.
and then installing xp and ubuntu.

---

### Post by bram100 on 2010-09-08
I have Ubuntu installed on a Dell430. Not inside XP but on a separate partition. At first it booted fine. But after some updates and starting the XP partition Ubuntu won't start anymore. 

Any Ideas.

---

### Post by thegod_slayer on 2010-09-08
the update may have erased some config files from your ubuntu part.

it happened with me on my rig ( win 7 and ubuntu 10.04 ).

what i did was very simple.

deleted the ubuntu partition and reinstalled it.

works fine.

---

### Post by Lemuel111 on 2010-09-08
Yes I'm having the same problem. 10.04 worked fine then put on some updates and now it won't get past the 'Ubuntu ....' screen. Suggestions most welcome.

---

### Post by TwelveGauge on 2010-09-08
which updates?

---

### Post by bram100 on 2010-09-08
Just delete the partition ? Which tools can I use for that ?

Can I still boot XP, is the bootloader erased as well ?

---

### Post by MisterLambda on 2010-09-08
Get a GParted Live CD. Potentially dangerous, but should do the trick.

Also, the MBR containing the bootload is on a seperate partition. Note that the GRUB bootloader will still be there, unchanged. (hopefully)

---

### Post by bram100 on 2010-09-08
- I only see some unknown Logical drives.
- There is two: 
1. 633MB
2. 13GB

Which one should I delete and can I still boot then ?

---

### Post by MisterLambda on 2010-09-08
Do you remember what size Ubuntu's partition was? Also remember that Windows uses ntfs and fat, and Linux usually uses ext.

---

### Post by bram100 on 2010-09-08
Ok I found out that 
- 13 GB is the ext partition
- 633 MB is the swap partition

Now which one should I remove without removing the bootloader ?

---

### Post by bram100 on 2010-09-08
[SIZE=3]- I figured it out
1. First I removed GRUP bootloader, by using the installation disk for XP (recovery console)
here is how:
[/SIZE][SIZE=3][FONT=Calibri, Verdana, Helvetica, Arial][/FONT][/SIZE][SIZE=3][FONT=Calibri, Verdana, Helvetica, Arial][http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD](http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD)[/FONT]

2. Next I removed the partition
3. I reinstalled Ubuntu on the empty space. 

Back in business (typing this in Ubuntu)![/SIZE]

---

### Post by Lemuel111 on 2010-09-09
I've tried the Ubuntu Live CD but it just goes to the same screen (Ubuntu.....) and progresses no further. Any suggestions?

---

### Post by Lemuel111 on 2010-09-09
I've managed to get a a black screen saying:-
"BusyBox v1.13.3 (Ubunutu 1:1.13.3-1ubutu11) built-in shell (ash)
Enter 'help' for a list of built in commands. 

(initramfs) Can not mount  /dev/loop0 (/cdrom/casper/filesystem.squashfs) on / /filesystem.squashfs"

I then typed "help" and a list of built in commands are listed followed by

"(initramfs) _"

Can I do anything with this lot?

Cheers

---

### Post by Lemuel111 on 2010-09-10
I can't even get the above now. I can load the Ununtu 9.10 live cd with the options but when I try boot from hard disk I get the same screen that won't progress (Ubuntu .....).

---

