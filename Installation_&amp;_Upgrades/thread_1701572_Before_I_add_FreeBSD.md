---
title: "Before I add FreeBSD"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by jeremyjjbrown on 2011-03-06
I'm looking for advice before I add FreeBSD to my laptop. Right now it's happily dual booting with 10.04 and 7

I used to use this great guide.
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Install_your_second_Linux_OS](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Install_your_second_Linux_OS)

Of course because of (the hated) GRUB2 it is now useless. If anyone has experience/advice for me I'd love to hear it.

---

### Post by An Sanct on 2011-03-06
I'm not sure if I understand *question*...

If grub is not working correctly, try to reinstalling it from a Live USB.

Here is a how-to from [my experience.]("http://www1.ubuntuforums.org/showthread.php?p=10440484")

---

### Post by jeremyjjbrown on 2011-03-06
I was just wondering if GRUB2 played nice with FreeBSD, or if I should try the FreeBSD bootloader. Some guys on the FreeBSD forum said to disallow the FreeBSD bootloader from installing and run an update-grub from an Ubuntu livecd.

---

### Post by Dutch70 on 2011-03-07
> **jeremyjjbrown said:**
> I was just wondering if GRUB2 played nice with FreeBSD, or if I should try the FreeBSD bootloader. Some guys on the FreeBSD forum said to disallow the FreeBSD bootloader from installing and run an update-grub from an Ubuntu livecd.

Yes, as long as FreeBSD gives you that option, that would be the way to go. If it doesn't, reinstalling grub from a livecd/usb is not very difficult at all. It's basically 2 commands.

Here is a link that I use & I do it often, because I try diff distro's often. Sometimes I just go ahead and install the bootloader with the distro, and go reinstall grub from a diff distro. with these same directions. 

[[COLOR="Blue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by jeremyjjbrown on 2011-03-07
Thanks Dutch70.

---

### Post by Dutch70 on 2011-03-07
> **jeremyjjbrown said:**
> Thanks Dutch70.

Your welcome.

LMK how everything works out & what you think about FreeBSD, I may try it as well.

---

