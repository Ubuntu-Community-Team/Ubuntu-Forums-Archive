---
title: "Problem installing grub on a flash drive"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by goaliedude3919 on 2009-12-20
So I've been trying to install grub on my 4GB Sandisk flash drive, but to no avail. I've been using these websites for help:

[http://www.linuxquestions.org/questions/linux-general-1/installing-the-boatloader-on-a-flash-drive-instead-of-mbr-553498/](http://www.linuxquestions.org/questions/linux-general-1/installing-the-boatloader-on-a-flash-drive-instead-of-mbr-553498/)

[http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/337977-4gb-flash-drive-multiple-bootable-linux-oses-part-1-a.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/337977-4gb-flash-drive-multiple-bootable-linux-oses-part-1-a.html)

[http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/338171-how-make-bootable-flash-drive-part2.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/338171-how-make-bootable-flash-drive-part2.html)

[http://www.freesoftwaremagazine.com/articles/grub_intro/](http://www.freesoftwaremagazine.com/articles/grub_intro/)

They all follow a similar formula, but when I get to the part where I'm in grub, that's where I run into problems. Whenever I try this step:

     ```
grub
root (hd0,1)
setup (hd1)
quit
```it says "Error 22: Selected disk does not exist"

When I tried the code form one of the other websites using "find", it gives me: "Error 15: File not found". I'm fairly new to Linux and I'm not really sure what's going on with hd0, hd1, and all that. I would really appreciate any help you guys could give me. Thanks!

---

### Post by darkod on 2009-12-20
Can you give more information why you want grub on the stick? Did you install ubuntu on it? Is there ubuntu on it already? Do you want to install only grub on it?

---

### Post by goaliedude3919 on 2009-12-20
I want grub on the flash drive to eventually partition the flash drive and have a couple different live distros on there. I basically want to be able to choose between a couple different distros when I boot off the flash drive.

---

### Post by darkod on 2009-12-20
Use a working Ubuntu computer and Gparted to create as many partitions as you want. I recommend as first partition to create small partition to keep the grub files.
For your idea, I would use program called grub4dos and grubinst.
That can install grub legacy on any usb stick in windows. Much easier than in linux, at least I don't know how to do it in linux yet. The problem is most tutorials you'll find for linux will be to restore grub, not to install it from scratch. For the restore to work you need to have the config files on the destination device, which you don't have because you never had grub there.
I created a flash drive with 4 partitions (one was 100MB for grub) with 3 different "systems". The Ubuntu 32bit and 64bit desktop version and clonezilla. Worked fine, once I figured it out. :)

---

### Post by goaliedude3919 on 2009-12-21
Thanks! I'll give those a try and see what happens.

---

