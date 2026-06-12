---
title: "Installing Windows after Ubuntu"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by linnerd40 on 2007-01-10
Soon I will have to load windows on to my machine again. I have been windows free for about a year now... so this is a sad moment. But, I need Autodesk inventor and 3dsmax. So, my question is, since I am installing Windows after i installed ubuntu.... how will be able to boot into Ubuntu? Will this method work:

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

To restore GRUB? If not, what is there to do? I'll be installing Windows XP Pro 64bit edition, if that is any help. It will be on my 40gig hard drive (/dev/hda). Ubuntu is on my 250gig (/dev/hdb). 

Thanks!

---

### Post by gcampathome on 2007-01-10
Hi, just recently installed Ubuntu and then Automatix.  I saw that one of the packages Automatix can install is VMware Player.  I haven't used this, but it might be an option to run Windows in Ubuntu.  I've also heard that Parallels works really well for this but requires lots of memory.

     - Gary -

---

### Post by linnerd40 on 2007-01-10
Yeah, virtual machines are definitely not an option for me. I need true performance. I've tried WINE... and it doesn't work that well. Thanks for the reply though!

Any other ideas?

---

### Post by confused57 on 2007-01-10
Maybe you could do it this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

This way, all you would do is set your bios to boot first from the Ubuntu drive & add an entry to your /boot/grub/menu.lst to boot your Windows drive.

First you might want to check the output of:
```
sudo fdisk -l
```
The -l is a small "L", which you probably already know.

If your root partition in menu.lst is (hd0,0), the above should work without any reconfiguring...if you set bios to boot first to the Ubuntu drive, but if the kernel line shows root=/dev/hdb1 & you switch the drive to hda, you'd need to change the root designation in the kernel line.

---

### Post by linnerd40 on 2007-01-10
That looks good! I'll have to try that! Thanks!

---

### Post by octokiddie on 2007-01-12
check this
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

