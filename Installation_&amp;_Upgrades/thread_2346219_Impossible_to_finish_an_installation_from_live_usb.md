---
title: "Impossible to finish an installation from live usb"
date: 2016-12-12
forum: Installation &amp; Upgrades
---

### Post by SilentSib on 2016-12-12
Hello,

I've been using Ubuntu for years on my laptops and have decided to install it as dual boot with Windows 10 on my newly-received rig. Problem is that no matter what I'm trying, I can't finish up the installation. Either it hangs after having selected "try..." or "install..." and then automatically reboots, or I manage to get further into the live usb, start the install process and have the computer suddenly reboot too...

Some info that could be useful to troubleshoot:

- Motherboard: Z97 Pro Gamer
- RAM: 16GB
- CPU: i7-5775c
- GTX 1070
- Dual screens
- Windows 10 installed as UEFI, trying to do the same with Ubuntu

What I've tried so far: nomodeset, noacpi, having only the integrated graphics card enabled when running the live usb, disabling fast boot, secure boot, usb stick reformatted even though it had been used successfully to install ubuntu on my laptop... I'm running out of ideas and I've yet to find a thread with the similar problem I have. I really don't know what's going on, and not having any log doesn't make it any easier for me to troubleshoot the issue. The one constant in this is the automatic reboot of the system after the live usb process hangs or the install process hangs... And yes, Windows 10 works perfectly fine.

Thanks in advance for your help!

---

### Post by oldfred on 2016-12-12
That is an Asus Z97?
I have the Asus Z97-AR and it works in UEFI mode, but I do not have Windows.
I did make many UEFI settings changes. And had to document most of them as installing latest UEFI reset most of them back to defaults.

I made a mistake getting the -AR as it has DisplayPort and HDMI, but my monitor has VGA & DVI. So I had to add an older nVidia 620GT. And that even worked without the nomodeset. And that was my first install, all with nVidia that did not need nomodeset. But with Intel you should not need nomodeset. Older versions of Ubuntu (15.10) did need a boot parameter for Intel, but newer should not.

I turned off Secure boot which really was Windows or Other setting.
Change USB support from partial to full.
Next boot after power failure to Full.
UEFI boot to UEFI only.
Network boot to ignore (will not use it)
Boot storage to UEFI first, UEFI & BIOS did not work.
Boot PCI-E UEFI only, but not really used.

I turned off fast boot until configured. Then set to 3 sec and have grub at 3 sec, which is most of my boot time as I have an 840 SSD for boot and HDD for data.

 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by SilentSib on 2016-12-13
Hi,

Thanks for your answer. Yes, my motherboard is an Asus Z97 Pro Gamer. From what I understand in what you mentioned, I shouldn't even have to use nomodeset. But if I don't and I boot on the live USB, I end up having a black screen after choosing "try..." or "install...". I'll try changing the options you mentioned and will report back. Hopefully this can get fixed.

---

### Post by oldfred on 2016-12-13
I did not notice till I checked manual that there is a motherboard setting for video.
It defaults to auto, which not sure then which video it uses. You may want to experiment with setting.

One user did say he was just able to use Intel video to install and manually installed nVidia driver. Then changed video cable to nVidia and it worked. Not sure what motherboard he had.

You will need the ppa to get newest driver. Do not install video from nVidia directly with .run file.
       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

---

### Post by SilentSib on 2016-12-13
Hi,

So I've applied what you mentioned and I think there's definitely progress. Out of 3 boots on the live usb, there was only one freeze prior to being on the install interface from Ubuntu. Both times when I managed to get there without a hitch, it showed that the system files had finished being copied and that the system was starting to be installed. From there, the system froze and rebooted. Once at the very beginning, and another time after a few percents of the installation made. Any new ideas about what could be blocking the actual installation?

[IMG]http://i.imgur.com/4ufPzS7.jpg[/IMG]

Thanks,
SilentSib

---

### Post by ubfan1 on 2016-12-13
Did you hashcheck the downloaded ISO?  I'd turn off wireless/internet access if that was on, it might cause problems if there are driver issues.

---

### Post by SilentSib on 2016-12-14
I just did check the hash, yes, and it matches... Plus, as I said before, this was the same usb stick I had previously used to successfully install ubuntu on my laptop, so I doubt it comes from there. I already disabled wifi/internet access for that exact same reason as I had already read something about drivers disturbing the installation. Anything else? :D

Is there no way for me to do the whole thing in command line from beginning to end? At least I'd get verbose and would be able to tell if there's a kernal panic happening or something...

Edit: I'll try this whenever I've got some time in the meantime: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by oldfred on 2016-12-14
Are you partitioning in advance with gparted from live installer?

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by SilentSib on 2016-12-14
Yep... Note that at some points during the many many attempts I've made I actually encountered a kernel panic saying this, followed by a reboot after 30sec:

```
[COLOR=#545454][FONT=arial]Kernel panic - not syncing: Timeout: [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**Not all cpus entered broadcast exception handler**[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR]
```

I've looked that up in Google but couldn't find anything concrete that could help me. I have this very strange feeling that the reason the system crashes in the graphic interface is actually caused by this same kernel panic. It's just that I can't prove it...

---

### Post by oldfred on 2016-12-14
If you totally unplug graphics card, does it then work?

---

### Post by SilentSib on 2016-12-16
I ended up trying a different live custom iso that let me finish the installation withoutany crash or reboot. I now have a few drivers-related bugs to fix but that's not for this thread. I have no idea why I couldn't properly use the official ubuntu iso but well.... the important is that it now works. Thread solved!

---

