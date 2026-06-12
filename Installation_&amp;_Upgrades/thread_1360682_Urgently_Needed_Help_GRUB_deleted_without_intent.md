---
title: "Urgently Needed Help: GRUB deleted without intent"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by madmax.santana on 2009-12-21
I installed Fedora on an existing system of
> - Windows Vista on /dev/sda1
- Linux Ubuntu Karmic on /dev/sda9
- Linux Mint Helena on /dev/sda11
with /dev/sda10 as swap partition...
I had just gone past partition set up when I changed my mind and cancelled the Fedora installation and rebooted.

I had made following changes:
deleted the NTFS partition on /dev/sda7 and reformatted with ext3. The Fedora installer anaconda renamed it to sda11 and then I rebooted...

Now

> GRUB Loading...
File Not Found
grub rescue>
appears... What would I do to get my system back?

Please help as I need to get the system back before evening. It's urgent and important.

---

### Post by madmax.santana on 2009-12-21
Ok... I successfully installed Fedora, but there is a problem as the Fedora has download grub on /dev/sda the bootloader doesn't read any of my Ubuntu or Mint partitions. However my Windows Vista is alright... I need a go from here. Please help.

---

### Post by darkod on 2009-12-21
Restore grub2 for 9.10:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And next time you install another linux after ubuntu first consider which grub you want to run the show. Personally I would keep grub2 from ubuntu on the MBR. In that case you should have told Fedora not to install a bootloader and all of this would be avoided.
You don't need to install grub with any further linux install you make.

---

### Post by madmax.santana on 2009-12-21
Well thanks Darko. I would keep that in mind in future. Although I knew I had to keep Fedora from installing the bootloader but I didn't know how to change that option in installer program. I know now and I shall care in future.

---

