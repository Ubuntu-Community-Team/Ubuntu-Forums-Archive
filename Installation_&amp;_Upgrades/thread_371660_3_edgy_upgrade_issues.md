---
title: "3 edgy upgrade issues"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by mykalreborn on 2007-02-27
hi there
i've recently updated to edgy, and it's al good. except for 3 things...
1. it has this annoying thing with the download manager. sometimes - [this]("http://gnome-look.org/content/show.php?content=53567") is a good example - i get the download manager window, but when i choose save to disc the window disappears and i don't get any download. now sometimes the download manager downloads the file, but when it does it "doubles" the extension - foo.exe is saved like foo.exe.exe. this is very annoying as you can imagine. i have swiftfox 2.02 installed for sempron which is the processor i have. help would be greately appreciated
2. gaim has an issue. the avatar on the yahoo protocol - that's the only one i have set up - doesn't show. all my windows friends told me all they see is a black picture. i have no linux buddies in my list, so i don't know if that happeness in linux too. i have gaim 2.03 defaultly installed when i upgraded to edgy
3. when i boot, it takes some time to load of course, and then at half way through i get the terminal saying something about checking the windows partitions (hda2, but i'm not sure because it's too fast). from what i could understand it's something to do with a file system being corrupted or something. i'm sorry i can't give you more details about this, but i don't have the time to read those things. is there a log or something i can show you? also here is my /etc/fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=b8c76144-54ac-432f-9c98-3f626c1a02e1 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=986053dd-0a8f-476e-82fb-206ff25aee06 /home ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=459A-5F50 /mnt/share vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=54BC-F63A /mnt/win vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda4 -- converted during upgrade to edgy
/dev/hda4    none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

i know it's such a long thread. sorry aobut that. thanks again!

---

### Post by mykalreborn on 2007-03-01
well... i did a few tweaks there and there... i messed up the whole system and had to start over again with a fresh copy of edgy eft alternate cd. ;))
so issue number three is gone. i'm curious about the other two . anyone? :D

---

