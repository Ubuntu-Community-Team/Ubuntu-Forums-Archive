---
title: "Using live cd"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2015-03-06
Just want to be sure... trying ubuntu from the live cd will not affect the current system on the computer. What are the limitations when using live cd? I assume it creates swap or temp on unused part of hard drive. Please explain how this works.

---

### Post by sotiris2 on 2015-03-06
The live cd will use any existing swap partition but won't create any or use unallocated space. The major limitation with using a live CD is that you can't install new applications (permanently) or save stuff to it (but you can save stuff on a disk partition if you manually mount it).  Thats for an actual CD/DVD though.

 You can have persistence in a live usb if you so desire (ubuntu's default startup disk creator has the ability to do it), or even make a full install on a usb stick (from another media) if you have a big one.

---

### Post by acefromspace on 2015-03-07
I'm using live cd of ubuntu 12.04 and the browser (firefox) is outdated... can't watch videos. Can I do an update? Also, what about using live cd AND a usb drive (make the usb drive swap drive)? Any others suggestions?

---

### Post by C.S.Cameron on 2015-03-08
You can make a new partition on your hard drive or USB drive, format it ext4 and name it casper-rw.
If, when booting, you hit F6 and type <space>persistent that is:
```
 persistent
```
after --
You will get a persistent session of Ubuntu, program installs and other changes will be saved to the casper-rw partition and appear the next time you boot using F6 persistent.

You can use the Live CD to make changes to your internal drive, such as removing viruses or formatting it.

If you want a swap partition, make a new partition and format it as swap.

---

