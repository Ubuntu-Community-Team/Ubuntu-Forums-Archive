---
title: "Lubuntu 14.04 Security Updates until 2019?"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-12-23
I believe I read on this Forum that the dreaded i915 Graphics Driver is not compatible with the upgraded Kernel that comes with the updated HWE and also with 15.04 and 15.10. This is probably the reason I experienced Desktop freezes, poor font rendering and horrible graphics when I installed 15.10 or when I tried to install the HWE in 14.04.

Will it still be possible to receive 14.04 default Kernel updates until 2019? Will it only be the LXDE components that will stop receiving Security Updates in 2017? Or will all components stop receiving Security Updates in 2017? If so, is there a way to install the appropriate Security Updates manually?

If the upgraded i915 Driver will not work correctly with the upgraded Kernel, then I do not see a way to upgrade to 16.04 LTS next year and I will have to stick with 14.04 and the default Kernel.

Please advise if possible. Thank you! Happy Holidays!

---

### Post by Bucky Ball on 2015-12-23
LTS releases upgrade directly to the next LTS release, leapfrogging the interims, via a net upgrade, so no need to panic, you're 'unstuck'. :)

As LTS releases are intended for stability, production and server environments, the idea is to avoid downtime. You could stay with LTS releases forever if you want, unless Canonical go changing something.

---

### Post by sudodus on 2015-12-23
In Lubuntu only the program packages, that are used in Ubuntu desktop and Ubuntu Server are supported for 5 years (will receive security updates). All the other program packages, that belong to Lubuntu (not only LXDE) are supported for 'only' 3 years (will not receive any security updates after 3 years). I'm talking about Ubuntu's official support.

There might be upstream support or specific support. Other distros and community re-spins built on Ubuntu's 14.04 LTS repositories promise support for 5 years, for example Bento, Bodhi, Linux Mint, LXLE. If they manage to get security updates for all the program packages used, you are fine. Do you trust them? I think many people do, at least some of these distros and re-spins. Some people only trust Debian and Ubuntu, and if that is the case for you, you should stick to Lubuntu and upgrade to a new LTS version before the old one passes end of life.

---

### Post by deadflowr on 2015-12-23
Having run an Ubuntu 16.04 install with intel's ironlake gpu, I am not sure that the statement that the i915 driver won't work is true.

But then, the driver's function also depends on the card.

Any links to where you read this, please.

---

### Post by roler2 on 2015-12-23
Thank you for the awesome feedback! I have not been able to find the article again on the i915, so maybe it wasn't on this Forum.

I experienced several issues when I attempted to install the 14.04 HWE or upgraded to 15.10 with a fresh install. Major issues with font rendering, really poor graphics, Desktop freezes, etc. I had to cold boot many times. It appears to me it is a Kernel issue and a conflict with the Graphics Driver. That is the only aspect I could think of that was causing all of the issues. Maybe it will work with 16.04. Certainly didn't work at all with 15.10 or the 14.04 HWE. The only Kernel that has worked correctly is the default 14.04. No cold reboots, no desktop freezes, terrific font rendering, good graphics, etc.

---

### Post by Irihapeti on 2015-12-23
I'm using an older Intel chip with the i915 driver on 16.04 successfully.

If you give the specific details of your machine, someone may be able to help you sort out what's happening and, hopefully, come up with a fix.

---

### Post by grahammechanical on 2015-12-24
If you are running Linux kernel 3.13 then it will be supported (security fixes) by the Canonical kernel team until April 2019. And this will apply whatever official flavour of Ubuntu we are using. Check out the graph 14.04 x Ubuntu kernel support.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Why not put in a test install of newer version to see if everything works as it should before upgrading your main installation?

Regards

---

### Post by yoshii on 2015-12-25
freeze ups can sometimes happen from failing or overheating RAM chips.  you may want to check your RAM just to be sure it isn't that.

---

### Post by roler2 on 2015-12-26
Thank you for all of the awesome advice and guidance! I am going to try out a test build of 16.04. I won't install the test build just test it without installing, which is what I should have done with 15.10. I don't think it is the RAM, given I installed 15.10 on the same computer as 14.04, and 14.04 runs great.

If there is poor graphics and font rendering with the test build, even without installing, then I would think it has to be a Kernel issue. Although I do have a very old P4.



