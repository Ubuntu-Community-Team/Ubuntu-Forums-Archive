---
title: "Multiple Ubuntu installations"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2008-01-31
I want to have multiple installations of Ubuntu and I've searched the forums and not found anything addressing exactly what I want to do.

I have triple-boot Xp, Vista, Ubuntu 7.10 32-bit. (there are solid reasons for needing all three).

The windows partitions share one hard drive, ubuntu has its own.

The ubuntu drive is the boot and Grub uses its MBR, with the grub menu providing entries for Ubuntu and Windows.

What I want to do is install additional a second Ubuntu instance, this one 64-bit (have AMD 64-bit processor) on the ubuntu hard drive.

My guess is that all I have to do is the following:
1) save off a copy of Grub's menu.lst file
2) make some available space on the ubuntu drive
3) insert the 7.10 AMD live CD and install it to the ubuntu drive, overwriting Grub on that drive
4) reboot

Is this right?

Also, when I'm done, will I need to edit the new menu.lst to add the Windows info? Also, will it contain both Ubuntu's or only the new one.

Finally, is there any way that I can share the same /home volume? Should I even do this, or should I use separate /home volumes, one for each Ubuntu?

---

### Post by logos34 on 2008-01-31
yeah, either shrink your ubuntu root down beforehand using gparted on the live cd or resize it during installation.  And, yes, let it overwrite existing grub.  If all goes normally, it will detect all OSs and add them to menu.lst, so you won't have to edit anything.  If it doesn't get the windows entries correct, post back.

Don't try to share /home.

Make an **extended** partition out of the freed space and put all your x64 partitions inside.

---

### Post by Mark Phelps on 2008-02-01
logos34:  thanks for the feedback.

Turns out, I was able to locate a third hard drive, so I'm thinking of adding that to my machine and installing the 64-bit Ubuntu to that drive.  Since I'm not going to share /home, and that takes up the most space, this will prevent me from having to give up space on the existing Ubuntu drive.

However, since the Live CD installs GRUB to the MBR of the first hard drive, even though I will be installing Ubuntu to (what will then be) the second hard drive, it should still overwrite the existing GRUB install, right?

---

### Post by logos34 on 2008-02-01
> **Mark Phelps said:**
> Turns out, I was able to locate a third hard drive, so I'm thinking of adding that to my machine and installing the 64-bit Ubuntu to that drive...
However, since the Live CD installs GRUB to the MBR of the first hard drive, even though I will be installing Ubuntu to (what will then be) the second hard drive, it should still overwrite the existing GRUB install, right?

Usually, but not always.  Like, if you add an IDE drive to a sata system, even though the sata is the boot disk, grub almost always thinks the IDE is the first one and puts the bootloader there by default.
No big deal, you can always reinstall grub later to wherever you want.  **Or** on the Ready to Install screen>Advanced button replace the default '**hd0**' with **/dev/<drive>** format just to make sure it goes to the correct mbr.

---

### Post by Mark Phelps on 2008-02-02
logos34: Thanks again for replying ...

Yeah, I discovered the boots-first-from-the-IDE problem the hard way.  So, now, I have it booting from the IDE drive all the time, and the Windows partitions are on the SATA drive.  I just want to ensure that if I install a second Ubuntu on the second IDE drive, it won't overwrite the Ubuntu installation on the first drive.

---

### Post by logos34 on 2008-02-02
> **Mark Phelps said:**
> I just want to ensure that if I install a second Ubuntu on the second IDE drive, it won't overwrite the Ubuntu installation on the first drive.

it's usually the grub part that causes the confusion...you definitely want to use the /dev/<drive> format.  Just before you click the installation icon open a terminal and run

sudo fdisk -l

that will show how your drives are being designated.  They should be seen the same way by the ubiquity installer.  

good luck

---

### Post by ajeannotte on 2008-02-04
as for sharing your /home folder, what i do is have a separate drive for all my documents and edit /etc/fstab to mount that drive in my home folder as a folder (say 'stuff') for every installation. 

when i format it, i format it as fat32 so that i can use it as 'My Documents' for Windows too. 

just a thought.

---

