---
title: "Triple Boot:: help"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by fparri on 2013-01-08
Hello,

As of now my box is set up in order to dual boot with GRUB (ubuntu and windows 7). I would like to add Windows 8 and also keep Windows 7, so I reduced Win7's partition and got some free space on my HD.

What's the easiest way to add windows 8 and get a triple boot setting? Will Windows 8 discover the other partitions and let me install them, Ubuntu included?

If not, what can I do to get it working? :))))

Thanks a lot in advance

---

### Post by sudodus on 2013-01-08
First of all, to edit partitions and and install new distros can go wrong, so before doing anything more, please ***backup up*** your hard disk drive or at least your personal data.

(I haven't done what you want to do with Windows 8, only installed the Developer's Preview version onto a clean drive.) Previous Windows versions could install alongside with older Windows versions. But they forgot about Ubuntu, so afterwards it is necessary to boot Ubuntu from an install CD/USB drive and reinstall grub. The last part is described in this link

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")

So I suggest that you backup your data to an external disk or to the cloud, while you are waiting for better replies :-)

---

### Post by fparri on 2013-01-08
Thanks a lot for the link.

I guess the easiest option to reinstall Grub seems to be using Boot Repair, right? :)

---

### Post by sudodus on 2013-01-08
> **fparri said:**
> Thanks a lot for the link.

I guess the easiest option to reinstall Grub seems to be using Boot Repair, right? :)
If you know and like it, use it :-)

---

### Post by oldfred on 2013-01-08
If you have a primary partition left best to install to a primary partition. Windows uses only one active partition or the one with the boot flag, so second installs always boot from the first install. And second installs take over the first install. The second install will have no boot files.

While Vista, still applies:
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

This also applies if dual booting just 7 and 8:
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

