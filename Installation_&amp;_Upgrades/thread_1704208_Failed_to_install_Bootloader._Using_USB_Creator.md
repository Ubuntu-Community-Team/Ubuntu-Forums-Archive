---
title: "Failed to install Bootloader. Using USB Creator"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by Aaron2 on 2011-03-10
Does anyone have any suggestions on why when using usb creator I may be getting a Failed to install Bootloader error??

I have the .ISO selected in the top pane, 8GB usb drive path in the lower pane.

I'm going this route because my mb isn't recognizing the CD's autorun.inf.

Any suggestions appreciated.

---

### Post by Aaron2 on 2011-03-10
Created a working bootable CD using infrrecorder, so all is solved.

---

### Post by thinman1189 on 2011-03-11
I am also having this problem. See this old thread [http://ubuntuforums.org/showthread.php?t=1422992](http://ubuntuforums.org/showthread.php?t=1422992)

Ideas?

---

### Post by Quackers on 2011-03-11
Try unetbootin?

---

### Post by grizzancs on 2011-03-24
I've just ran into the same problem, the solution was to reformat the flash drive as fat32 (it was ntfs, didn't even notice it)

---

### Post by Auslegung on 2011-09-07
I know this thread is old but I was having similar problems, couldn't find a solution online, and made it work for myself nonetheless.  I was trying to use a 4GB ext4 partition of my 500GB external hdd to make a LiveCD.  I got the Failed to Install Bootloader issue.  I reformatted the 4GB partition to NTFS, still failed.  Finally I reformatted the 4GB partition to FAT32 and it worked.

I'm not very savvy about the different file system types, in general I know ext4 is the fastest and "best," (which is why I tried to use it for my 4GB partition) while NTFS works well with Windoze and Linux, and FAT32 is a Windoze fiile system type that Linux can read and use anyway.  Maybe this will help others, hopefully.

---

### Post by ranskalex on 2011-11-08
Formating to FAT32 worked for me too. Thanks for the tip!

---