Thank you again!

---

### Post by roler2 on 2015-12-31
UPDATE: I did try out a test build of 16.04. The results were exactly the same as the 15.10 install: extremely poor graphics and horrible font rendering (blurry, fuzzy, unfocused and, at times, unreadable and/or unclear). I also ran a test build without installing with the same results. No desktop freezes, however, I didn't do any updates, as that is when 15.10 started to freeze.

So is Lubuntu hopeless for me after 14.04? On 14.04 I have good graphics and terrific font rendering (clear, focused, sharp).

---

### Post by vasa1 on 2015-12-31
> **Irihapeti said:**
> I'm using an older Intel chip with the i915 driver on 16.04 successfully.

If you give the specific details of your machine, someone may be able to help you sort out what's happening and, hopefully, come up with a fix.

^^^

Or at least the output of```
lspci | grep VGA
```or```
grep -i chipset /var/log/Xorg.0.log
```

If you have Firefox, open Help, Troubleshooting and see the section on graphics. Mine looks like this:```
...
Graphics
--------

Adapter Description: Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
Asynchronous Pan/Zoom: none
Device ID: Mesa DRI Mobile Intel® GM45 Express Chipset
Driver Version: 2.1 Mesa 10.1.3
GPU Accelerated Windows: 0/1 Basic (OMTC)
Supports Hardware H264 Decoding: No;
Vendor ID: Intel Open Source Technology Center
WebGL Renderer: Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
windowLayerManagerRemote: true
AzureCanvasBackend: cairo
AzureContentBackend: cairo
AzureFallbackCanvasBackend: none
AzureSkiaAccelerated: 0
CairoUseXRender: 1

...

```

---

### Post by roler2 on 2015-12-31
**lspci | grep VGA**


00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


**grep -i chipset /var/log/Xorg.0.log**


80.622] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
80.622] (II) VESA: driver for VESA chipsets: vesa
80.642] (--) intel(0): Integrated Graphics Chipset: Intel(R) 845G


**Firefox**


VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
Asynchronous Pan/Zoom	none
Device ID	Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
Driver Version	3.0 Mesa 11.2.0-devel (git-65d3f85 2015-12-31 trusty-oibaf-ppa)
GPU Accelerated Windows	1/1 OpenGL (OMTC)
Supports Hardware H264 Decoding	No;
Vendor ID	VMware, Inc.
WebGL Renderer	VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
windowLayerManagerRemote	true
AzureCanvasBackend	cairo
AzureContentBackend	cairo
AzureFallbackCanvasBackend	none
AzureSkiaAccelerated	0
CairoUseXRender	1


**cat /var/log/Xorg.0.log | grep -i sna **


80.623] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git1512151933.822939~gd~t (Oibaf <fmrummey@gmail.com>)
80.623] (II) intel(0): SNA compiled for use with valgrind
80.642] (**) intel(0): Option "AccelMethod" "SNA"
80.645] (II) intel(0): SNA initialized with Almador (gen2) backend


**lshw -c video**


description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff


Works very well with Lubuntu 13.10 and 14.04 with default kernel only. Upgrade HWE or to 15.04 or 15.10 or 16.04 all same issues with very poor graphics, horrid font rendering (unclear, blurry, etc.) and then experienced desktop freezing after updates were applied to a point where the only resolution to terminate freeze was a cold reboot, where it would promptly re-freeze again after booting to desktop (also no mouse, no keyboard upon boot to desktop).

---

### Post by vasa1 on 2016-01-01
> **roler2 said:**
> ...
VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
...
Device ID	Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
...
WebGL Renderer	VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
...

I don't know anything about hardware but isn't the whole "llvmpipe" business something brought in by Unity to "emulate" stuff? I didn't know Lubuntu comes with llvmpipe by default.

Are your installs pure Lubuntu?

---

### Post by sudodus on 2016-01-01
The Trusty kernel, that comes with Lubuntu 14.04.1 LTS can be updated and upgraded until April 2019, but the program packages, that are specific for Lubuntu are only supported until April 2017 (so a little more than one year from now). If you avoid upgrading HWE (and get new kernel series), I think and hope that your graphics will continue to work also with upgraded kernels within the Trusty kernel series.

