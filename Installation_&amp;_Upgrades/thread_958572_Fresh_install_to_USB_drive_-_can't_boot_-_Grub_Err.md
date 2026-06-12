---
title: "Fresh install to USB drive - can't boot - Grub Error 21"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by mrmcd on 2008-10-25
Hello all,

After leaving ubuntu some years back I thought I'd give it another go.
I tried installing xubuntu 8.04 to a USB flash drive using a Thinkpad T23.

The install went well enough, but it seems to have loaded GRUB on my primary hard drive of the Thinkpad _without_ warning me or prompting me.

This is not cool and it is not clear to me what went wrong. Could anyone please explain?


Anyway, I need some way to either modyify or remove GRUB from the primary hard drive such that I can boot Windows XP from it normally again. I'm not a stranger to ubuntu, GRUB, or using UNIX heavily, so please feel free to get nitty gritty.


I see a similar problem in post #6 in this thread:
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

Super GRUB seems to be a possible solution. Could anyone confirm this?

I'm also thikning I could boot with a Windows XP and restore the MBR, but I really don't want to mess with the MBR until I'm sure it would fix this particular problem.

Thanks

---

### Post by caljohnsmith on 2008-10-25
Yes, you can just boot your Windows Install CD and run:
```
fixmbr
```
And your Windows drive should boot fine again. Or like you mentioned, the Super Grub Disk will do the same thing. 

To put Grub in the MBR (Master Boot Record) of your Xubuntu USB drive, you can follow these steps:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Xubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, set your BIOS to boot your USB drive, and you should get the Grub menu. You'll have to slightly modify the Xubuntu entry in Grub to boot it though; so select the first Xubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Xubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. I can help with that if you can get this far, let me know how it goes. :)

---

### Post by mrmcd on 2008-10-25
> **caljohnsmith said:**
> Yes, you can just boot your Windows Install CD and run:
```
fixmbr
```


FIXMBR worked as expected, Windows XP is booting normally off of the primary hard disk.

```
sudo grub
grub> find /boot/grub/stage1

```

This returned `(hd1,0)` which makes sense - hard disk 2, first partition. This was the same default record in menu.lst and it was what I was expecting.

However, after trying the following, it still doesn't boot off of the flash drive. :

```

grub> root (hd1,0)
grub> setup (hd1)
grub> quit

```



Unfortunately, I have to give up here. This type of fiddling is what made me leave Linux in the first place. Maybe the problem is due to the USB 1.1 ports of the T23, the motherboard, or even the Xubuntu installer. In any case, I just don't have time for messing with things like this and I'll have to stick with Windows and OS X on my machines. (Which sort of sucks - I was looking to make a Linux-loaded flash-drive with the Plan9 tools installed for when I'm away from my Mac.)

Now if only the OS were as seamless as the trouble-shooters on this forum... ;)

Anyway, thanks again, your time is appreciated.

---

