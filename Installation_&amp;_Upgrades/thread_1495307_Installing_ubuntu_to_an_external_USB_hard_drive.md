---
title: "Installing ubuntu to an external USB hard drive"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by pedrovay2003 on 2010-05-27
Hey, I'm sorry if this has already been posted -- I'm EXTREMELY new to ubuntu and this website.

I just bought a 500gb internal laptop hard drive and put it in an external casing.  I'd like to install ubuntu to it and create 2 partitions -- One very small one, only what the OS needs, and then another huge one for all my files.

I'd like to keep the huge partition in FAT32 format so I can connect it to my PS3, which I use as a media center.  I hear that ubuntu doesn't play nicely with FAT32, but as long as I can keep the big partition FAT32, I don't mind what the smaller one is.

Is it possible to do this?  Can I have ubuntu on my now-external drive and have the larger partition FAT32?  Also, will the OS run at a decent speed, and will my settings be saved when I exit (like the wallpaper and saved wireless networks, stuff like that)?  Again, thanks for bearing with me -- I really don't have much of a clue as to what I'm doing.  :P

---

### Post by lmarmisa on 2010-05-28
No problem. You can define a great FAT32 partition (I do not know the size limitations of the FAT32 system) and two partitions for Ubuntu: one for the root directory (file system: ext4 or ext3; 15 Gbytes will be a good size) and a second partition for swap (my recommendation is to define the same size for swap than your RAM memory).

You have to select the manual partition option during the installation if you wish to define the sizes for the different partitions.

An important installation detail: install the grub loader in the MBR of the extermal drive, not in /dev/sda!!!!. I believe that this is selected in the last menu of the Ubuntu installation (7/7), in Advanced Options. This is very important!!!!.

---

### Post by pedrovay2003 on 2010-05-28
Excellent -- This is EXTREMELY helpful.  I was confused as to which option to choose when it came to that ext4 and 3 stuff, too, so that answered yet another question.

Thanks a ton for the response -- I'm going to give this a whirl later.  I really appreciate it.

---

### Post by pedrovay2003 on 2010-05-28
Also, one more thing:  Grub is the thing that tells ubuntu to boot automatically from the external, correct?  Is it possible to just F12 to boot from the external when the computer's starting up, or is Grub actually REQUIRED?

Just curious.

---

### Post by dino99 on 2010-05-28
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by lmarmisa on 2010-05-28
> **pedrovay2003 said:**
> Also, one more thing:  Grub is the thing that tells ubuntu to boot automatically from the external, correct?  Is it possible to just F12 to boot from the external when the computer's starting up, or is Grub actually REQUIRED?

Just curious.

I forgot to explain this: you have to change the BIOS configuration in order to boot from your external hard drive. 

Grub is the loader program and its loader code is stored in the code area (446 bytes) of the Master Boot Record of the hard drive:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Grub (or LILO) is required for starting up your Ubuntu system.

Win XP has its own loader, but it is not able to boot Ubuntu.

Grub is able to boot not only Linux systems, but also other OSs like XP, Vista or W7.

---

### Post by pedrovay2003 on 2010-05-29
I just got ubuntu installed to my external, and everything is working absolutely flawlessly.  Thank you for your help, I couldn't have done this on my own.  :D

---

