---
title: "Install Ubuntu on a CD-RW"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Blackcamaro8 on 2009-12-22
Okay. I'm pretty proficient in all things I've learned about Ubuntu so far. I've gotten past installing Ubuntu, I know a lot of basic commands, I can install things on it using the command line, etc. 

But I have a wierd question.

Most modern computers come with at least ONE CD-RW/DVD-RW drive... So I was wondering if there was a way to take an entire installation of Ubuntu and put it on a CD-RW or a DVD-RW that would use the disc as the root directory, reading from it, and being able to WRITE to it. 

I know the CD-RW method would take some sort of live-CD sort of application, and possibly a disk compression method, that would allow a large allotment of information to reside in a small one. I'm thinking something SORT of like Slitaz OS, the one that ophcrack relies on to boot, and then runs from. 

Something... Customizable.

---

### Post by carl99fan on 2009-12-22
You can do this using a usb flash drive I think. Leaving room to make all the changes you need.

---

### Post by Blackcamaro8 on 2009-12-22
Well, honestly, i knew this.
I just think it would be cooler to blow my friends' minds using a CD-RW. XD

---

### Post by Mark Phelps on 2009-12-24
> **Blackcamaro8 said:**
> Most modern computers come with at least ONE CD-RW/DVD-RW drive... So I was wondering if there was a way to take an entire installation of Ubuntu and put it on a CD-RW or a DVD-RW that would use the disc as the root directory, reading from it, and being able to WRITE to it. 

Basically -- NO.  Why? Because, unlike a hard drive or USB drive, optical media is not really a read/writable filesystem.  Data must be formatted in some fashion and then BURNED to the media.

All that RW means for optical media is that the data can be erased and the media rewritten --  it does not mean that the media can operate like a read/filesystem.

A while back, in MS Windows world, CD/DVD burning app vendors offered special drivers that would allow you to (1) mount your optical drive simulating a filesystem, and (2) format your optical media to create a filesystem.  This tended to work poorly or not at all.

---

### Post by oldfred on 2009-12-24
Take a look at this, its both backup & creating a cd without your personal data:

[http://geekconnection.org/remastersys/remastersystool.html](http://geekconnection.org/remastersys/remastersystool.html)

---

### Post by lukeiamyourfather on 2009-12-24
Even if it was possible it'd be incredibly slow which would make Ubuntu look bad anyway. Use a USB flash drive and make sure to enable the extra space to save file in the USB creation utility (so you can save changes). Cheers!

---

