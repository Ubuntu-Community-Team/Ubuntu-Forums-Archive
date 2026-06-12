---
title: "Help with ATI Driver requirements"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Scarred Warble on 2010-07-05
Hello!

[QUOTE=You don't really need to read this]I'm new to Ubuntu and I need a little help, you see I have a ATI graphics card and a widscreen monitor. To be able to see anything I have to use the built-in VESA driver, which stretches the picture from 4:3 to 16:9, which is very annoying.

The version I am trying this on is Ubuntu 9.10.

I have downloaded and installed the Driver I need from [ATI website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") (<-clickable) but on reboot the screen goes black/blank with the occasional flash of text once every (approximately) 20 seconds. The text does not change (had it on for several hours).

When installing I've tried just opening it, it installed but the logs said there was an error. On reboot I got the blank screen after the Ubuntu logo with the flash of text once in a while. I can not access the thingy that you get to by pressing F6 (I barley know what I'm talking about).

I've also tried using these commands to install:
*[I]sudo chmod* +*x ati*-*driver*-*installer*-10-6-x86.x86_64.run 
sudo sh *ati*-*driver*-*installer*-10-6-x86.x86_64.run 
aticonfig --initial -f[/I]

With the same result.
[/QUOTE]


So I go online and start looking for some more instructions and you know what, ATI had very precise instructions the whole time. 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf)

There is only one catch, they say on page two and three that some things are required, to be more precise:

• POSIX Shared Memory (/dev/shm) support is required for 3D apps
• glibc version 2.2 or 2.3
• Linux kernel 2.6 or higher
• XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
• XFree86-Mesa-libGL
• libstdc++
• libgcc
• XFree86-libs
• fontconfig
• freetype
• zlib
• gcc

I'm using Ubuntu 9.10.
[B]
How do I know if I have them and how do I get those I don't have?[/B]

Thank you!

---

### Post by Mark Phelps on 2010-07-06
What's the make/model of your card? The ATI drivers only work with the newer HD 3x/4x/5x series cards.  

IF you have an older series card, nothing you do will get the drivers working.

---

### Post by cascade9 on 2010-07-06
> **Mark Phelps said:**
> What's the make/model of your card? The ATI drivers only work with the newer HD 3x/4x/5x series cards.  

HD 2XXX works as well.  Older cards though, the only choice you have is the open source ATI drivers.

---

### Post by Scarred Warble on 2010-07-06
Thank you for the quick replies.
 
I have HD 3650 but as I said I have the right drivers, I just can't install them in a way that makes them function.

---

### Post by WinRiddance on 2010-07-06
In the past 15 months or so I've encountered so many horrible problems with ATI cards and Ubuntu that I stopped trying to get things to work correctly anymore. Some of the issues would take in excess of 20 hours time to resolve ... some issues could not be resolved at all even though ATI claimed to have resolutions in newer driver releases, and so on. I've seen ATI driver issues where drivers had to be installed - removed - reinstalled numerous times over the course of several months without a final working resolution.

Finally I've just gotten in the habit to install Ubuntu and hope for the best. Once installed I use the HARDWARE DRIVERS option under ----> SYSTEM ----> ADMINISTRATION to look for better drivers. If I can't find any there I go ahead and either use the system as is, or I replace the graphic card with another non ATI card instead.

**I know that may sound ridiculous** but I've been a "die-hard" ATI user for many years, installed their products on literally hundreds of computers that I've personally built, but these Ubuntu/ATI problems are just far too time consuming for me. I have better things to do with my time, other than fighting endless hours to make something work that should be working to begin with ... just like other products from other graphic chip vendors work on Ubuntu. Don't get me wrong, nothing is perfect and you should always expect some problems during OS installations so you don't get too surprised or frustrated later on, but only ATI was capable of bringing me to my knees with their funky drivers and Ubuntu incompatibility issues. If your ATI card doesn't work out of the box or with the Ubuntu Hardware Drivers option, there's a good chance that there are many frustrating hours ahead for you .... **think about that** ....

---

