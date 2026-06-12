---
title: "How to boot casper drive to RAM"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Je1lybean on 2011-02-21
Hi All,

I've made myself a multiboot usb drive and looking to add ubuntu to it.  I've created a live system and its respective casper drive, made the changes I want to it  and now looking to make the whole system boot to ram including the casper drive so I can use the same usb drive in multiple machines instead of having to have multiple usb pens.

I've added the toram option in the txt.cfg file but only the operating system (filesystem.squashfs) goes into ram so when I take the usb out, the files on the casper drive are lost.

Could you tell me either how to boot the casper drive to ram or how to combine or merge the filesystem.squash and the casper-rw drive.

Many thanks

Je1lybean

---

### Post by psusi on 2011-02-21
What do you mean "the casper drive"?  Everything the system needs to keep running is in the squashfs so once it is loaded to ram with the toram argument, you can remove the drive.

---

### Post by Je1lybean on 2011-02-21
Thanks for your reply.

I've used the live system with the persistence squashfile, this allows you to make changes to the live system and saves the changes to a seperate file (casper-rw) but works in conjunction with the filesystem.squashfs file, this allows you to do updates and download other applications not released on the live version.

The problem is that it will not load the casper-rw file to ram even if you add *toram=casper-rw* in addition to the *toram* option.

Many thanks

Je1lybean

---

### Post by psusi on 2011-02-21
Ohh, well yea, persistence and toram are not compatible.  The former means DO NOT keep changes in ram.

---

### Post by Je1lybean on 2011-02-21
Is there a way to combine/merge the two files? or make the persistent drive read only?

Thanks

---

### Post by psusi on 2011-02-21
I don't think so.

---

### Post by Je1lybean on 2011-02-22
Is there anyway to modify the filesystem.squashfs file to include the programs I need?

Many thanks

---

### Post by psusi on 2011-02-22
You might be able to do it by mounting the squashfs and the caspwer-rw images, then copy the files out to a temp directory to merge their contents, then build a new squashfs from that temp directory to replace the other one with.

---

### Post by Je1lybean on 2011-02-28
I've now amended my filesystem.squashfs file and transfered it to my multiboot pen.  the problem now seems to be that it is trying to load everything from my pen into ram (so around 5gb of data) and coming up with an error stating that there is not enough ram in the machine (4GB), tried changing the append to boot=casper toram=filesystem.squashfs but it doesn't work, it just loads the filesystem from the pen.  Do you have any idea how to change the options to just load the filesystem.squashfs into ram on its own?

Kind regards

---

### Post by Je1lybean on 2011-03-01
I've now amended my filesystem.squashfs file and transfered it to my  multiboot pen.  the problem now seems to be that it is trying to load  everything from my pen into ram (so around 5gb of data) and coming up  with an error stating that there is not enough ram in the machine (4GB),  tried changing the append to boot=casper toram=filesystem.squashfs but  it doesn't work, it just loads the filesystem from the pen.  Do you have  any idea how to change the options to just load the filesystem.squashfs  into ram on its own?

Kind regards

---

