---
title: "[lubuntu]Can not boot live session from DVD or USB"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by wolfsong73 on 2016-10-22
Hi all, 

So, I've spent an hour trying to figure this out (Google, etc) and am at a complete dead end.

I'm trying to check out Lubuntu on my system here prior to installing, as I'm trying to choose which distro I want to go with.

Now, Linux Mint and Linux Lite (which I believe is also based on Ubuntu?) boot just fine from DVD. Last I checked, so does Ubuntu itself.

However, Lubuntu just refuses to boot at all, either from the DVD or from the USB (created with unetbootin). In both cases, I ultimately end up with my monitor going into standby 'cause there's no activity. The DVD rom drive will stop reading and I guess the USB isn't being accessed, either (hard to tell). 

My mobo is a GIGABYTE GA-990FXA-UD3 R5, and it has a dual bios supporting both UEFI and Legacy. I've tested it with both UEFI enabled, and disabled. Doesn't make a difference, same thing happens, again, regardless of whether from DVD or USB. 

I looked and there's no SecureBoot setting I can see anywhere in the BIOS settings.

I can confirm that Mint and Lite load just fine even with UEFI. 

Incidentally, I'm having the same trouble getting any flavor of Arch to work (Antergos or Manjaro) - I know this isn't a forum about them, but I just wanted to add that detail, in case it might provide a clue to someone familiar with those distros as well as to what might be going on.

Anyway, any help is greatly appreciated!

Thanks much!

---

### Post by Bucky Ball on 2016-10-22
*Thread moved to **Installation & Upgrades**.*

Which graphics card?

```
sudo lshw -C video
```

---

### Post by wolfsong73 on 2016-10-22
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*Which graphics card?```
sudo lshw -C video
```Hi there.I'm on a GeForce GTX970

---

### Post by sudodus on 2016-10-22
Then you should try linux distros with the newest possible linux kernels. Ubuntu 16.10 is more likely to work than Ubuntu 16.04 LTS. But you might also need the boot option nomodeset. See this link and links from it for details how to apply boot options,

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by wolfsong73 on 2016-10-22
> **sudodus said:**
> Then you should try linux distros with the newest possible linux kernels. Ubuntu 16.10 is more likely to work than Ubuntu 16.04 LTS. But you might also need the boot option nomodeset. See this link and links from it for details how to apply boot options,[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)Thanks for that! Though from what I'm seeing there, it looks like those settings are intended for if you're doing an actual install? I'm just wanting to run from the live disc to check it out before deciding which one I want to use.

---

### Post by wolfsong73 on 2016-10-22
> **sudodus said:**
> Then you should try linux distros with the newest possible linux kernels. Ubuntu 16.10 is more likely to work than Ubuntu 16.04 LTS. But you might also need the boot option nomodeset. See this link and links from it for details how to apply boot options,


[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)


Thanks for that! 


Though from what I'm seeing there, it looks like those settings are intended for if you're doing an actual install? I'm just wanting to run from the live disc to check it out before deciding which one I want to use.

---

### Post by oldfred on 2016-10-22
Gigabyte boards often need IOMMU setting in UEFI changed and a boot parameter.
        GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 
    
And nVidia normally needs the nomodeset boot parameter (or you probably need at least two to install & first boot, nomodeset & iommu=soft).
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL][https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

NVIDIA 970  with 14.04 - Bucky Ball
[https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433) 

 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by Bucky Ball on 2016-10-22
I have that very same card and works fine in 16.04. Nothing to do with needing 16.10. That is NOT a new card. Been out for a year or more. ;)

Use the 'nomodeset' option and when you are installed, open 'Software and Updates' and make sure the Canonical Partners repo is enabled. Do an update then check in 'Additional Drivers' and you will find the correct driver there (the 'proprietary, tested' one, 361.42). 

And that's about all you should need to do. Do NOT tick 'Install third-party drivers' or 'Update during install' when installing the OS.

PS: Doubt you'll be able to do this on a Live session. If you do manage, any changes you make will be lost on reboot.

---

### Post by sudodus on 2016-10-23
@Bucky Ball,

Did you try Yakkety live with your nvidia GeForce GTX970 card? I'm curious, because I might get the same kind of nvidia card. Does nouveau work out of the box, or do you need nomodeset also with Yakkety? (My experience is that after some time, nouveau will catch up and work, but maybe not with all chips/cards.)

---

### Post by Bucky Ball on 2016-10-23
Sorry, haven't tried with Yakkety but will give that a go later if I get time and report back. I installed in a hurry and a flurry and had to get this machine working quickly in February so much water under bridge during this busy year. Didn't take notes of that process unfortunately. From memory, the live 16.04 worked fine if that tells you something. ;)

---

### Post by T2uiYKb7 on 2016-10-23
At the menu where it says "Try Ubuuntu Without Installing" press "e" then remove the word [COLOR=#0000cd]quiet [/COLOR]and write [COLOR=#0000cd]nomodeset [/COLOR]in it's place.

That will make it show what it's doing instead of a blank screen and also hold off on the video drivers until the desktop loads. It fixes this problem on a bunch of Linux distributions on my tablet.

---

