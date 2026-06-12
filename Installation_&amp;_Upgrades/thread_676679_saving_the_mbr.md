---
title: "saving the mbr"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by agim on 2008-01-24
Okay, I understand that I can save an mbr by using this command

dd if=/dev/sda of=/boot/mbr_backup bs=512 count=1. 

I also understand the significance of using bs=446 instead.

My question is, to save it on something external, can I just use a CD? Or, as one person told me, do I have to use a floppy? And if either would work, is either choice better?

While I'm asking, can I save multiple mbr's to a single CD rw or a floppy or even a USB.

I am interested because I know several people who are interested in using Linux after I have told them about how well it is working for me, but I do not feel comfortable installing it on another's machine until I am reasonably sure I can reset everything to its original state.

Thanks for the help.

---

### Post by yabbadabbadont on 2008-01-24
Yes, you can save multiple mbrs.  Your dd command is dumping the mbr to a file.  Just copy the file to whatever external media you desire.  (Just like any other files)  :)

---

### Post by agim on 2008-01-24
Great to hear. Thanks for the help.

---

### Post by logos34 on 2008-01-24
A grub boot floppy is easier to make:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Just like yabbadabb said, you can save the mbr(s)--however many you like--to any storage media you like. (it's only 512 bytes including partition table, so you could fit many even on a floppy).    

> **agim said:**
> I am interested because I know several people who are interested in using Linux after I have told them about how well it is working for me, but I do not feel comfortable installing it on another's machine until I am reasonably sure I can reset everything to its original state.

You know, if it's the MBR you're worried about disturbing, you don't have to touch it at all during install---just tell the ubuntu installer to write it directly to a floppy instead.  Using the live cd, when you come to 'Ready to install' screen, click 'Advanced' button lower right and change default (hd0) to **(fd0).**

Or specify the ubuntu root partition, say (hd0**,1**) or whatever--this will write it to the bootsector or first part of root.  Then use [Super Grub Disc CD]("http://supergrub.forjamari.linex.org/") to boot ubuntu.

---

### Post by agim on 2008-01-25
Those are interesting ideas, and I will look into them. Thanks for the info. I have read a little about the Super Grub Disk, maybe its finally time to dive in.

---