There are community re-spins based on Ubuntu 14.04 LTS, that promise support until April 2019, for example ***Bento*** and ***LXLE***.

If still problems, you might have better luck with a distro for old hardware, ***Wary Puppy*** or ***TahrPup***.

-o-

Have you tried UXA acceleration according to the following link: [Old Intel graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

See also this link: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by sudodus on 2016-01-01
> **vasa1 said:**
> I don't know anything about hardware but isn't the whole "llvmpipe" business something brought in by Unity to "emulate" stuff? I didn't know Lubuntu comes with llvmpipe by default.

Are your installs pure Lubuntu?

+1

I thought so too about llvmpipe.

Maybe you should try with a clean Lubuntu system (booted from a live DVD or USB drive).

---

### Post by roler2 on 2016-01-01
**Are your installs pure Lubuntu?**


I have only installed Lubuntu 13.10 and 14.04 and 15.10. I tried Lubuntu 16.04 without installing. 13.10 worked well with i915 Driver. 14.04 works well with i915 Driver with default kernel only. Once I upgraded HWE, many issues.


**I think and hope that your graphics will continue to work also with upgraded kernels within the Trusty kernel series.**


Graphics does not that is the issue I am having. Upgrading 14.04 HWE or install of 15.10 or an attempt to try 16.04 without installing all produced both extremely poor graphics and font rendering.


**Maybe you should try with a clean Lubuntu system (booted from a live DVD or USB drive). **


I did with Lubuntu 13.10, 14.04, 15.10. Video did not work correctly with 15.10 installed or 16.04 (without installation). Video worked correctly with 13.10 and 14.04 (default kernel only).


The desktop freezes started only after I upgraded HWE on 14.04 or applied security updates with 15.10. With 16.04, the graphics and font rendering were so awful in a non-installation mode that there was no point to attempt an install.


**Have you tried UXA acceleration.**


No because SNA worked with 14.04 default kernel and with 13.10. So I thought it should work just as good with the upgraded kernel, that is, if I can get the graphics to work correctly.


**I thought so too about llvmpipe.**


What I will do is obtain the same graphics driver information with 16.04 (without installation) and post, including the Firefox info.




Thank you so much for all of your help.

---

### Post by sudodus on 2016-01-01
> **roler2 said:**
> ...

**I think and hope that your graphics will continue to work also with upgraded kernels within the Trusty kernel series.**


Graphics does not that is the issue I am having. Upgrading 14.04 HWE or install of 15.10 or an attempt to try 16.04 without installing all produced both extremely poor graphics and font rendering.

...

If you start with Lubuntu 14.04.1 LTS and 'only' run

```
sudo apt-get update && sudo apt-get dist-upgrade
```

you will ***not*** upgrade the HWE stack, so you will keep the Trusty kernel (security updates, but still the 3.13 'Trusty' series). Try that, I think it will work with the graphics.

If you upgrade the HWE stack you will get the Vivid or Wily kernel which you don't want.

---

### Post by roler2 on 2016-01-01
The problem is that when 16.04 is released then I am stuck with the upgraded kernel, which is what I don't want either based upon the upgraded kernel not working with 15.10 installed nor with 16.04 without installation. One of the Forum members apparently has been able to utilize the i915 driver with 16.04. I have not. So I am not sure why the i915 driver works with 16.04 for that specific Forum member, but for my very old Dell Dimension 2400, it does not. Kernel Security updates for the 3.13 series work just fine, as did the Kernel Security updates for 13.10.

---

### Post by sudodus on 2016-01-01
There are community re-spins based on Ubuntu 14.04 LTS, that promise support until April 2019, for example Bento and LXLE. This means that you should be able to use the Trusty kernel until April 2019, more than 3 years to go :-)

***Why suggest Bento and LXLE?***

1. Lubuntu is fine, but promises support only until April 2017.

2. Bento and LXLE have light desktop environments, similar to Lubuntu, and promise support until April 2019. (Kubuntu and Standard Ubuntu with Unity also promise support until April 2019, but need a more powerful computer to work well.)

-o-

If still problems, you might have better luck with a distro for old hardware, ***Wary Puppy*** or ***TahrPup***.

-o-

Just for reference, I can tell you about the computer of my mother in law.

