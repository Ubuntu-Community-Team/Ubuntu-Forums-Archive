---
title: "Cannot install Ubuntu 12.04 on HP Pavillion"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2013-03-19
Hi,

I am trying to install Ubuntu (12.04) on an HP Pavillion dv5000.

The CD kicks in, and I get the purple screen with the Ubuntu logo and the white/red dots turning over. The installation freezes there and does not proceed.

The same thing happens with Lubuntu 12.04.

How can I resolve this? Any help gratefully received.

Many thanks.


P.S. Windows XP just installed afresh on the same machine with no trouble.

---

### Post by oldfred on 2013-03-19
How much RAM and what video. 

If nVidia you need nomodeset. Both for live install and first boot after install until nVidia drivers are installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by rdh61 on 2013-03-19
ATI Radeon Xpress 200M
1GB RAM

I'll try with nomodeset later this evening.

---

### Post by rdh61 on 2013-03-19
No joy with nomodeset.

This time after the Ubuntu logo and dots have finished, I get a black screen with a flashing cursor. The installation does not proceed past this point.

Can you suggest which other boot options I might try?

---

### Post by rdh61 on 2013-03-19
I have now tried ALL the boot options. None of them allows me to successfully install Ubuntu.

---

### Post by tejpatel98 on 2013-03-19
Are you trying to wipe the computer and install Ubuntu over the whole hard drive, or dual boot?

---

### Post by oldfred on 2013-03-19
Have you tried both the generic or the Radeon setting. Link is old, but video issues are still the same.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by rdh61 on 2013-03-20
> **tejpatel98 said:**
> Are you trying to wipe the computer and install Ubuntu over the whole hard drive, or dual boot?

Wiped hard drive and installed fresh Windows XP. Now trying to install Ubuntu alongside Windows so I can dual boot.

---

### Post by rdh61 on 2013-03-20
> **oldfred said:**
> Have you tried both the generic or the Radeon setting. Link is old, but video issues are still the same.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]


I tried the Radeon setting - no joy. I haven't tried the generic setting. I'll read the link, try the settings, and give feedback. Thanks.

---

### Post by rdh61 on 2013-03-20
I also began the installation without quiet splash, to see at what point it stalled, and got this;

b43-phy0 ERROR: Firmware file "b43/ucode.5fw" not found.
b43-phy0 ERROR: Firmware file "b43-open/ucode.5fw" not found.
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

I will have a look at this now.

---

### Post by rdh61 on 2013-03-20
> **rdh61 said:**
> I also began the installation without quiet splash, to see at what point it stalled, and got this;

b43-phy0 ERROR: Firmware file "b43/ucode.5fw" not found.
b43-phy0 ERROR: Firmware file "b43-open/ucode.5fw" not found.
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

I will have a look at this now.

I've now looked at this. But how on earth am I supposed to install the required packages when I haven't yet installed Ubuntu itself???!!!

---

### Post by rdh61 on 2013-03-20
> **oldfred said:**
> Have you tried both the generic or the Radeon setting. Link is old, but video issues are still the same.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]


I have now tried the Radeon setting and both of the generic settings with the same (negative) result. The sticking point is always the same as that described previously.

---

### Post by tejpatel98 on 2013-03-20
> [COLOR=#000000]Wiped hard drive and installed fresh Windows XP. Now trying to install Ubuntu alongside Windows so I can dual boot.[/COLOR]
So then can't you just use Wubi, although I still don't understand the difference from dual booting from the CD or using Wubi.

---

### Post by rdh61 on 2013-03-20
> **tejpatel98 said:**
> So then can't you just use Wubi, although I still don't understand the difference from dual booting from the CD or using Wubi.

Wubi installs Ubuntu on the Windows partition. This apparently slows it down and makes it more vulnerable to crashes and hard boots. I would much prefer my Linux on a separate partition. Thank you.

---

### Post by rdh61 on 2013-03-20
I am hopeful that this may provide a solution...

Boot option: [COLOR=#000000]*b43.blacklist=yes*[/COLOR]

[http://ubuntuforums.org/showthread.php?t=1966655](http://ubuntuforums.org/showthread.php?t=1966655)

I'll try it out tonight.

---

### Post by rdh61 on 2013-03-20
The boot option *b43.blacklist=yes* allowed the installation to proceed (I decided to install Lubuntu, as it's an old computer).

But then I came up against another problem. 

The installer did not give me the option to install alongside Windows, only to replace Windows or "something else". "Something else" did not allow me to take space from my Windows partition (the whole disk) for the Lubuntu installation. I resolved the problem by using a partitioning tool within Windows to create some unallocated space.

Developers, if you read this, this is poor. Ubuntu is making worthy efforts to expand the awareness and use of Linux OS. But if I were the average computer user, with limited technical knowledge or experience, first time trying Linux, I would have thought, "Well, if they can't even get the installation to work properly it's got to be dodgy, I'm not going to be bothered with it."

---

