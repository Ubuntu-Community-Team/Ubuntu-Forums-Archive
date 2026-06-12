---
title: "Ubuntu on a 16GB pendrive problems (persistent install) NTFS"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by Davste on 2011-04-20
I want to install Ubuntu on my 16GB pendrive, with only 4GB allocated to Ubuntu. I also want to leave the other 12GB as an NTFS partition, so I will be able to copy films and files larger than 4GB to it, from windows.

I managed to do this with gparted. The 12GB partition was instantly recognized by windows, and linux booted up from the USB.

However after a while I quickly ran out of space. Is there any simple way to install all linux software to an NTFS partiton by default? For example install open office, firefox etc to the NTFS partition, while leaving all system files on the ext4 one. Or install linux on NTFS altogether?

What I would really like is having a folder named "Linux Software" on my 12GB partition, and having ubuntu automatically installing all applications there.

Like I said, I hate FAT. I want to be able to copy files larger than 4GB on my pendrive. Any ideas?

---

### Post by Dutch70 on 2011-04-20
Ubuntu will not run on ntfs.

One option to consider is to install Ubuntu to the entire usb stick, format it to ext2 or ext3. Windows can read these file systems if you install fs-driver into windows.

I've never tried that, but I do have an ext2 file system and windows reads it quite well with fs-driver installed. 
[[COLOR="RoyalBlue"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

There are probably many other ways to accomplish this. A couple more would be to install a much smaller distro, or make Ubuntu's partition around 6-8GB or create a live usb with persistence and don't update it, that shouldn't take more than 1 GB.

---

### Post by bob-linux-user on 2011-04-20
Have a look at 
"Memory Issues on USB Install" 
Which was one of my questions and was solved for me.

---

### Post by oracle2b on 2011-04-20
You can remove .deb files in your cache located at 
> /var/cache/apt/archives

you can run this command in the terminal to remove those files which should free up some space

> sudo rm /var/cache/apt/archives/*.deb

P.S Use the > sudo rm command with care if you are not copying & pasting.

---

### Post by MBybee on 2011-04-20
I do something similar to this - I run my daily work image on a 16GB SD card. My Ubuntu 11.04 is installed in 10GB, the remaining 5 and change is formatted as FAT32 (not really worth NTFS for 5GB).

As long as you remove swap and use tmpfs, 10GB is perfectly sufficient for Ubuntu. 4GB might be pushing it.

---

