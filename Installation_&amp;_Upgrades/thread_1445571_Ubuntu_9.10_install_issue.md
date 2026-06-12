---
title: "Ubuntu 9.10 install issue"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by nishi40uk on 2010-04-02
Hi,
I'm a newbie to Linux, and am trying to install Ubuntu 9.10 on an old IBM T21 laptop.
It starts very happily, and I am able to partition the disk & copy the files to the HDD.
 
However, when it loads the desktop there is an icon for the CD drive ( and install disk).  Everything appears to be fine, but I don't see any confirmation of the installation being completed.
 
The CD drive does not open when the button is pressed.
When I restart the laptop, I get the message 'operating system not found'.
 
Starting the machine using the CD works fine.  The disk shows that the partitions have been created, and I am told that Ubuntu  9.10 is installed.
 
Any help in resolving this issue would be greatly appreciated.
 
Many thanks.

---

### Post by sxmaxchine on 2010-04-02
have you tried installing it throught the install instead of running the desktop and clicking install.

---

### Post by nishi40uk on 2010-04-02
Many thanks for your swift response.
 
Yes, I've tried to install from the initial option screen with the same result.

---

### Post by sxmaxchine on 2010-04-02
it sounds like it installed try installing the grub bootloader [check here]("http://ubuntuforums.org/showthread.php?t=224351")

to open the drive try right clicking the drive and clicking eject.

other then this i dont know what your problem is, hope this helps.

---

### Post by nishi40uk on 2010-04-02
many thanks - I'll give that a try and update this thread with my results.

---

### Post by presence1960 on 2010-04-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

