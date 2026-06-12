---
title: "[grub] error: out of disk"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by kirschre911 on 2010-12-10
Hi all
Trying to do a new install of ubuntu 10.10 to my laptop. Installation and all works fine, but upon rebooting, after the bios screen i get:
```
error: out of disk.
grub rescue>
```I tried using following some instructions i found after googling for the problem:
```

[LIST=1]
[*]ls (displays the partitions and devices Grub can see)
[*]set prefix=(hdX,Y)/boot/grub
[*]set root=(hdX,Y)
[*]set (shows Grub's environment; inspect the prefix= listing; make sure it matches what you set in step 3)
[*]ls /boot/ (should show the contents of your system's /boot -- kernels, initrd images, the grub folder, etc)
[*]insmod /boot/grub/linux.mod
[*]linux /vmlinuz root=/dev/sdXY ro
[*]initrd /initrd.img
[*]boot
[/LIST]

```but after the 5th step, i get another "error: out of disk" message.
The odd thing is that I had an install of 10.10 on this laptop a month ago, and it worked fine. As a side note, I installed fedora 14 after this happened, which worked fine. Reinstalled ubuntu, and it was back to the same problem. I also tried installing with a kubuntu cd I had, to make sure it wasnt the install media, and had the same problem. I'd appreciate it if anyone could help me out.

---

### Post by oldfred on 2010-12-10
Can you post your actual drive,partitions that ls found not the X,Y?

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

This will also give lots of detail to help fix your system.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by kirschre911 on 2010-12-11
I think i fixed the problem... I created a new partition table on the drive and manually set up partitions for a clean install, and everything appears to work right now. I don't know what could have been the problem before, as I just used the default use the entire disk settings, but im glad its working now.
cheers for the help and quick reply tho :)

---