I bought a computer with Windows XP 8 years ago to her. Just before XP passed end of life, I installed Lubuntu, and she learned how to use it. A few days before Christmas the computer died. I did some tests, but it was obvious that there was some serious problem, I think with the motherboard or some other hardware that is not easy or cheap to replace. So I bought a second-hand refurbished computer with Windows 7 to her. It was cheaper than replacing the motherboard or CPU. Now she has a more powerful computer, and I could port her previous Lubuntu system via the ***One Button Installer*** (made a tarball with xmktbl) and copy the data partition to the new computer.

So now she has the same system as before in the new computer - no learning curve, and in due time she can learn Windows 7, which might help her use all the features of her new multi-function printer-scanner-fax. I have already tested Lubuntu Xenial Xerus in her new computer, and it works very well, so I think it will be easy to upgrade to 16.04.1 LTS, when it is released.

---

### Post by roler2 on 2016-01-01
OK I am really confused now. Are you saying my computer is bad? If it was bad then I would not be able to run 14.04.

Once again, my computer works great with 14.04 with the default kernel. The graphics, font rendering do not work well if I upgrade the kernel or install 15.10 or if I try 16.04 without installing.

So why should I get another computer? Obviously it appears to be a kernel issue, at least with my computer. So you and another Forum Member have had success with 16.04 with the i915 driver. I have not and that is why I posted. I gave out the Graphic Card specs per this thread. One of the Forum Members was concerned about some sort of emulation. Yet it works fine with 14.04.

So, once again, if the Graphics work fine with 14.04, why won't it work with 15.10 or 16.04 or when upgrading the HWE? I am sure other Forum Members have i915 Graphics. So am I the only one with i915 Graphics issues when utilizing an upgraded kernel?

---

### Post by Irihapeti on 2016-01-01
> **roler2 said:**
> The problem is that when 16.04 is released then I am stuck with the upgraded kernel, which is what I don't want either based upon the upgraded kernel not working with 15.10 installed nor with 16.04 without installation. One of the Forum members apparently has been able to utilize the i915 driver with 16.04. I have not. So I am not sure why the i915 driver works with 16.04 for that specific Forum member, but for my very old Dell Dimension 2400, it does not. Kernel Security updates for the 3.13 series work just fine, as did the Kernel Security updates for 13.10.

I'll assume that you're referring to my earlier post.

Now that I've seen your hardware specs, I see that your graphics chip is quite different from mine. I suspect that it's older.

Unfortunately, there comes a time when the older hardware no longer works with newer software. Then you have the choice of either getting a new machine (or upgrading components if that's possible) or sticking with older software versions for as long as you can.

However, it's still possible that someone may come up with a way of getting your graphics chip to work with the later kernel versions.

---

### Post by sudodus on 2016-01-02
> **roler2 said:**
> OK I am really confused now. Are you saying my computer is bad? If it was bad then I would not be able to run 14.04.

Once again, my computer works great with 14.04 with the default kernel. The graphics, font rendering do not work well if I upgrade the kernel or install 15.10 or if I try 16.04 without installing.

So why should I get another computer? Obviously it appears to be a kernel issue, at least with my computer. So you and another Forum Member have had success with 16.04 with the i915 driver. I have not and that is why I posted. I gave out the Graphic Card specs per this thread. One of the Forum Members was concerned about some sort of emulation. Yet it works fine with 14.04.

So, once again, if the Graphics work fine with 14.04, why won't it work with 15.10 or 16.04 or when upgrading the HWE? I am sure other Forum Members have i915 Graphics. So am I the only one with i915 Graphics issues when utilizing an upgraded kernel?

I'm sorry. I did not mean that your computer is bad. I have old computers too, and I help several people with old computers, and I really want that old computers can be used with Ubuntu and other linux distros as long as possible.

I only tried to say that sometimes new linux kernels and their drivers do not match all older hardware, and your computer seems to be affected by that problem (according to what I understand from what you have written earlier in this thread). I think your computer will to get along with the Trusty kernel (3.13 series) for another 3 years, because there are some community re-spins that promise support until the end of life of Ubuntu 14.04 LTS and they have light-weight desktop environments similar to Lubuntu.

When the new linux kernels and their drivers are developed to match new hardware, the support for some old hardware might be dropped. This happens, and it is something that I cannot change. People active at the Ubuntu Forums are not the same as the developers of linux in general, not even Ubuntu. Most developers never visit the Ubuntu Forums, so if you are unhappy with the development of the linux kernel software, yes, you can complain here, but we cannot do anything about it, except maybe suggest some work-arounds.

The standard way to communicate with the developers is to file a bug report at Launchpad, and if you want a more direct dialogue, to use one of the Ubuntu or linux IRC channels.

---

### Post by Bucky Ball on 2016-01-02
You could try [a minimal approach]("https://help.ubuntu.com/community/Installation/MinimalCD") and add things until it breaks. 

Install the Ubuntu kernel (a minimal install), don't choose a machine profile, once installed and rebooted you'll end up at a login screen. Login and:

```
sudo apt-get install lxde
```

Reboot. That will give you the Ubuntu kernel, the lxde desktop environment used by Lubuntu, and that's it. Now 'sudo apt-get install' or install Synaptics and use that to install other things until it breaks ... or doesn't. 

Just a suggestion. No idea of its chances of success. Good luck. ;)

