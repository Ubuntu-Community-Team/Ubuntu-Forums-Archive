---
title: "Ubuntu and XOSL"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by eniali on 2008-05-05
Foreword: I am VERY new with Linux.

I am quite fond of XOSL (v 1.1.5) boot loader and would like to continue using it with my new Ubuntu installation.

Unfortunately Ubuntu and XOSL do not seem to like each other. When I install XOSL and try to boot the Ubuntu partition, it just does not work. When I uninstall XOSL, Ubunto does not start anymore.
With Windows it works...

Does anyone have any hint on how to make Ubuntu boot from XOSL?
Thanks.

---

### Post by hvw on 2008-05-17
:-kThat release is not up to date because of date (December 23, 2000). So may be you would try xosl2:
[http://www.sourceforge.net/projects/xosl2/]("http://www.sourceforge.net/projects/xosl2/")
This comparation table lacks of data about xosl:
[http://en.wikipedia.org/wiki/Comparison_of_boot_loaders]("http://en.wikipedia.org/wiki/Comparison_of_boot_loaders")
Aso you can try gujin
[http://en.wikipedia.org/wiki/Gujin]("http://en.wikipedia.org/wiki/Gujin"), but I've never tried it.
When you install boot loader on external USB (FAT-formatted) drive you should use 'syslinux' which is aviable in repository. As you can see on Wiki:
[http://en.wikipedia.org/wiki/Syslinux]("http://en.wikipedia.org/wiki/Syslinux")
Syslinux has also abilities like other bootloaders to boot up linux. Actually, it works as well with live-CD-preinstalled squashfs-compacted version of Ubuntu (on FAT formatted drive, actually).

---

### Post by Aearenda on 2008-05-17
WHen you installed Ubuntu, did you allow GRUB to be installed onto the partition where Ubuntu is? I suspect XOSL needs to chainload to Grub. Just a thought - I don't know XOSL.

---

### Post by eniali on 2008-05-19
Thanks for your replies gents.

I got it working this weekend (not much time during the week :( ). The initial problem was that I did not tell GRUB to be installed on linux partition (hd0,1) and it was installing at the MBR. Unfortunately XOSL was not compatible with this, although it is said that XOSL creates a mirror of the MBR and saves it as a file which is loaded during boot time.

On my second attemp I installed GRUB on (hd0,1), where linux is installed, and it worked in the sense that I got the GRUB menu. Unfortunately the keyboard had become inactive and GRUB timeout did not work at all.
It still is the same but I found the workaround, which is modifying GRUB menu.lst using Ubuntu live - removed all other entries except the default one and set the timeout to 0.

Thanks for the tip on XOSL2 :cool:. I was not aware the new version was out. Will give it a try.

---

### Post by hvw on 2008-05-22
I also have Lilo installed on (hd0,x) because of Apple EFI. And also have inactive keyboard.
You can also try lilo. Install it from Live CD:
$ sudo mkdir /target
$ mount /dev/<partition> /target // your linux partition
$ mount -t proc none /target/proc
$ mount -o bind /dev /target/dev
$ sudo chroot /target /bin/bash
$ sudo aptitude install lilo
replace in /target/etc/fstab file <UUID...>, comment it with "#" and add line with /dev/sd.. instead of. Then type:
$ sudo liloconfig
I've installed it on /dev/sda3. There are only one default entry in lilo menu, it works as well for me. And MBR is free for XOSL.

---

