---
title: "installation error"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by vert11 on 2010-09-28
Hi all 
One of my friends has installed ubuntu a day ago,when he installed it his portable hard-drive was attached to the PC .He is not sure whether he has installed ubuntu on portable drive or not,but now he not able to login into any of the OS on his machine until and unless he insert his portable drive,what  could be the reason and what is the solution(his regular harddrive contains XP)

---

### Post by P4man on 2010-09-29
Can your friend run this little "bootinfo" script:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and post the result? That should make it clear what's going on.

---

### Post by vert11 on 2010-10-01
hi here is th log attached with the post.do let me know what is the issue.?
PS when he boots his comp without attaching his portable drive some grub rescue> console come up 
which accepts no commands accept ls,and the output of ls is somthing like (hd0) (hd1) and like that.

---

### Post by Goolie on 2010-10-02
Okay, so I'm not 100% sure, because my familiarity on the subject is pretty low, but Windows and Ubuntu are *not* on the same hard drive.  Looks like Windows is on the smaller 40GB harddrive while Ubuntu is on the bigger 320Gb HDD.  

I'm going to go on a limb and guesstimate that the Master Boot Record ended up on the 2nd external drive.  I'm saying this because 

A.) Linux is on the bigger 320GB, 
B.) It was the 2nd installed OS on the PC 
C.) It would make the GRUB loader for you.

Essentially, the computer is looking for the little data table that says where the operating systems are, but that little data table (MBR) is actually on the portable hard drive, which is why you're not able to boot into either OS unless it's attached.  

You could fixmbr within Windows, and remove the Ubuntu OS from the external.  Unless you wanted Ubuntu on the external, on which case you're project involves moving the MBR from the external to the internal HDD, which would allow you to boot.  

But you have to take everything I say with a grain of salt.  I'm no expert, but no one else replied, so I tried for ya!

---

### Post by P4man on 2010-10-02
Indeed, the MBR is on sda (the internal, windows drive). It points to grub on sdb, the external drive. Thats why it wont boot without the external drive.

There are two ways to solve it; 

Scenario 1

if the machine has a bios option to select the boot drive or a boot menu, then the easiest solution is reinstalling windows MBR on sda, and grub MBR on sdb. That will make the machine bootable with or without external drive. Then set the bios to boot from the external drive by default, so if that is present, you will get grub and be able to chose windows or ubuntu. 

TO reinstall MBR on windows, using a windows XP CD, follow this:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

If you dont have a windows CD, you can do it from ubuntu as well, see here:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

After doing that, windows will be okay, but ubuntu will not as there is no grub MBR anywhere anymore. You will have to install grub on sdb. Boot an ubuntu live cd, and run these commands:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

**edit**: The first command may need to be 

```
sudo mount /dev/sdb**5** /mnt
```

Looks like everything is in extended partitions. Im not 100% sure here, but I think it should be sdb5

then ubuntu will be bootable from the USB drive on any machine.
Configure the bios too boot form USB first. So if there is an USB drive, grub menu will show. If the bios isnt retarted, it will boot windows from internal drive if no USB drive is present.

Scenario 2

If the bios of the laptop doesnt have a disk boot priority menu, then you will need to install all of grub (not just the MBR) on the internal drive. It will need its own /boot partition, so you must shrink the existing windows drive, free up a few 100 megs, create a /boot partition and install grub there. Ill post that if needed.

BTW, to avoid all this, next time you install ubuntu, in the last phase of the installation procedure, make sure you install the bootloader not on sda (default, and the first drive), but on the drive you actually install ubuntu on, being sdb. You will need to change the bios to boot from that drive first, but all the rest will be done automagically. Nice side effect is that the USB drive becomes bootable by itself, so you can actually boot your Ubuntu install on any machine (if you dont require restricted drivers).

---

### Post by vert11 on 2010-10-02
Thanks for the help ,i'll be going to my friend's place this weekend and after that i'll post back whether or not the problem was solved.
 
one off topic question,What happen to the packages that are downloaded from the USB booted linux version??Do they stay on harddrive or is there any way to make them stay permanently??

---

### Post by P4man on 2010-10-03
I dont understand the question. by "USB Booted" do you mean a "live image" (the iso image) or the ubuntu your friend installed on the external USB drive? If its the first one, then no, not really. YOu can make a custom livecd easily though, if you want to include a few specific packages, look at remastersys or ubuntu customization kit.

---

### Post by vert11 on 2010-10-03
nah i meant usb booted as live mode...

---

