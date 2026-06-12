---
title: "Dapper Live CD Persistence: Not enough space after one use!"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by ulgor on 2006-05-31
Hi,
one thing I should mention first: sorry for my English...
 
Second: I am quite new to Linux/Ubuntu but I do have a little experience using it. Still, consider me a noob please...

**Story **
Last week my hard disk with Windows/Ubuntu dual boot broke, and I am happy to be able to access my external USB drive and still use my laptop using the LiveCD! Actually, everything works fine with the LiveCD, no hardware detection problems, good performance.

**Background**
Now, because I have to work completely without hard disk, I switched to the new Dapper Live CD, using the new persistence feature. Still, no problems, good performance!

I even managed to set up a 1GB USB stick with a 350MB ext2 partition called "casper-rw" and format the remaining 650MB to fat32, so that I can store and access data on any OS/system. 

The first thing I did was to install Thunderbird, Skype and Inkscape and Processing. I also made some changes to Theme/Background/Font-settings etc. I thought that 350MB should be enough for those applications, even if the GNOME settings alone take up 100MB. 

So this is my setup:
- Dapper Drake LiveCD, (Development Release downloaded 2 days ago)
- 1GB USB Stick with two partitions
      1.  "casper-rw" (primary): size: 350MB filesystem: EXT2
      2.  "usbdisk" (primary): size:650MB filesystem: FAT32  
- Installed: Thunderbird, Skype, Inkscape, additional required packages for Inkscape
-  Booting with "-persistent" works fine, my modified Desktop appears, all installed programs are still there!

**Problem:**
I cannot download anything, not even check for new emails, because there is no free disk space available! I tried emptying the trash and deleting downloaded files on the Desktop - still no space for ANYTHING but browsing the web.

Should I have a bigger partition for the persistent files? Is there anything I can do to see how much space I really need?

The file size info from the LiveCD does not help me much since a lot of stuff stays on the CD or exists just in the RAM, correct?

It seems that even deleting big files (installers for Thunderbird etc.) does not free any disk space, where does the free space go? :-k 

Thanks in advance for helping a newbie who is stupid enough to use development releases! ;)

---

### Post by pellgarlic on 2006-06-07
[QUOTE=ulgor]It seems that even deleting big files (installers for Thunderbird etc.) does not free any disk space, where does the free space go? :-k[/QUOTE]

maybe a stupid question, but - have you made sure to empty the trash?

---

### Post by ulgor on 2006-06-18
Hi, I thought of that too,  but emptying the trash did not work...

OK, I only checked the trash as default user! But apparently I deleted a lot of stuff as "root".
All I had to do is switch to root and empty the .Trash Root - voilá!

I just came back here to post the solution.
@Pellgarlic: Thanks for answering anyway!

---

