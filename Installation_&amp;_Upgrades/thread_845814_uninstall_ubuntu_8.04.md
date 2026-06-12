---
title: "uninstall ubuntu 8.04"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by glennnf on 2008-07-01
Hi all, ive installed ubuntu 8.04 on my slave & ive got vista on my master,can somone tell me how to uninstall ubuntu without effecting vista (as it seems grub has some effect on vista?).Thanks for the help.

---

### Post by Partyboi2 on 2008-07-01
If you have a vista disk you can use it to restore the mbr.
Boot the  Vista installation disc. Press a key when you are prompted. Select the language etc and then click Next. Then click repair your computer. Click the operating system that you want to repair, and then click next.
In the System Recovery Options  box, click Command Prompt.
Type ```
Bootrec.exe /FixMbr
``` and then press enter.
Then reboot using the ubuntu live cd and use gparted (System>Admin>Partition Editor) to delete the ubuntu partitions.

Edit: If you don't have a vista disk use [[COLOR=Blue]supergrub[/COLOR]]("http://www.supergrubdisk.org/")

---

### Post by ericalejandrocasas on 2008-07-24
how can i uninstall ubuntu 8.04?
the problem is that i cant run the installation disk because the window wont open, in fact i cant open any folder window or use the right button mouse on the desktop, i really dont know what to do, i was hoping that i could find a way by doing it via terminal or something like that

---

### Post by Partyboi2 on 2008-07-24
> the problem is that i cant run the installation disk because the window wont open,I am not sure what you mean by this.

---

### Post by ericalejandrocasas on 2008-07-24
let me tell you the whole story, i wanted to make my ubuntu look like a mac by doing this [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/) but something went wrong i think during the dock section because the dock would not appear, so i decided to abandon the project, but now the problem is that when i restart my computer my home folder will just randomly open and close about 7 times, the icons on my desktop wont appear, well they'll appear but only when my home folder is flashing, and they'll to disappear, i cant use the right button mouse button on my mouse on the the desktop, so by this point i really got frustrated and decided to just reinstall ubuntu so i inserted the boot cd the one i used to install it in the first place (i had win xp) and hopefully just reinstall like windows, but the problem again is that all of my file browser (or the window) will automatically close, and i mean everything, so then i thought well just make another account and maybe start fresh from there, but no, when i try to open users and groups it says that ''the configuration could not be loaded - you are not allowed to access the system configuration'' funny thing is im supposed to be the only user allowed, because im the only user in the computer. Well i hope you can really help me out with this one man! hope its not too much info 

thanks again!!

---

### Post by Partyboi2 on 2008-07-24
Did you install ubuntu to its own partition or did you install it inside windows using wubi?
If you installed ubuntu to its own partition are you able to boot the ubuntu live cd? If so, make sure in your bios you have boot from cd selected first. Then boot to the ubuntu desktop, which is the first option at the ubuntu live cd main menu.
Then recover any data you don't want to lose to another medium. Then open a terminal (Applications>accessories>terminal) and type or paste
```
sudo fdisk -l 
``` (small L)
and let us know what the output to that command is.

---

### Post by ericalejandrocasas on 2008-07-25
i did use the live cd to install ubuntu i didnt use wubi, but i cant boot the cd, i dont know why! nothing happens

---

### Post by pmlxuser on 2008-07-25
if you know how to go into bios mode in your machine 
change the boot order to CDROM, FDD, HDD then you will be able to boot from CD

then follow instruction by Partyboi2 in post #2

(if you don't know how to get into your bios please specify what machine you use)

---

### Post by ericalejandrocasas on 2008-07-27
hey, hows it going guys? sorry i couldn't respond earlier i had a family emergency and had to leave town for a few days :( but oh well. i typed the comand and this is what came out:

  To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00550055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19127   153637596   83  Linux
/dev/sda2           19128       19457     2650725    5  Extended
/dev/sda5           19128       19457     2650693+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ce8ec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   b  W95 FAT32
ubuntu@ubuntu:~$ 

oh and thanks for the help so far man i know its kinda been a pain! and sorry for the wait as well! cheers!

---

### Post by Partyboi2 on 2008-07-28
I am assuming that since you were able to post the output to that command that you have been able to boot the live cd. To reinstall you can start the installer and when you get to the partitioning part choose the manual way and edit sda1, tick the box to format and make sure the mount point is set to /

---

### Post by ericalejandrocasas on 2008-07-28
it worked! thanks alot man! i thought i was never going to be able to do this! thanks alot!!

---

### Post by tridianm on 2008-08-05
How would one completely delete Ubuntu from my Mac PowerBook G4?  I am going to sell it and the buyer wants the original OS X on it.  I am completely novice to this and didn't install Ubuntu Hardy Heron onto the Mac myself and the person who did is no longer around.

---