---

### Post by tokyobadger on 2016-01-02
[quote="roler2"]**Firefox**


**VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)**
Asynchronous Pan/Zoom    none
Device ID    Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
Driver Version    3.0 Mesa 11.2.0-devel (git-65d3f85 2015-12-31 trusty-oibaf-ppa)
GPU Accelerated Windows    1/1 OpenGL (OMTC)
Supports Hardware H264 Decoding    No;
**Vendor ID    VMware, Inc.**
**WebGL Renderer    VMware, Inc. -- Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)**
windowLayerManagerRemote    true
AzureCanvasBackend    cairo
AzureContentBackend    cairo
AzureFallbackCanvasBackend    none
AzureSkiaAccelerated    0
CairoUseXRender    1[/quote]
So this is a virtual installation not a "bare metal" installation?
What's the host OS? 
VMWarePlayer version 12 supports Ubuntu 15.04 - playing with 15.10 or 16.04 is not going to work as well / at all until VMWare issue a version with updated support

---

### Post by roler2 on 2016-01-02
Thanks to all of you again for all of your awesome feedback! I really very much appreciate your time and diligent efforts!

So. . .when 16.04 is released, will I be able to install the default 3.13 Kernel series, rather than utilize the upgraded Kernel that will be released with 16.04, and then utilize the 3.13 Kernel with the respective security updates until 2019?

If so how do I do that and not get updates for the 16.04 Kernel? Is there a way to uninstall the 16.04 Kernel and not receive updates for that specific Kernel, rather, receive updates for the 3.13 Kernel?

Maybe that would resolve the Graphics issues, well, at least for my old P4 and the i915.

---

### Post by sudodus on 2016-01-02
It is possible to use an older kernel. When 16.04 is released, or should I say a couple of months after it is released, and the worst bugs are squashed, you can try it ***live***, and if necessary the detailed instructions how to install and lock the system to only use (and upgrade within) the 3.13 kernel series. But I am not sure that it will be better than to stay with 14.04 LTS.

My only reason to upgrade the main operation system to 16.04 LTS would be to get new versions of program packages, where the versions in 14.04 LTS do not work well or are missing some important feature. If your current system works well with 14.04 LTS, and its program packages do what you need, why bother to change what is working?

An alternative is to make a dual boot or multi boot system, and try an installed system with 16.04 LTS, to find a kernel with drivers that work, and to make all the other software work with it. This can be an interesting journey. Maybe the road will be smooth, maybe bumpy, if bumpy you will learn a lot of interesting things :-)

---

### Post by deadflowr on 2016-01-02
> **tokyobadger said:**
> So this is a virtual installation not a "bare metal" installation?
What's the host OS? 
VMWarePlayer version 12 supports Ubuntu 15.04 - playing with 15.10 or 16.04 is not going to work as well / at all until VMWare issue a version with updated support

No, it's bare metal. 
It show the Op is using the oibaf ppa, which you cannot use in a standard vm.
Also note that vmware is the maker/developer of llvmpipe, afaik.

That said, is there a reason to use the oibaf ppa, as the 845g card is really old?
And for how long have you been running that ppa for?

---

