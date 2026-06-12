---
title: "Backed Into an Installation Corner by Older Hardware"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by dyers2 on 2013-08-08
I have an older computer, a Toshiba Satellite A105 that looks like,

* OS Version: Microsoft Windows XP Home Edition, Service Pack 3, 32 bit
* Processor: Intel(R) Celeron(R) M processor 1.70GHz, x86 Family 6 Model 13 Stepping 8
* RAM: 894 Mb
* Graphics Card: ATI RADEON XPRESS 200M Series, 128 Mb
* Hard Drives: C: Total - 57231 MB, Free - 25130 MB; E: Total - 28003 MB,  Free - 9505 MB; G: Total - 29996 MB, Free - 10867 MB; H: Total - 180464  MB, Free - 12570 MB;
* Motherboard: ATI, SB450
* Antivirus: Microsoft Security Essentials, Updated: Yes, On-Demand Scanner: Enabled

* This CD ROM no longer burns.
* BIOS are set to boot from "external device".
* Drive C: is internal.
* Drives E:, G:, and H: are partitions of a single external.
* My primary machine is down. This Toshiba Satellite had been backup, but has now called into full time service.

Several days ago, anxious to get into Linux, and with the challenges this machine will bring just beginning to dawn, I decided to install using wubi. The more I thought about that, though, the less I liked it. The goal was to replace all existing software with something similar on Linux, delete Windows, expand the Ubuntu partition, and carry on. It seemed to me that the way I installed it was creating unnecessary hassles down the road, and I uninstalled it using the Windows Add & Remove Software utility.

Ran Universal USB 1.9.3.9, and used that to make a bootable flash drive. Even that had a variable about which I don't know what to think. So far as I know, that is the newest version of UUI. I had decided on using Ubuntu Studio v. 13.04, and downloaded it. However, that distro was not among those in UUI. Finally, I decided to select Ubuntu 13.04 Desktop i386 with which I paired the distro I downloaded, and hoped it would work.

Whether that, or my older hardware, I've never seen a glimpse of the contents of my flash drive during boot. It just boots straight into Windows. How might I proceed?

---

### Post by slw210 on 2013-08-08
Is your computer capable of booting from a USB drive?

If it is able to boot from USB drive, is it configured to do so in the BIOS?

---

### Post by Boab1993 on 2013-08-08
Hi dyers,

A definate way to get around this is by installing PLOP:

