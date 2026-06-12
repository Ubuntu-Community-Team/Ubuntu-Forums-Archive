---
title: "Very Serious Problem Please Help"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by bondboy8 on 2008-03-23
I tired to intall ubuntu.  I partitioned the drive in the installer and began to install the base system.  All of a sudden a bunch of messages about corrupt files came up.  I tired going back but another popped up.  I was worried so I shut down the comp.  No windows or ubuntu doesnt work my comp is  stuck at a black screen what went wrong and will installin ubuntu still allow me to dual boot or did i lose windows.  I am currently redownloading the Ubuntu Installer and I am going to rewrite the cd

---

### Post by LaRoza on 2008-03-23
That really doesn't give us enough information.

What were the errors for one? They are given for a reason.

Also, did you burn the ISO at a slow speed, and did you check it before installing?

---

### Post by teaker1s on 2008-03-23
sounds like bad image on cd md5 check will verify this

---

### Post by bondboy8 on 2008-03-23
boxes get popping up during the install saying such and such is corrupt i would continue then there was another then i tried pushing go back and there was another i just need to know can a save my windows its just a black screen with a blinking white line

---

### Post by LaRoza on 2008-03-23
> **bondboy8 said:**
> boxes get popping up during the install saying such and such is corrupt i would continue then there was another then i tried pushing go back and there was another i just need to know can a save my windows its just a black screen with a blinking white line

Sounds like a back image or burn. You should have checked it first.

How were you installing? Were you trying ot dual boot? Did you format the entire disk? Where does the install fail?

You can use the Super Grub Disk to restore the Windows MBR, this will work if the Windows partition is still there (use a live disk to see if the Windows partitions and its files are there).

If not, you can use testdisk to try to recover the partitions. See the link in my sig.

You didn't give the errors, or much useful information. If the Windows partition is damaged, testdisk can probably recover the data, but it will be unlikely to be bootable.

I suggest getting your backups ready.

---

### Post by bondboy8 on 2008-03-23
I was trying to setup a dual boot and i resized it 50 gigs and left 30 gigs for ubuntu.  It failed about 6% in.  I was using the alternate CD

---

### Post by LaRoza on 2008-03-23
> **bondboy8 said:**
> I was trying to setup a dual boot and i resized it 50 gigs and left 30 gigs for ubuntu.  It failed about 6% in.  I was using the alternate CD

Try using testdisk or a Windows disk to repair it. It may be fixable.

But as I said, get your backups ready.

---

### Post by bondboy8 on 2008-03-23
ok what is test disk

---

### Post by bondboy8 on 2008-03-23
will instaliing a fresh version of ubuntu help

---

### Post by LaRoza on 2008-03-23
> **bondboy8 said:**
> ok what is test disk

I said see the link in my sig.

---

### Post by LaRoza on 2008-03-23
> **bondboy8 said:**
> will instaliing a fresh version of ubuntu help

Help you get Windows? No. Help you get Ubuntu? Yes.

---

### Post by teaker1s on 2008-03-23
if ubuntu installs correctly then unless you have overwritten windows partition, then if it's xp it will show up in grub boot options.
Hit esc at boot to get grub

---

### Post by bondboy8 on 2008-03-23
ok what do i do with testdisk sorry im still a bit shaken it just happened

do u think installing a fresh version of ubuntu wi help

---

### Post by bondboy8 on 2008-03-23
im just assumed that if i reinstall ubunu i would be able to dual boot with xp

---

### Post by bondboy8 on 2008-03-23
is there even a way to install ubuntu into the empty (I think) partition i already created for the first install

---

### Post by teaker1s on 2008-03-23
simple way of seeing it is you have made the computer think you have two area's on the hard drive. The problem is your computer doesn't know where to look as master boot record is missing.

if you can get ubuntu to install from a different disk that the md5 sum matches, it will install grub onto the master boot record and allow you to boot linux or windows.

Or you "fixmbr" and reinstall the microsoft master boot record-which will automatically boot windows

---

### Post by bondboy8 on 2008-03-23
do i have to delete the partition i already setup cuz i dont remember seeing an option to choose a partition in the install.  Also will deleting the linux partion with junk and resizing my indows partiition to full help

---

### Post by bondboy8 on 2008-03-23
how do i use fixmbr

---

### Post by teaker1s on 2008-03-24
delete the contents of the ubuntu partition with live boot iso of gparted (burnt as image) then reinstall ubuntu with a verified copy (md5)

or to fix xp

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

hope this helps

---

### Post by bondboy8 on 2008-03-24
I ran the install with a clean cd this morning i used the built in partitioner to destroy the old one.  Then used the guided- use largest free space.  Grub loads and will my xp boot fine, but when i boot ubuntu it seems to stall after the loading screen.  I have only given it like five minutes top but my comp isn't doing anything so i always restart any idea why this is happening or is it normal.

---

### Post by Coruba67 on 2008-06-27
hey guys.. am having the same problems.. corrupt files during install, yet checking the cd yields no errors... any way to run the installer without it checking for errors or to download them from repos as needed??

---

### Post by Canis familiaris on 2008-06-27
I think you should look at the Minimal CD 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Coruba67 on 2008-06-27
never even knew aboot that! thanks mate!

---

