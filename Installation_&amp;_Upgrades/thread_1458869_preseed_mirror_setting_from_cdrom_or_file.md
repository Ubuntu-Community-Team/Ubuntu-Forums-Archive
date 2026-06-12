---
title: "preseed mirror setting from cdrom or file?"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by dalesyk on 2010-04-20
Hello,
  I'm trying to auto install Ubuntu9.10x64 desktop from an existing freedos harddrive partition and without using the network.  I have this working with the network as follows... The hd-media kernel/initrd files, the alternate iso, and a preseed file on the dos partition, launched via linld.com  The preseed has a mirror section that includes...

d-i     mirror/http/hostname    string archive.ubuntu.com
d-i     mirror/http/directory   string /ubuntu
d-i     mirror/suite            string 

I tried changing to this

d-i     mirror/file/directory    string /cdrom
d-i     mirror/suite            string 

Now the installer prompts for the mirror.

Does anyone have a suggestion?

Thanks,

Dale

---

### Post by dalesyk on 2010-04-21
replying to myself... 
It seems that the alternate cd (unlike the desktop cd) does not contain all the packages needed for a desktop install, and that is why I have the mirror problem.  I am going to try to add the needed packages and remaster the cd.  I found a guide that shows how to add custom packages at url below.
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
Hopefully I'll be able to use this guide and make this work.

Thanks,

Dale

---