[http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

Its an alternative boot manager, works very well, and is nice and user friendly.

Also another point is that 13.04 is a bit buggy sometimes when booting for USB, id advise installing an older LTS Ubuntu install such as 12.04, you can then upgrade it via the update manager when youve installed it

Hope this helps

---

### Post by dyers2 on 2013-08-08
> **slw210 said:**
> Is your computer capable of booting from a USB drive?

Yes, good questions. I don't yet know if this machine can boot from a USB flash drive or not. I've tried a couple of different ways to do that, but so far, it misses the USB during boot, and goes straight to Windows.

> If it is able to boot from USB drive, is it configured to do so in the BIOS? 

The BIOS are currently set to try booting from an external device, then the HD.

---

### Post by Mark Phelps on 2013-08-08
Some problems with your approach ...

Regarding installing from inside Windows (using Wubi) -- Wubi has been dropped starting with Ubuntu 13.04.  So, this is no longer an option.  IF you still want to use Wubi, then you need to consider 12.10 or 12.04.

Regarding booting from USB,  some PCs will put up a one-time boot menu when you press F12.  If that works for you, then scroll down through the list of boot devices.  IF you see something like "USD-HDD", select that one -- and the PC will attempt to boot from the USB.

---

### Post by oldfred on 2013-08-08
I have a Toshiba A105 with 1.5GB of RAM and run Ubuntu but fallback or gnome-panel which requires less video & RAM than Unity. Mine was bought the week before Vista came out as I knew already that I wanted XP not Vista.
If less RAM Xubuntu or Lubuntu may be better choices. If I load more than one large or a couple of smaller apps I will see it swap as screen goes gray for a second. But my normal use of Firefox and Zim for text to post here works. But if I also open Thunderbird while Firefox is open I get swapping. So I normally just use one at a time.

Only if flash drive is bootable will my Toshiba boot from it. And If I have two flash drives even if other is not bootable it will not boot flash drive. Have not booted for a while from Flash but I do not change BIOS, but just use f12 (?) as one time boot key.

I do have a Logitech wireless mouse in another USB port and it just works.

---

### Post by dyers2 on 2013-08-09
> **Boab1993 said:**
> Hi dyers,

A definate way to get around this is by installing PLOP: [http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)  Its an alternative boot manager, works very well, and is nice and user friendly.

Great; thanks! I've fiddled with this for a number of hours now, and I had a lot of hope it might help. I first became intimidated by it when I tried to wade through the read-me.text file. I didn't understand a good bit of what I was reading.  :redface:  I never could get it installed.

> Also another point is that 13.04 is a bit buggy sometimes when booting for USB, id advise installing an older LTS Ubuntu install such as 12.04, you can then upgrade it via the update manager when youve installed it

That's very helpful to know, and it might help with another strategy I'm forming. I also found, and had much hope for the Ubuntu 13.04 minimal CD which I was actually able to burn on my machine. So far, I haven't gotten past the network configuration stuff. Will keep trying.

---

### Post by Boab1993 on 2013-08-09
Thanks for the feed back,

PLOP got me stumped for a good while, i was having trouble getting round a bad intsall of windows on a refurbished netbook, but if you know where to look its actually very easy to install.

The file you access is 'plpbt5-'>'Windows'>'InstallToBootMenu.bat'

A command line will appear and do the installation for you, then one restart later and it should be there.
This will allow to access all usb drives connected to you computer and boot from them.

Good luck and report back with any issues!

---

### Post by cub on 2013-08-09
> **oldfred said:**
> If less RAM Xubuntu or Lubuntu may be better choices.
As Ubuntu Studio run Xfce like Xubuntu it should be fine.

---

### Post by dyers2 on 2013-08-09
> **Mark Phelps said:**
> Some problems with your approach ...

Regarding installing from inside Windows (using Wubi) -- Wubi has been dropped starting with Ubuntu 13.04.  So, this is no longer an option.  IF you still want to use Wubi, then you need to consider 12.10 or 12.04.

Hello, Mark; 

I appreciate your time, and thoughts. You told me some things here about which I wasn't aware. It was a different aspect of Wubi with which I wasn't comfortable, and that was my reason for uninstalling the instance of Ubuntu in Windows.

> Regarding booting from USB,  some PCs will put up a one-time boot menu when you press F12.  If that works for you, then scroll down through the list of boot devices.  IF you see something like "USD-HDD", select that one -- and the PC will attempt to boot from the USB.

I didn't know that, either! I expect that will help someone who reads this down the road a bit. I wish it had worked on my machine, though.

---

### Post by dyers2 on 2013-08-09
Thanks, oldfred; this is a lot of useful information.

> **oldfred said:**
> I have a Toshiba A105 with 1.5GB of RAM and run Ubuntu but fallback or gnome-panel which requires less video & RAM than Unity. Mine was bought the week before Vista came out as I knew already that I wanted XP not Vista.
If less RAM Xubuntu or Lubuntu may be better choices. If I load more than one large or a couple of smaller apps I will see it swap as screen goes gray for a second. But my normal use of Firefox and Zim for text to post here works. But if I also open Thunderbird while Firefox is open I get swapping. So I normally just use one at a time.

My initial choice about which Linux distro I'd be using was Lubuntu because I have so little RAM. I thought I'd go to 2GB, the max supported by our machines, and tried Crutial. They don't carry it anymore, so I bought some from a dealer on eBay who confirmed that what he was selling would be compatible with my machine. It wasn't, and I returned it. He sent a different pair of modules which were also incompatible. Someday, I'll find it, but for now, I'll have to deal with 1GB.

My mind changed towards Ubuntu Studio (Xfce, I believe), which is rated a higher resources consumer than Lubuntu, but less than Win XP (which is what I'm using now), and also less than Unity. I am a visual artist, and configurability weighed in my decision. Unity seems the ultimate for customization, and I read also that Lobuntu lacks a lot of that, so it seemed to me that Xfce was a reasonable compromise.

> Only if flash drive is bootable will my Toshiba boot from it. And If I have two flash drives even if other is not bootable it will not boot flash drive. Have not booted for a while from Flash but I do not change BIOS, but just use f12 (?) as one time boot key.  I do have a Logitech wireless mouse in another USB port and it just works.

I hadn't thought about flash drives being bootable before. I usually buy on the cheap, though, so I may well have purchased one that isn't bootable. However, Plop did get Ubuntu loaded through the USB. I have a 250GB drive connected via USB, It's my data / music drive from the machine that's down at the moment. When I tried the BIOS / USB approach to installing Ubuntu, I did think to disconnect that external data drive. But when I was successful, I forgot, and left the external connected.

---

### Post by oldfred on 2013-08-09
This is the f12 boot options screen from my system. And if whatever is plugged into USB port does not have a boot loader in the MBR it is not shown.

---

### Post by dyers2 on 2013-08-09
> **Boab1993 said:**
> Thanks for the feed back,

PLOP got me stumped for a good while, i was having trouble getting round a bad intsall of windows on a refurbished netbook, but if you know where to look its actually very easy to install.

The file you access is 'plpbt5-'>'Windows'>'InstallToBootMenu.bat'

That got me through the first hurdle. With help from you all, I've had success in booting from my flash drive using Plop. It  does a lot, and it's very configurable. It's label for the Ubuntu boot  record needs to be changed, but it correctly labeled the Win XP boot  record. It did install 13.04 from the USB, and I can get into Ubunto  with ease. I just like cleaning up one thing before moving on to the  next. I can't put my finger on it exactly, but it just doesn't look right...even after I figured out that I could replace that illegible novelty font with the one the developer called "normal".  Here's a long page of [documentation]("http://www.plop.at/en/bootmanager/full.html#l_intro") that is packed with information.

> A command line will appear and do the installation for you, then one restart later and it should be there. This will allow to access all usb drives connected to you computer and boot from them.  Good luck and report back with any issues!

Thank you again very much. So much to learn. So many people willing to share. So little time..

---

### Post by dyers2 on 2013-08-09
> **cub said:**
> As Ubuntu Studio run Xfce like Xubuntu it should be fine.

I think so, too. I can't have much software open as things stand now with Win XP, and so little RAM, and I doubt things are gonna get worse, so I anticipate relatively smooth sailing in that area, at least.

---

### Post by dyers2 on 2013-08-09
> **oldfred said:**
> This is the f12 boot options screen from my system. And if whatever is plugged into USB port does not have a boot loader in the MBR it is not shown.

That's very interesting; thanks for going to the bother to make that illustration. I'm wondering if we have the same BIOS? I'm using [COLOR=#003366]_Phoenix Technologies LTD 2.30, 9/30/2008_[/COLOR], and last time I looked, that was the most recent. F12, eh? Very convenient.  Another possible difference: when I edit the boot order, I can only move the HDD up or down. It has an * just to the left of HDD, and the guide tells you it's the only one that moves. Is it like that with yours?

---

### Post by Boab1993 on 2013-08-09
Your quite correct dyers2 and i agree full heartedly, when something doesnt feel right i cant put it down until its fixed.

If your concerned about RAM, check out debian: [http://www.debian.org/](http://www.debian.org/)

Its a very nice small operating system, and a precursor to ubuntu.
It only requires a minimum of 128MB of RAM for a full desktop, its a nice alternative and can install most popular packages.

Im sure we'll here more from you in the future.

---

### Post by oldfred on 2013-08-09
My BIOS at the Boot tab on top looks just like the screen from the f12. And all the setting move with + or - when selected. My BIOS is older than yours, but I am not sure I ever updated it. I regularly had updated my Desktop but only used laptop on trips or vacations.

>     Vendor: Phoenix Technologies LTD
    Version: 2.00   
    Release Date: 08/30/2006


> System Information
    Manufacturer: TOSHIBA
    Product Name: Satellite A105
    Version: PSAA8U-14F02K


Above from my saved bios.txt file.
 sudo dmidecode > bios.txt

---

### Post by cub on 2013-08-10
> **dyers2 said:**
> My initial choice about which Linux distro I'd be using was Lubuntu because I have so little RAM. 
Someday, I'll find it, but for now, I'll have to deal with 1GB.

My mind changed towards Ubuntu Studio (Xfce, I believe), which is rated a higher resources consumer than Lubuntu, but less than Win XP (which is what I'm using now), and also less than Unity. I am a visual artist, and configurability weighed in my decision. Unity seems the ultimate for customization, and I read also that Lobuntu lacks a lot of that, so it seemed to me that Xfce was a reasonable compromise.

I have tried different distributions on my eee pc with 1 GB RAM. I swapped from Lubuntu to Xubuntu since I use Ubuntu Studio on my main laptop. The resources used was not much difference. I then moved to Debian with Xfce for a while, which used less RAM but there was other things that required a bit more tweaking. Now I run Ubuntu Studio 13.04 which use a bit more RAM than Xubuntu and Debian did, but still not enough to mess up with my user experience. I mostly do work in Gimp and Libre Office on it and never run into any trouble. Though it depends on how large projects you work on.

---

