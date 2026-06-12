---
title: "Virtualization: Is it better to have Windows virtualized in Ubuntu, or vice-versa?"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by N17r0usAn931 on 2009-12-15
Hello,

I have used Ubuntu and Windows Vista side by side for almost two years, but I often tire of having to reboot to switch between the two operating systems. I recently downloaded Ubuntu 9.1 and purchased Windows 7, however, I am considering a virtualized configuration utilizing Sun VirtualBox rather than a dual-boot. 

My question: In your opinion, is it better to use Windows or Linux as the host operating system, and why?

Note: It seems that Ubuntu has very poor driver support for connecting to networks with hidden SSIDs with BCM43xx cards, and this may be a primary deciding factor in determining which operating system I use as the host... (Normally I would just enable broadcasting the SSID as hiding it doesn't really add and security, but its not my network... :( ) If anyone knows anything about this issue within Ubuntu 9.1 , please let me know about that as well. :D

---

### Post by snowpine on 2009-12-15
Personally, I have Windows XP virtualized within Linux, for two very simple reasons:

1. I use Linux 99% of the time
2. Snapshots... if my virtual Windows gets a virus, it's really easy to restore the snapshot (don't even have to reboot the computer).

Your wireless issue might be a wrinkle, of course... have you tested it with an Ubuntu 9.10 Live CD?

---

### Post by N17r0usAn931 on 2009-12-15
> **snowpine said:**
> Personally, I have Windows XP virtualized within Linux, for two very simple reasons:

1. I use Linux 99% of the time
2. Snapshots... if my virtual Windows gets a virus, it's really easy to restore the snapshot (don't even have to reboot the computer).

Your wireless issue might be a wrinkle, of course... have you tested it with an Ubuntu 9.10 Live CD?

I'm hoping that virtualizing Ubuntu or Windows will make me use Linux more... 

I've tried testing it with the Live CD, however, to use restricted drivers usually requires a reboot, and I was unable to find the correct commands load the BCM43xx STA driver module and complete installation without reboot (which isn't possible using the Live CD).

Thanks for the Reply! :)

---

### Post by presence1960 on 2009-12-15
> **N17r0usAn931 said:**
> **_I'm hoping that virtualizing Ubuntu or Windows will make me use Linux more... _**

I've tried testing it with the Live CD, however, to use restricted drivers usually requires a reboot, and I was unable to find the correct commands load the BCM43xx STA driver module and complete installation without reboot (which isn't possible using the Live CD).

Thanks for the Reply! :)

If you want to use Linux more just boot into Linux. Make it a concious decision, you do not need virtualization to decide to use Linux more.

I would put Windows on Virtualbox inside of Linux. You want the host OS to be more stable than the Guest OS is my thinking.

---

### Post by N17r0usAn931 on 2009-12-15
> **presence1960 said:**
> If you want to use Linux more just boot into Linux. Make it a concious decision, you do not need virtualization to decide to use Linux more.

I would put Windows on Virtualbox inside of Linux. You want the host OS to be more stable than the Guest OS is my thinking.


Well, actually, virtualization (of either OS) would allow me quick and easy access to my MS Outlook Calendar, which is actually what drove me back to Windows in the first place. I use calendar sharing extensively, and I've tried several free linux-compatible alternatives (Mozilla Sunbird/Thunderbird/Lightning, Evolution, etc.), but they don't offer the sharing compatibility that I need with MS Outlook...  That, the bit of gaming that I do, and my need to understand the Windows OS are the only reasons that I have windows hanging around... However, the one thing that Windows has going for it is that proprietary drivers are generally made available via the vendor rather than having to be reverse engineered, and as a general rule, I've found Windows drivers to be more stable...

I think that if I can resolve the hidden SSID issue with Ubuntu 9.1, I'll try Ubuntu out as the host OS...

---

### Post by presence1960 on 2009-12-15
> **N17r0usAn931 said:**
> Well, actually, virtualization (of either OS) would allow me quick and easy access to my MS Outlook Calendar, which is actually what drove me back to Windows in the first place. I use calendar sharing extensively, and I've tried several free linux-compatible alternatives (Mozilla Sunbird/Thunderbird/Lightning, Evolution, etc.), but they don't offer the sharing compatibility that I need with MS Outlook...  That, the bit of gaming that I do, and my need to understand the Windows OS are the only reasons that I have windows hanging around... However, the one thing that Windows has going for it is that proprietary drivers are generally made available via the vendor rather than having to be reverse engineered, and as a general rule, I've found Windows drivers to be more stable...

I think that if I can resolve the hidden SSID issue with Ubuntu 9.1, I'll try Ubuntu out as the host OS...

That is a little more detailed info. Given that rather than just the generalized info given first I would say you need to use which ever OS as host that allows you to do what you need to do.

I keep Windows around for Adobe Acrobat Professional and for work as most employers do not want Open Office due to formatting incompatibilities.

---

### Post by wojox on 2009-12-15
Look into Google Calendar. You can share it with the world. I vote VM Windows as well.

---

### Post by snowpine on 2009-12-16
> **N17r0usAn931 said:**
> Well, actually, virtualization (of either OS) would allow me quick and easy access to my MS Outlook Calendar, which is actually what drove me back to Windows in the first place. I use calendar sharing extensively, and I've tried several free linux-compatible alternatives (Mozilla Sunbird/Thunderbird/Lightning, Evolution, etc.), but they don't offer the sharing compatibility that I need with MS Outlook...  That, the bit of gaming that I do, and my need to understand the Windows OS are the only reasons that I have windows hanging around... However, the one thing that Windows has going for it is that proprietary drivers are generally made available via the vendor rather than having to be reverse engineered, and as a general rule, I've found Windows drivers to be more stable...

I think that if I can resolve the hidden SSID issue with Ubuntu 9.1, I'll try Ubuntu out as the host OS...

Given these new details (you want to play games and use proprietary Windows hardware drivers) I am changing my recommendation to Windows host, Ubuntu guest. :)

---

### Post by egravede on 2009-12-16
Let me know which one you decide and how its working for you, I've actually been thinking of doing the same thing on my laptop.  I use Ubuntu at work so having a home client would ease the learning curve.

---

### Post by N17r0usAn931 on 2010-01-07
I ended up reformatting with Windows 7 as a host and Ubuntu as a guest. Mostly because I tried to use Ubuntu as the host, but I ended up with all sorts of nasty driver issues (laptop), and I decided that it probably wasn't worth the time spent trying to work them all out.

After nearly a month of use, I find that I have not really used the Ubuntu VM at all. I have to say, after the excellent driver support that was provided in Ubuntu 9.04, that 9.1 was sort of a let down. 

Thanks for all of your input!

---

