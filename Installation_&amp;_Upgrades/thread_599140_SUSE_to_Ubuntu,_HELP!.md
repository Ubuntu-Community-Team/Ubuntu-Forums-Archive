---
title: "SUSE to Ubuntu, HELP!"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by xjrokee on 2007-11-01
Ok, soooo this will be kind of embarrassing, I have no idea what i'm doing LOL I installed SUSE 10 on my laptop thus no floppy, and I'm trying to convert to Ubuntu (everyone has such nice things to say about it) ANYWAY I can't get my machine to boot from CD after changing the boot option to boot from that drive and by changing the BIOS boot sequence.  I read in some other forum that some machines won't boot from the drive you select because of "isolinux"? Not sure what that means.  Could anyone lend a hand? In laymen's terms? (I mean very very very laymen's terms lol)  Thanks in advace :)

---

### Post by Cato2 on 2007-11-01
This is a little like doing dual boot installation with Windows, assuming you want to keep your SuSE installation for a little while: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Or you can simply tell Ubuntu to wipe out your SuSE installation and install as if this is a new hard disk.  Either way, you should back up anything important onto a separate hard disk or server, as the installation might run into problems.

The real problem is how to get your system booting from a CD - normally it's just a matter of setting the CD boot option in the BIOS.  "isolinux" is just a way of booting from a CD-ROM, and Ubuntu may even use that for installation, but the problem is the BIOS is not trying to run isolinux.

Maybe if you could post more details of machine, BIOS, setup, and what you've tried already in setting BIOS boot sequence?

If all else fails, you could try looking into network based installs of Ubuntu athttps://help.ubuntu.com/community/Installation#head-b751f1c9b3b4e0c27d6bc8828a831de92eb57a70  - however, these tend to be a lot more technical so if you are struggling with the CD-ROM BIOS issue tthey may be too much.

Or try [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/) but that installs Ubuntu into a big file on your SUSE filesystem, which is not what you want, and doesn't work as fast as a real Ubuntu install, but would get you going with Ubuntu.  Note that the Ubuntu files are hidden within a big file on your SUSE partitions, so you can't delete the SUSE parts.

---

### Post by zvacet on 2007-11-01
[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

