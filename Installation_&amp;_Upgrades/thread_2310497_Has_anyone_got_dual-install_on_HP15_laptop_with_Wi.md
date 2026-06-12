---
title: "Has anyone got dual-install on HP15 laptop with Windows 8.1 preinstalled?"
date: 2016-01-19
forum: Installation &amp; Upgrades
---

### Post by t0p on 2016-01-19
I have a HP15 laptop - model 15-g261sa - and try as I might I cannot get Ubuntu on it. It has Windows 8.1 on it, which I would like to keep as a dual-install, but I am willing to wipe that and replace it with Ubuntu, if I was sure the install would work. I have looked around a lot for info on how I could get Ubuntu on my laptop and tried out many how-tos, but the result has always been that the laptop will only boot to Windows. If I went for the Ubuntu-only install, I'm terrified I'd just end up bricking my machine, which I can't afford to have happen.

I can't even install Ubuntu in VirtualBox on the computer. And I have tried, many times, with many versions of Ubuntu. I tend to get an error message at the start of the install process, when I run the .iso - it's a very quick message, white text on the black background, I don't get a chance to read exactly what it says, but the gist is that I should "update my BIOS". I'm running the latest version of VBox, so that message doesn't make sense to me. Then sometimes the "live session" will start, I'll go through the installation process, restart it - and I get an input username password loop. Or it will not let me start an install at all.

The only way I can use Ubuntu on my laptop is by using persistent usb sticks (at first it wouldn't see my wireless card, but after a strange, unfinished install of "bcmwl-kernel-source" on the persistent stick it now *does* let me use wifi...) but of course running Ubuntu in live session is a poor imitation of the real thing. Every time I want to get online I have to install ad-blocker and https-everywhere on firefox (why aren't *they *persistent when the wifi driver is?) I can't use my VPN account, and of course it's slooow compared to a bare-metal install. When I'm out I get tempted to use Windows when I'm near a wifi hot-spot... but that wouldn't be a good move, what with my complete lack of Windows street-smarts (I've been an Ubuntu user for years).

I have been driven to this ranting plea for help because I have tried everything I've found online to get this install done and none of it has worked. Is there anyone who knows how to do it? It's a Hewlett Packard HP15, model 15-g261sa - it's blue, if that makes any difference (see how unbalanced I've become?). Someone, please, ***HELLLP******!***</rant>

If you're still reading this, thank you.

---

### Post by oldfred on 2016-01-20
All HPs seem to violate UEFI spec. The spec says not to use description as part of UEFI boot, and of course the only valid description is "Windows". But there are various work arounds.

If dual booting we can use the UEFI fallback or default hard drive entry. You then have to boot hard drive entry not ubuntu nor Windows.
Or if only booting Ubuntu we just change description from "ubuntu" to "Windows Boot Manager" but use Ubuntu/grub shimx64.efi as actual boot file. Often good idea to also copy shim to bootx64.efi, so two different entries should work.

       Details in link in my signature below and:
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
      
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by t0p on 2016-01-21
Thanks, I'll check out what you suggested and the links you provided when I get the chance.  Unfortunately I can only sit down to attempt an install when I've got a fair chunk of free time as my experience has been that trying it on the laptop takes a while.

I'll post results and, if I get it to work I'll write how and mark the thread [Solved] so anyone else out there with this model of HP laptop might learn from my results.  Fingers crossed eh!

This UEFI is such a pain... next time I get a computer I'm going to have to do some detailed research first so I don't waste my money on a machine that refuses to do as it's told.  I really do think UEFI is some kind of Microsoft-engineered scam.  Maybe I'll find somewhere in the UK that sells inexpensive laptops with Ubuntu installed...

Thanks!

---

