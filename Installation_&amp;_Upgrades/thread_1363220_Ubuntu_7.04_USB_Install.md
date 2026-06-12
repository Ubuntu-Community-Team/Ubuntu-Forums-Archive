---
title: "Ubuntu 7.04 USB Install"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by bert682 on 2009-12-24
Hey guys,

Im trying to salvage some files from a disk that belongs to my sister.  I am just home from university and all I have is an old 7.04 install disc here.  I only have one hard disk and the installer for 7.04 only allows me to wipe everything, I guess the partitions are locked?

I have an 8Gb USB stick that I have used to install 9.10 to (there was an option from its menu) but it has long been cleared.  Because im running 7.04 the software isnt supported anymore and I cant install anything thats half in a way new from apt-get.

I cant download the full 9.10 iso either, im writing this from a Live running of 7.04 and have no space to download the file.

Any ideas?  Thanks in advance.

Regards, Robert

---

### Post by sanderj on 2009-12-24
> **bert682 said:**
> Hey guys,

Im trying to salvage some files from a disk that belongs to my sister.  I am just home from university and all I have is an old 7.04 install disc here.  I only have one hard disk and the installer for 7.04 only allows me to wipe everything, I guess the partitions are locked?

I have an 8Gb USB stick that I have used to install 9.10 to (there was an option from its menu) but it has long been cleared.  Because im running 7.04 the software isnt supported anymore and I cant install anything thats half in a way new from apt-get.

I cant download the full 9.10 iso either, im writing this from a Live running of 7.04 and have no space to download the file.

Any ideas?  Thanks in advance.

Regards, Robert

Download the 9.10 ISO to the empty 8GB USB stuck, burn a CD from the ISO, and boot the CD (or first create a live Ubuntu on the 8GB USB stick) in a PC with your sister's harddisk.

---

### Post by lisati on 2009-12-24
Use the "Start or install" option to start a "Live" session. Don't install Ubuntu at this stage - not only is 7,04 no longer supported, it will risk wiping the data you want to recover.

edit: it might be more useful to get hold of a newer version as has been already suggested, and use the "Try Ubuntu without installing" option. I just fired up a stray 7.04 CD I happened to have lying around - accessing the hard disk might be a bit difficult.

---

### Post by bert682 on 2009-12-24
I now have access to a laptop running Ubuntu Netbook Remix.  I downloaded the 9.10 iso and tried to run the USB creator tool (from UNR)  It loads up and I select the ISO and the application tells me I need to format my USB.

I click format and nothing happens?  Any ideas?

Regards, Robert

---

### Post by bert682 on 2009-12-24
UPDATE

Got it solved.  Used unetbootin and booted into 9.10 from the USB.  Resized with GParted and copied all the files I needed.

Thanks for the responses

---

