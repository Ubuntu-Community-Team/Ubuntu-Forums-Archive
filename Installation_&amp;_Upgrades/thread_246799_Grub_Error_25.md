---
title: "Grub Error 25"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by caiman64 on 2006-08-29
](*,) 

I am getting Grub Error 25 on boot... I cannot enter to Windows XP nor Ubuntu... 

I am posting this using the live cd... How can I fix this grub error??

How can I access the files on the disk?? Live cd does not let me into the disks!!!

Help!!

Regards,
Carlos

---

### Post by caiman64 on 2006-08-29
](*,) 

I used to have WinXP on my first disk, and Ubunto on my second disk. Then I got the Grub error 25....

Now I switched the disks... and again instales Ubunto (on top of the older instasll)... now I can only use Ubuntu when ever I try to select Windows XP to run I ger error reading disk...

How can I configure Grub to load the darn windows XP??!!!....

Please help me...

Regards, 
Carlos

---

### Post by confused57 on 2006-08-29
Can you boot the Windows drive, if it is the only drive connected to the primary controller?  If you can't, you can try booting up with the Windows install cd(not the recovery cd), press "r" to enter recovery mode, then enter **fixmbr**...hopefully, this will repair the Windows mbr and enable you to boot Windows. 
  Here's a website explaining how to do this:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you're able to boot into Windows, you might want to connect your Ubuntu drive to controller#1(SATA) or master(IDE) and your Windows drive on the secondary or slave position and try to set up a dualboot using this guide:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I don't have any experience with SATA drives, but the above method works great on 2 of my systems with 2 IDE drives.

---

### Post by caiman64 on 2006-08-30
Hi, Thank you for your help... I really appreciate it!! :-D 

No my windows disk will not boot if connected alone... even if I re-install windows it will not boot... (I tried with both disks)!!

Right now I have Ubuntu running and booting normally on the first disk... however, after downloading and installing the upgrades to Ubuntu I get GRUB 0.9x intead of GRUB 1.5... I guess they are trying to fix the issues with the newer GRUB version

Works for me... BUT I am not being able to boot or install Windows on either disk.  :confused: 

Bye,
Carlos

---

### Post by confused57 on 2006-08-30
I don't know if this has anything to do with it, but Windows doesn't recognize ext3 format...you might be able to format the other drive as fat32 from Ubuntu and then the Windows install cd may be able to recognize it and install.
You could download gparted live cd(30 Mb) and format the hd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by caiman64 on 2006-09-08
nothing worked...  decided to dump Windows for good!!  :-k

---

### Post by NetworkGuy on 2006-09-08
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

You might have a bad block on your hard drive.

---

