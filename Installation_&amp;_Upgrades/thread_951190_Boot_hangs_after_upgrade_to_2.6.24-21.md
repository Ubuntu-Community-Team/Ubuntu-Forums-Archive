---
title: "Boot hangs after upgrade to 2.6.24-21"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by lostinUHF on 2008-10-17
I upgraded to -21 and everything seemed ok.  I let the upgrade update my menu.lst. ( I will never do that again!)

I then went into menu.lst and removed the old versions and just left the current -21 including recovery mode.  (I will never do that again either).

Anyway the system starts to boot in a verbose mode and then stops after

**uniform CD-ROM driver Revision 3.20**

Nothing happens after that! 

I have a dual boot system with windows on my first drive and Ubuntu 8.04 on my second hard drive.

The menu.lst is set to root(hd1,1) which I think is OK.

I tried editing the lines in grub to start -19 but the same hang occured at the same place.

I had to use windows to enter this question.  Yuk!

Please help!!!!:(

---

### Post by Neo_The_User on 2008-10-17
> **lostinUHF said:**
> I upgraded to -21 and everything seemed ok.  I let the upgrade update my menu.lst. ( I will never do that again!)

I then went into menu.lst and removed the old versions and just left the current -21 including recovery mode.  (I will never do that again either).

Anyway the system starts to boot in a verbose mode and then stops after

**uniform CD-ROM driver Revision 3.20**

Nothing happens after that! 

I have a dual boot system with windows on my first drive and Ubuntu 8.04 on my second hard drive.

The menu.lst is set to root(hd1,1) which I think is OK.

I tried editing the lines in grub to start -19 but the same hang occured at the same place.

I had to use windows to enter this question.  Yuk!

Please help!!!!:(

Open up a file browser and in the boot/grub folder, make it show hidden files. See if there is a back-up file of the menu.lst file. If so, replace the new menu.lst file with the previous version.

---

### Post by lostinUHF on 2008-10-17
> **Neo_The_User said:**
> Open up a file browser and in the boot/grub folder, make it show hidden files. See if there is a back-up file of the menu.lst file. If so, replace the new menu.lst file with the previous version.
I can't get the system to boot to edit anything so looking for an older copy of menu.lst will not help me

---

### Post by wacky_ninjas on 2008-10-17
> **lostinUHF said:**
> I can't get the system to boot to edit anything so looking for an older copy of menu.lst will not help me

If you still have your Ubuntu install CD (assuming you used the desktop CD), you can boot it as a live CD and get to all of your files that way. Just boot it as if you were going to install Ubuntu, but _do not_ select the "Install" icon on the desktop.

Instead of installing, you can mount the HD partition that contains /boot/grub - there should be an option for that in the "Places" menu, maybe under "Removable Media". Then look for the backup file that Neo suggested. It might be named "menu.lst~".

If you don't have your Ubuntu CD, then you can do the same thing with other live CDs, including small ones that you can download and burn (in Windows) more quickly than the Ubuntu CD. Some examples are SystemRescueCD (about 200Mb) and DamnSmallLinux (50Mb). Google will find these for you.

---

### Post by lswb on 2008-10-18
Do you have a ubuntu live CD? You can boot from it, mount the ubuntu partion on your hard drive, and edit your menu.config or run update-grub to create a new one. See the man pages for mount and update-grub or post again if you need help with those commands.

---

### Post by Niniel on 2008-10-18
Haha, that's funny, I have the exact same issue, except that for me it hangs after it tries to do something related to USB. What it should be doing is ask me for my system password, but no, it doesn't want to do that.
I was already *beep*ed off by all that Automagic junk that the upgrade put in menu.lst, and now this...
Fortunately, I didn't delete everything so the 19 kernel is my new default now. :)

---

### Post by Neo_The_User on 2008-10-18
> **lostinUHF said:**
> I can't get the system to boot to edit anything so looking for an older copy of menu.lst will not help me

Let me make that more clear. Use windows to look for the older version of menu.lst ok? Depending on how you partitioned your hard drive, windows might be able to find it.

---

### Post by lostinUHF on 2008-10-18
Thanks I will try that also.  

I tried editing the commands in grun before booting and changed the version numbers.  Same result as before the system dumps out into init??? and gives me the message ALERT /dev/disk/by-uuid/1a9fb419-b2a3-470b-886 does not exist

Very strange.  Now my system can not find the drive.  Could it be that the automatic update of my menu.lst has changed the uuid?

---

### Post by lostinUHF on 2008-10-18
Hi,

I tried that but windows does not see show me any folders at all although it does see the drive.

---

### Post by lostinUHF on 2008-10-18
Well I have finally solved it.

I did ls -l /dev/disk/by-uuid (within init????) and found that the uuid was truncated in grub.   I simply edited the kernel portion of grub and added on the 14 characters and I was back in action

---

