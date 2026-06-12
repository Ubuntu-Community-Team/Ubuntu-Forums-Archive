---
title: "Dual Boot Grub Problem"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by djmashedman on 2010-04-05
So I had ubuntu 9.10 happily installed.
I installed windows vista as instructed here - 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

I got vista installed fine. Then I wanted to reinstall grub.
So I did this - 
root (hd0,0)
setup (hd0)

for which it gave an error, I don't remember exactly which. (sorry)
Anyway, I booted into a karmic live cd, opened up terminal, and attempted to install grub as instructed here

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Everything seemed to go fine, but now when I rebooted I am greeted with a nearly blank screen which reads

"Minimal BASH-like line editing is supported. ..."
and
"grub> _"

with no operating systems listed.
So I try to boot into ubuntu so I can attempt to fix grub as follows  (as listed here [http://forums.fedoraforum.org/showthread.php?t=211383](http://forums.fedoraforum.org/showthread.php?t=211383))
- 

root (hd0,4)
kernel /boot/vmlinuz- (whatever the kernel is called)
initrd /boot/initrd (whatever the kernel is called)
boot

It seems to go ok until it stops and says 
"Gave up waiting for root device" and lists common problems
then
"Busybox v1.13.3 ... built-in shell (ash)"
and 
"(initramfs) _"


Just wondering what the hell is going on and how can I fix it?
I can mount both my ubuntu and vista partitions in the karmic live cd, so it's definitely a grub problem.
I had a similar problem a while ago because I was being stupid and messed up files in my grub folder, instead of fixing it I just reinstalled ubuntu, though this time I'd rather get it fixed.

Any help getting this sorted will be much appreciated.
Thanks!

---

### Post by kansasnoob on 2010-04-05
Please boot to your Ubuntu Live Desktop and then post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2010-04-05
The apc & fedora sites are older and fine for old grub legacy, but with Karmic as a new install you have grub2 and can only follow the directions for grub2. If you installed parts of grub legacy grub2 may not work.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by djmashedman on 2010-04-05
THANK YOU!
Followed what that link said, oldfred, and it restored grub perfectly.
Then it was a simple update-grub and everything appears and loads as it should.

Many thanks, both of you. Speedy replies too. :)
Oh, how I love ubuntu.

---

