---
title: "Grub 'Error 25' after first stage install"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by jgb2185 on 2005-08-02
I have partitioned the Maxtor 120 GB slave drive in my Dell Optiplex GX100 as follows:

[FONT=Courier New][INDENT]/dev/hdb1      swap   512 MB    (no mount point)
/dev/hdb2      ext3   512 mb    /boot
/dev/hdb3      extended
[INDENT]/dev/hdb5      ext3     1 GB   /       (root)
/dev/hdb6      ext3    10 GB   /usr
/dev/hdb7      ext3     1 GB   /tmp
/dev/hdb8      ext3     1 GB   /var
/dev/hdb9      ext3    30 GB   /home[/INDENT][/INDENT][/FONT]
The 10 GB primary drive contains a pre-existing install of Windows XP, which I would like to retain.

During the first stage of the install, I okayed the installation of GRUB, and restarted the PC. The result is:

[FONT=Courier New][INDENT]GRUB loading stage1.5
   
GRUB loading, please wait...
Error 25
[/INDENT][/FONT]
Googling indicates that this may be an error in the generated menu.lst file, which I have attached to this post as menu.lst.txt.

Can someone point me to the error in the file? I have sufficient skills to modify it using a live CD and a text editor, but my knowledge of GRUB is less than zero.

Links to good GRUB resources will be welcome as well.

Thanks...

JGB

---

### Post by amohanty on 2005-08-02
/boot & GRUB which resides in /boot/grub need to be on the primary master drive.

AM

Edit: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Edit 2:
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

It is trying to look for it in the Primary HDD and faile sto find it.

---

### Post by jgb2185 on 2005-08-03
Thanks for the response. I'm studying the GRUB manual, I really am... but the solution is still a little bit out of my grasp.

What's the best way to proceed? Do I make my slave disk my master, and vice versa?  Do I put a /boot parition on the master disk?

Sorry to be so thick. Any additional clues gratefully accepted.

JGB

---

### Post by amohanty on 2005-08-03
IF (its in caps for a reason) you are going to reinstall I would suggest putting /boot in /dev/hda and swap anywhere else you can find the space.

To get around having to use grub you might have to do some vmlinuz voodoo. The simples way:
1. Put in the Ubuntu install CD. 
2. When it prompts you for entering the install command, you can make it boot off a kernel image on the HDD or use one of the images and instructions here:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RECOVERY](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RECOVERY)

3. There you might have to parted magic to move your partitions around. Since I have not done much of that, I cannot tell you how to do it but if you search the forums for parted you will find lots of stuff.

HTH
AM

---

### Post by jgb2185 on 2005-08-03
I'm sorry, I am clearly too stupid to handle this. I still do not understand how to fix the 'error 25' and allow the Ubuntu install to complete. I'm working my way through the GRUB manual, but it's heavy going.

I suspect it may be better to remove the Windows hard drive entirely and make the new drive I bought for Linux the primary and only HD for the moment. I can wipe and re-partition the drive and re-install Ubuntu from scratch, and hope that GRUB will be happier in that environment.

Later I can reinstall the Windows HD, and perhaps I'll be able to figure out how to boot Windows from a secondary drive.

JGB

---

### Post by amohanty on 2005-08-04
Before you do that you can try to switch the msater and slave as you suggested a few posts back and see if it works. If it does you can then change the menu.lst for grub to point the WinXP to the right place.

AM

---