### Post by roler2 on 2016-01-02
** . . .the detailed instructions how to install and lock the system to only use (and upgrade within) the 3.13 kernel series**


How do I accomplish that? 
 
**And for how long have you been running that [oibaf ppa] for?** 

Since Lubuntu 13.10. I did not utilize the ppa when I installed 15.10. I didn't utilize any ppa's after installing 15.10. The graphics and font rendering did not work correctly from the get-go. Desktop freezes started after security updates. I neither installed nor uninstalled any programs. I installed 15.10, went right to installing security updates, rebooted, desktop freeze, no mouse, no keyboard. Cold reboot, same issues again when booted to desktop.

---

### Post by deadflowr on 2016-01-02
> **roler2 said:**
> ** . . .the detailed instructions how to install and lock the system to only use (and upgrade within) the 3.13 kernel series**


How do I accomplish that? 


Install from 14.04(or 14.04.1) from here
[http://old-releases.ubuntu.com/releases/14.04.2/](http://old-releases.ubuntu.com/releases/14.04.2/)

It, by default, will not upgrade the kernel series or graphics stack in use for the duration of the release.
(You'll get kernel updates but only for the 3.13 series, no kernel upgrades to any others, like 3.19 or newer.)
if that makes sense.

---

### Post by roler2 on 2016-01-02
Oh so sorry I don't think I phrased the question correctly:

[FONT=arial black]When 16.04 is released. . .the detailed instructions how to install and lock the system to only use (and upgrade within) the 3.13 kernel series[/FONT]

In April when 16.04 is released, I want to both install and utilize the 3.13 Kernel as the default kernel in 16.04 so as to receive security updates for the 3.13 Kernel until 2019.

---

### Post by Irihapeti on 2016-01-03
> **roler2 said:**
> Oh so sorry I don't think I phrased the question correctly:

[FONT=arial black]When 16.04 is released. . .the detailed instructions how to install and lock the system to only use (and upgrade within) the 3.13 kernel series[/FONT]

In April when 16.04 is released, I want to both install and utilize the 3.13 Kernel as the default kernel in 16.04 so as to receive security updates for the 3.13 Kernel until 2019.

Unfortunately, I don't think that's possible. :(

Have you  tried booting a liveDVD of a later version using nomodeset? When you get to the "Try Ubuntu", "Install Ubuntu" etc screen, press F6 in the boot menu. Nomodeset is near the bottom of the list. That bypasses the i915 driver which appears to be causing the problems and loads a very basic one. It's worth at least trying.

---

### Post by kurt18947 on 2016-01-03
Good thought about nomodeset. Is this a desktop machine or laptop? If a desktop would it be practical to install an inexpensive/used video card to do an 'end run' around the problematic graphics chipset?

---

### Post by roler2 on 2016-01-04
I did try the nomodeset with 16.04. It didn't load any driver at all. Looked similar when Windows is unable to find a video card and in 640x480 mode. I suppose when 16.04 is released I could try an install with nomodeset, however I am still going to eventually have to install a driver of some sort. 

Good suggestion, yet eventually I am going to have to deal with the i915 graphics issues, which appear to be the central problem especially with an upgraded kernel. I remember one of the Forum Members was successful with 16.04 and the i915 driver. So far I have not been as successful. The upgraded kernel must not fully support the i915 Graphics or maybe just not fully support the i915 that is installed with my old P4.

---

### Post by sudodus on 2016-01-04
Q 1. Do you ***need*** a version newer than 14.04 LTS? In that case why?

Q 2. Or do you simply ***want*** to get the latest and greatest, and you enjoy tweaking your system?

Both reasons are good, but very different.

A 1. If you need to fix some application that does not work, let us focus on that problem.

A 2. Otherwise:

At one extreme, you should stay with what works (and can be expected to work for years). At the other extreme you can participate in testing during the development of Xenial Xerus, to be released as 16.04 LTS in April. But in the latter case you should have two systems, one stable system 'a work-horse for production' and one experimental system. And you can participate in

isotesting at [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

and exchange of ideas at the subforum [Ubuntu Development Version](http://ubuntuforums.org/forumdisplay.php?f=427)

Somewhere in the middle there is the alternative to wait until a couple of months after 16.04 LTS is released, and at that time start trying to make it work in your computer. This is much easier than to do it now (when the development of  Xenial Xerus is at the 'alpha 1' stage).

---

### Post by roler2 on 2016-01-04
If I could stick with Lubuntu 14.04 until 2019 I would, but I can't because security updates stop in 2017, I think July. So I will wait until 2017 to update to 16.04, hopefully by that time there will be a fix for the i915 Driver applicable to the kernel updates. 

If Lubuntu is designed to work with older computers, many of those computers will have old/outdated Graphics Cards. So if the updated kernels are not designed to work with older graphics, then, to me, that is defeating the purpose of Lubuntu as a whole. So Lubuntu should consider an option to stick with a kernel that works, such as the 3.13 series, for those who have very old graphics cards. When 16.04 is released, and the kernel isn't being friendly to old graphic cards, then a lot of other Lubuntu users are going to be having the same issue(s). Just reading some of the Forum posts about 15.10 makes me wonder if a majority of the issues with installation, updating, poor performance, unable to boot correctly, etc. that other Forum Members are experiencing aren't somehow related to graphics poorly interacting with the updated kernel and vice-versa.

---

### Post by vasa1 on 2016-01-04
> **roler2 said:**
> ...

If Lubuntu is designed to work with older computers, many of those computers will have old/outdated Graphics Cards. So if the updated kernels are not designed to work with older graphics, then, to me, that is defeating the purpose of Lubuntu as a whole. So Lubuntu should consider an option to stick with a kernel that works, such as the 3.13 series, for those who have very old graphics cards. When 16.04 is released, and the kernel isn't being friendly to old graphic cards, then a lot of other Lubuntu users are going to be having the same issue(s). ...

Your point is totally valid but I wonder if it's allowed or possible for an "official" flavor to implement what you suggest. Plus 16.04 is already [in its alpha stage]("https://wiki.ubuntu.com/XenialXerus/Alpha1/Lubuntu").

You may get some more views on your issue by signing up and posting on the [Lubuntu users mailing list]("https://lists.ubuntu.com/mailman/listinfo/lubuntu-users").

Sudodus has mentioned some other distros but I didn't check what their policies are with respect to providing older kernels.

---

### Post by sudodus on 2016-01-05
The main developer of Lubuntu has decided to maintain the LTS versions for 3 years. I don't think we are able to convince him to maintain the Lubuntu specific software for two more years.

If you want to extend the Lubuntu LTS experience beyond 3 years, there is [http://www.lxle.net/](http://www.lxle.net/), which promises 5 years LTS, so LXLE 14.04 will be supported until April 2019. (Do not confuse it with the desktop environment LXDE.)

Try it live - and if you like it, install it :-)

The LXLE 14.04.3 version comes with the Trusty kernel 3.13, which works for you, so if you only update && dist-upgrade, but avoid upgrading the HWE stack, it should keep working for you.

[COLOR="#696969"](This is different from Lubuntu 14.04.3, which comes with the Wily kernel. To get the Lubuntu Trusty kernel, you should download version 14.04.1 LTS)[/COLOR]

---

### Post by mörgæs on 2016-01-05
Searching for old software should be seen as a last resort. Configuring new software to run on old hardware is the preferred approach.

People have advised you to try UXA in stead of SNA, and you have still not tried it 'just because'. I think it's about time you follow the advice rather than demand that 16.04 will be able to run this or that kernel.

I also like to make old hardware useable again but the 845 is ancient. One must expect to do some configuration to make it work.

---

### Post by Bucky Ball on 2016-01-05
> **mörgæs said:**
> I also like to make old hardware useable again but the 845 is ancient. One must expect to do some configuration to make it work.

Isn't that part of the fun? ;)

---

### Post by roler2 on 2016-01-05
I currently have 14.04 installed. When 16.04 is released then I will try UXA right after installation and before applying anything else, such as security updates. Subsequent to the 15.10 install, I immediately applied the security updates, rebooted, and got a desktop freeze, and the only way to terminate the desktop freeze was a cold reboot because the mouse and keyboard stopped working.


Also, I haven't demanded that 16.04 run this or that kernel. I have asked if it is possible to install the 3.13 series kernel as the default with 16.04. The answer that has been posted is apparently no.


Yes the 845 is ancient. So are Pentium 4's.

---

