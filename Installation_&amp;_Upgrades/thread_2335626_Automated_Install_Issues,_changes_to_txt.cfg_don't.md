---
title: "Automated Install Issues, changes to txt.cfg don't appear in GRUB list."
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by tjmatt on 2016-08-30
Hi,

I really need to get this to work, and am struggling with what seems to be an easier part of an automated install process.  Basically, I'm trying to create a .iso file for an automated install process for 16.04.1, following a few different tutorials, I clearly need to edit the txt.cfg file to add an "Automated Install" label, with info on where to find a kickstart/preseed file, among other things.  Regardless of my changes to that file, when I write to a .iso, create a bootable usb from the ISO, and then try to use my "Automated Install" label when GRUB appears, my new option won't appear (or any other changes, for that matter).  

I'm basically following these tutorials, so it's possible the information I have is outdated:
[https://archethought.wordpress.com/2015/03/29/ubuntu-bootable-usb-with-kickstart/](https://archethought.wordpress.com/2015/03/29/ubuntu-bootable-usb-with-kickstart/)
[http://gyk.lt/ubuntu-14-04-desktop-unattended-installation/](http://gyk.lt/ubuntu-14-04-desktop-unattended-installation/)

I don't think the issue is with my kickstart or preseed files, as I should be able to add a new label/option in GRUB anyway.  I'm basically using the same label as from the tutorial, but I've tried various modifications and nothing seems to work.  I'm guessing that I need to edit either a different file, or make changes in another file so that changes to txt.cfg appear?  Sample label:

```
label autoinstall
  menu label ^Automatically install Ubuntu
  kernel /install/vmlinuz
  append file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz ks=cdrom:/ks.cfg preseed/file=/cdrom/ubuntu-auto.seed quiet --
```

I've tried ending with both "---" and "--" as I've seen that vary in different tutorials.

I'm using a 16.04.1 64bit Server ISO for the original files, making an editable copy, making my changes / adding files, and then writing a new .iso.  Just say if there is any other information I can provide, I'd *really* like to get this to work, so I appreciate any help.  I can't believe there isn't a better way to do automated installations for Ubuntu, but maybe I'm missing something?

---

