---
title: "Custom kickstart CD woes"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by MattNuzum on 2005-06-09
Howdy,

I'm trying to create an automated server installation CD that will set up a computer so that it is ready to install a particular web server application.

I've started down the path that has these three stages:
 * Get kickstart working
 * Customize the installed packages
 * Prune the CD of uneeded packages

Step 1 works, largely. I've created a kicstart file that does basically what the complete install does but with no prompts.

I'm just about through with the second stage and thinking about the third step.  I'm not sure of the process to delete the unneeded packages.

I obtained a list of packages that I need by doing an install, adding a few select packages and then doing dpkg -l to get an 'all installed packages list.'

Can anyone suggest how to remove packages from the CD in such a way as to not cause problems? Also, can anyone suggest how to add packages to the CD that were not there originally?

My kickstart file will be at [http://newz.gotdns.com/ks3.1.cfg](http://newz.gotdns.com/ks3.1.cfg) for now.

For the record, I made the kick start install CD by doing this:
 * copying ks.cfg to /isolinux/ks.cfg
 * editing /isolinux/isolinux.cfg and modifying the second line:
```
APPEND ks=cdrom:/isolinux/ks.cfg preseed/file=/cdrom/preseed/server.seed vga=normal initrd=/install/initrd.gz ramdisk_size=12288 root=/dev/rd/0 rw --
```

(note that you must have a / before isolinux/isolinux.cfg)
I'm doing some testing and the preseed part may need to be left out.

Burn the CD with this command from the root of the folder where your cdrom files are:

```
mkisofs -o ../ks.iso -r -J -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin -c isolinux/boot.cat .
```

---

