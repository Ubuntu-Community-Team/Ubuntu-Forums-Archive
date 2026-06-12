---
title: "GPU is fried - how to install ubuntu"
date: 2017-07-26
forum: MINT
---

### Post by hands-down on 2017-07-26
Hello,

The GPU in my Laptop stopped working a couple of days ago and I have no hope of getting it back. The silver lining is my Intel HD Grafics. Currently I use a dual boot with Mint and Windows10 automatically deactivates the GPU and works with the Intel HD which is fine for desktop only usage. 

Now the question: Why can't I get that to work under Linux?

What I tried: Dropped to root shell and edited the /etc/default/grub to have 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modset=0" 
and 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodset"
in there. 
Both didn't work. It get's me to the login in screen and freezes there or freezes during the login process. Is there any other way to disable the gpu? 

I wouldn't mind installing Ubuntu completely clean, but the ubuntu boot disk froze before I could do anything (elementaryOS as well). This is the error messages I get at the start. 

[http://imgur.com/a/dVm9P](http://imgur.com/a/dVm9P)

Any help is appreciated,

Thanks in advance!

---

### Post by ubfan1 on 2017-07-26
I don't know much about radeons, but you probably have an open source driver for it that you have to blacklist too, so you force a fallback to a vesa or framebuffer video.  With Nvidia, that would be the nouveau driver to suppress, but for radeon ???

---

### Post by hands-down on 2017-07-26
> **ubfan1 said:**
> I don't know much about radeons, but you probably have an open source driver for it that you have to blacklist too, so you force a fallback to a vesa or framebuffer video.  With Nvidia, that would be the nouveau driver to suppress, but for radeon ???
I think I even forced the proprietary radeon driver upon the system. But that was half a year ago so I am not quite sure what the f I did. My first choice would be to install a clean new system but no one seems to be able to tell me how I am supposed to do that.

---

### Post by QIII on 2017-07-26
Hello!

If you are sure that the AMD GPU is inoperative, I suggest you attempt to disable it in your BIOS/UEFI menu so that the machine will default to the Intel graphics on startup.

Let us know if that works.

Cheers!

---

### Post by BenginM on 2017-07-26
Hiya, which AMD Radeon GPU is it ...
lspci -k | grep -A3 VGA

should tell .. and

dmesg , run sudo cat /var/log/dmesg | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us) 

and paste the result link so we look at the logs ..


and what happens when KMS is enabled and the kernel boots without nomodeset & radeon.modset=0 ..!

---

### Post by BenginM on 2017-07-26
unfan1 , The radeon driver is the free driver for AMD .

---

### Post by deadflowr on 2017-07-26
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modset=0" 
Is that a typo on the forums or was that how you actually input it?
Should be modeset not modset

But +1 to what QIII suggests and go into your BIOS to see about disabling the amd card and try running from the intel card.

---

### Post by hands-down on 2017-07-27
Thanks for all the input. I unfortunately only now had the time to try all that stuff you suggested.

> **QIII said:**
> Hello!

If you are sure that the AMD GPU is inoperative, I suggest you attempt to disable it in your BIOS/UEFI menu so that the machine will default to the Intel graphics on startup.

Let us know if that works.

Cheers!

Unfortunately my BIOS doesn't contain such an option. 

> **BenginM said:**
> Hiya, which AMD Radeon GPU is it ...
lspci -k | grep -A3 VGA

should tell .. and

dmesg , run sudo cat /var/log/dmesg | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us) 

and paste the result link so we look at the logs ..


and what happens when KMS is enabled and the kernel boots without nomodeset & radeon.modset=0 ..!
It is the AMD Radeon HD 7670M

The problem about the logs is that I can only go into recovery mode and drop to root shell from there. When I am in there I neither have an internet connection nor do the log files contain anything. And I have no idea how to boot into a non-gui version of Mint. I tried it with this line in the grub file but it froze during boot as well. 
```
[COLOR=#000000]*GRUB_CMDLINE_LINUX_DEFAULT="text"*[/COLOR]
```

When I have KMS is enabled the boot freezes at the bootscreen. When I have radeon.modset=0 it freezes at the login screen or during login. I never came closer to an actual running operating system. Like I said I would gladly wipe the Mint for something else but I have no idea how to run an installer with this broken GPU. 

> **deadflowr said:**
> Is that a typo on the forums or was that how you actually input it?
Should be modeset not modset

But +1 to what QIII suggests and go into your BIOS to see about disabling the amd card and try running from the intel card.
I actually saw this yesterday, too. But even without the typo it won't let me boot into Mint.

---

### Post by ubfan1 on 2017-07-27
Take a look at the /etc/X11/xorg.conf file, and you should find two (or more) "Device" sections, like the below example:
Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection

copy the xorg.conf file so you can reset it later, and try removing the non-intel "Device" sections for the radeon.  Then try rebooting or just restarting the X server.  Other things to try on the "Driver" line in the Intel device section instead of "modesetting" are "vesa", and "fbdev"

---

### Post by QIII on 2017-07-27
*Moved to **MINT***

---

