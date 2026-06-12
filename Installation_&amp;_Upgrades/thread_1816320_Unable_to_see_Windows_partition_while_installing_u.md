---
title: "Unable to see Windows partition while installing ubuntu 11.04"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by Vijay Dhama on 2011-08-01
[HTML]
I am installing Ubuntu 11.04 dual boot along with Windows 7.
But I am unable to see already installed windows partitions.
During installation it shows hard disk as a whole.
Does failure of CMOS battery has something to do with this??
please help..

[/HTML]

---

### Post by jasonrisenburg on 2011-08-01
Did you choose to install beside or entire disc?

---

### Post by Mark Phelps on 2011-08-02
CMOS battery failure will prevent you from saving changes to BIOS settings, but that is unlikely to have anything to do with not seeing the Windows install.

Plus, if you really do want to push forward with dual-boot install, BEFORE you do anything else, boot into Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will be useful later, should you need to repair the Win7 boot loader.

Second, boot into an Ubuntu Live CD (use the Try It option), when you get to a desktop, open a terminal and enter "sudo fdisk -lu (that's a lowercase L, not a one).  That will list off the partitions on your drive.  If you already have four, then you can NOT install Ubuntu to its own partition without doing a lot of work first -- because you can not have more than 4 primary partitions on a drive.

Third, if you have three or fewer partitions, then use the Win7 Disk Management utility to shrink the Win7 OS partition to create room.  Do NOT format the new unallocated space, and do NOT, repeat NOT, allow the Ubuntu installer to shrink Win7 to make room.

---

### Post by omelette on 2011-08-02
Having just installed 11.04 (and removed it again) beside an XP partition, I can say that the installer identified the Windows partition OK.  What bugged me about the installer and which seems really dumb, is that when I selected the option to upgrade my already existing Ubuntu 10.04 installation (which it also detected automatically) it also quietly added that it would be using the whole of available disk-space - meaning it would reformat the entire hard-disk, wiping Windows!  And there's no 'bells & whistles' warning about this, just the disk-size it will be using is printed.  If you didn't read what's on the screen carefully, your M$ installation would probably be history!!!  Thankfully the 'Advanced' option allows you to specify exactly what to format...

Reminds me of the way Gate's offerings used to wipe any other OS it found during installation without comment, though maybe not so cheeky...

---

### Post by Vijay Dhama on 2011-08-02
I had kept a 23 GB partition for Ubuntu while installing WINDOWS 7..
I selected "Something Else" ubuntu 11.04 during installation.
In which installer shud detect windows.
but it's not detecting windows partition.
Just shows
"/dev/sda"
Also I have 4 partitions.
3 - windows 
1- left for ubuntu

---

