---
title: "dual boot issue xp 10.04"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by kulus1969 on 2010-08-29
I installed XP and 10.04 on seperate hdd's on a friends computer.

Windows XP Professional won't boot from Grub Menu of the 10.04 installation.

Ubuntu was installed on one 80GB hdd.

I switched to another empty 80gb hdd which I switched to Master and installed Windows XP Professional on it with all the upgrades including Service Pack 3 etc...

As long as the Windows drive is set as Master it boots fine with no problems.  When I set the Ubuntu as Master it will display:

Microsoft Windows XP Professional (on/dev/sdb1)

as an option but when selected it gives the following errors:

error: no such device: e2ecbb5aecbb2825.
error: hd1,1 cannot set C/H/S value
Press any key to continue...

When in Grub I pressed a key to show script and it showed the following:

insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e2ecbb5aecbb2825
drivemap -s (hd0) ${root}
chainloader + 1

I would like to help my friend next time I go over but I find the new Grub very complicated and wondered if someone can give me advice as to what to do next.

Thanks in advance,
Kev

---

### Post by jimbop99 on 2010-08-29
This is what I would do. Set up the XP drive as master, the Ubuntu drive as slave. Then reinstall Ubuntu onto the the second drive. Grub wiil be installed replacing windows MBR and all should work well.

---

### Post by Mark Phelps on 2010-08-31
Don't change the master/slave settings.

Instead, change the drive you boot from to be the Ubuntu drive.

If Ubuntu then boots OK, open a terminal and run "sudo update-grub".  That will regenerate the GRUB2 menu and you should be able to select either OS after that.

---

### Post by kulus1969 on 2010-08-31
I will try this and report back...
thx Kev

---

### Post by kulus1969 on 2010-09-13
I did "sudo update-grub" from a Terminal window with no success.  I then set XP drive to boot as Master and then installed wubi on XP from the 10.04 CD.  (I was hoping it wouldn't need to download the .iso of 10.04 if I did it that way but it downloaded it anyways.)

I left the CD in the drive (by accident) when I rebooted and had to select the option of boot from first HDD.  I then selected Ubuntu from the "windows/ubuntu Wubi bootloader" (not sure what to call it).  It then went to a screen with a cursor in the top left corner without mouse or keyboard control and didn't boot.

I am beginning to wonder if there is a setting in the CMOS that doesn't allow dual booting on his computer.  I am not sure what else to try.  I am planning to do a full install on a 10GB Partition on his XP drive and using the other drive as a data drive for both XP and 10.04.  I am afraid of losing the XP bootup ability after installing 10.04 due to the previous two attempts at setting up a dual boot system didn't work.

Has anybody had a similar problem, and if so, did you find a fix for it?

Kev

---

