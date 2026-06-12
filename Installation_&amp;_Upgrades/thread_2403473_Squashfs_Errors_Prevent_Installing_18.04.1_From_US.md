---
title: "Squashfs Errors Prevent Installing 18.04.1 From USB"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by Nico_Janow on 2018-10-11
I'm trying to install 18.04.1 on my old desktop (Celeron g1610, 3.6 GB RAM, BIOS: American Megatrends P1.10 (2013)) and I get the squashfs errors.  I've tried it from two USB sticks, and got exactly the same errors. I've tried the solutions listed elsewhere, which didn't work.  I could figure out which line was the kernel line (starts with linux), but I wasn't able to find out which line is supposed to be the 'grub line' for adding '[COLOR=#333333][FONT=UbuntuMono]all_generic_ide pci=nommconf'.  I'm not familiar with grub, so maybe I'm just missing something.  My version only shows 4 lines:

setparams 'try ubuntu without installing'

set gfxpayload=keep
linux /casper/vmllinuz file=cdrom/preseed/ubuntu/seed boot=casper quiet splash ---
initrd /casper/intitrd/lz


I tried the all_generic code on all the lines, with none fixing the problem.  Am I supposed to start a new line with a specific word for the code?  Is there some other way to fix this inability to install?  Am I supposed to wait for the squashfs errors to finish being listed, which would take how long?

I'd like to tell people that Ubuntu is easy to install, but my experiences say that it's really frustrating.  I avoided upgrading from 14.04 until now because I expected this sort of frustration.[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-10-12
Did you check the md5sum of the ISO file you downloaded to create the USB?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Nico_Janow on 2018-10-12
The md5sum did indeed prove incorrect.  I'll have to redownload it, which is a pain because I'm on a slow connection with limited downloads/month.  I didn't realize that downloads were so easily defective.

---

### Post by ubfan1 on 2018-10-12
zsync might be a solution -- it can take a local iso file, hash many small sections separately, and just download the sections which differ from the master.  I didn't see a Windows version, so you would have to try downloading the  zsync package on the running Ubuntu install media (try...), then run it (with your own iso and choice of cdimage) like:
zsync -i ubuntu-16.04-beta2-desktop-amd64.iso     [http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)

The local bad iso is after the -i option
Pick out the zsync file on cdimage.ubuntu.com/daily-live/current of the equivalent iso.

---

### Post by Nico_Janow on 2018-10-17
I had downloaded via torrent, so a bit of checking turned up 'verify local files', which started redownloading the damaged bits.  Installation went fine after that.

Lesson learned: always verify local files after download is complete.  :)

I am a bit disappointed that 18.04 is noticeably slower to boot than 14.04, and that it doesn't properly recognize my old (pre 2000?) keyboard.  It doesn't recognize the caps lock or num lock keys.  I'll have to see if there's a way around that.

Installation problem solved though.  I can recommend Ubuntu as easy to install (but check the iso first).

---

