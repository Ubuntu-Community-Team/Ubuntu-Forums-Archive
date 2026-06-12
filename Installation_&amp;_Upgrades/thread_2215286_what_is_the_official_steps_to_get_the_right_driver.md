---
title: "what is the official steps to get the right driver?"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by ambt on 2014-04-05
Hi guys, 

I work in a small company and we have a goal that is changing all the company to Ubuntu 12.04 LTS. 

I face driver problems usually and honestly and just wait till Ubuntu finish updating and then I close the computer because I have no I idea how to figure out what is the missing driver? and how can I get this driver worked in Ubuntu? 

I read many article in my first and second language and still didn't find the OFFICIAL guide to ( How you figure out what driver is missing after installing Ubuntu? ) and ( What are the steps or instructions to get the right driver and install it? ) 

Many of my workmate say "finding a driver for Linux is a luck, because there is no specific steps or instructions to get that done easily like in Microsoft OS" 

Is that right guys? if it was wrong, don't blame me because 95 % of people in my country have no idea what is Linux or how to use this thing? :)


Thanks guys,

---

### Post by Mark Phelps on 2014-04-06
What makes you think a driver is missing?  If some piece of hardware is not working, that is a strong indication -- but you said nothing about anything not working.

The "right" drivers are found by the installer during initial setup; unlike with Windows, you don't start searching around for drivers.

> Is that right guys?Basically -- YES.  A known exception is the offering of proprietary drivers but those are limited to video and networking. In other cases, if the hardware vendor doesn't offer Linux drivers, it's most likely the hardware is not going to work.

MOST people don't know what Linux is, so that doesn't make your situation unique.

---

### Post by carl4926 on 2014-04-06
> **ambt said:**
> Hi guys, 

I work in a small company and we have a goal that is changing all the company to Ubuntu 12.04 LTS. 

I face driver problems usually and honestly and just wait till Ubuntu finish updating and then I close the computer because I have no I idea how to figure out what is the missing driver? and how can I get this driver worked in Ubuntu? 

I read many article in my first and second language and still didn't find the OFFICIAL guide to ( How you figure out what driver is missing after installing Ubuntu? ) and ( What are the steps or instructions to get the right driver and install it? ) 

Many of my workmate say "finding a driver for Linux is a luck, because there is no specific steps or instructions to get that done easily like in Microsoft OS" 

Is that right guys? if it was wrong, don't blame me because 95 % of people in my country have no idea what is Linux or how to use this thing? :)


Thanks guys,

Your first question in the forum is not very informative. You need to be more specific as to you particualr problem. At the moment it sounds more imagined than real.

If you plan to move a company to Linux use. I'd suggest you need at least one person to administer the process who is fully conversant with Linux.

---

### Post by SeijiSensei on 2014-04-06
"Drivers" in Linux usually mean "kernel modules."  Except for the proprietary ones Mark mentioned, the rest of the drivers come bundled with the kernel.  Take a look in /lib/modules.  You'll see one, and likely more than one, directory with a name like 3.13.0-18-generic that contains the modules for particular kernel build.  To see the one in use, enter the command "uname -r" at a terminal prompt.

Most standard PC hardware works just fine with most modern Linux distributions.  Problems can arise with some devices like printers and scanners, but you can search online to see which manufacturers and models are well-supported in Linux.  Wifi and video adapters can be problematic because the manufacturers want to preserve trade secrets.  In those cases the manufacturers, like ATI and NVIDIA, provide proprietary binary drivers that you can install from within Ubuntu itself. Wired Ethernet almost always works without any additional fuss.

What particular pieces of hardware are giving you problems?

Now I have two other pieces of advice.  The first is to wait a few weeks until the most recent Ubuntu version with "long-term support," 14.04, comes out.  While 12.04 will be supported for a few more years, you might as well go with the most recent LTS version which will be released before the end of the month.

In the meantime, take one system and install the [current 14.04 beta]("http://cdimage.ubuntu.com/releases/14.04/beta-2/") on it.  Depending on the age and power of your hardware, you might want to choose an Ubuntu flavor with a  less-demanding desktop environment like [Lubuntu]("http://cdimage.ubuntu.com/lubuntu/releases/14.04/beta-2/") or [Xubuntu]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/beta-2/").  On decently powerful hardware you might want to give [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/14.04/beta-2/") a look as well. Build the system you would expect your office mates to use and try it out on your most computer-savvy staff.  

You might also want to browse some of the threads here on using Linux in business settings like:
[http://ubuntuforums.org/showthread.php?t=2130015](http://ubuntuforums.org/showthread.php?t=2130015)
[http://ubuntuforums.org/showthread.php?t=2186212](http://ubuntuforums.org/showthread.php?t=2186212)
[http://ubuntuforums.org/showthread.php?t=2157348](http://ubuntuforums.org/showthread.php?t=2157348)
[http://ubuntuforums.org/showthread.php?t=2118323](http://ubuntuforums.org/showthread.php?t=2118323)

---

### Post by ambt on 2014-04-06
> **Mark Phelps said:**
> What makes you think a driver is missing? If some piece of hardware is not working, that is a strong indication -- but you said nothing about anything not working.

The "right" drivers are found by the installer during initial setup; unlike with Windows, you don't start searching around for drivers.

Basically -- YES. A known exception is the offering of proprietary drivers but those are limited to video and networking. In other cases, if the hardware vendor doesn't offer Linux drivers, it's most likely the hardware is not going to work.

MOST people don't know what Linux is, so that doesn't make your situation unique.


> **carl4926 said:**
> Your first question in the forum is not very informative. You need to be more specific as to you particualr problem. At the moment it sounds more imagined than real.

If you plan to move a company to Linux use. I'd suggest you need at least one person to administer the process who is fully conversant with Linux.


You both have no idea about what I meant, so ask before you try to be genius or don't reply and that would be better. 

What I meant is that I'm looking for (Device Manager) in Linux. In Windows, you can click on (Device Manager) and you can see all drivers. If there is a driver not recognized by Windows, just click on that device and get the Hardware ID, then you can google that ID and you will get the right driver. 

Is there a way like that in Linux?


And by the way, Linux usually get sound, VGA, and wireless drivers. But Linux miss many drivers like SM card, fn keys, HDMI, etc. 

I'm looking for a good steps to get all drivers in my computer recognized in Linux.


Thanks guys,

---

### Post by buzzingrobot on 2014-04-06
No, there is no Device Manager in Ubuntu, now that you've actually asked the question on your mind. No need for it exists. The previous responses provide excellent and expert advice on this subject.

The Ubuntu installer detects the hardware components in a system and automatically installs the approrpriate "driver" from the Ubuntu repositories.  More precisely, as mentioned, it installs kernel modules, which is the way drivers are implemented in Linux.

Ubuntu does offer an "Additional Drivers" feature which will offer to install certain proprietary drivers for video cards and wireless chips if those vendors have released drivers for Linux that have been tested and packaged by Ubuntu.

Some printers require installation of a closed-source driver provided by the vendor.  A number of HP printers are in this category. GUI  tools are available in the repository to ease the installation.

Avoid bleeding edge brand new hardware and search for reports of any potential hardware choices *not* working on Linux. (People don't post when hardware works, as it usually does.)

---

### Post by oldos2er on 2014-04-06
> **ambt said:**
> You both have no idea about what I meant, so ask before you try to be genius or don't reply and that would be better. 


People here are volunteering their time  and effort to help you, and asking clear questions helps them to do so. Please keep your posts polite.

---

### Post by Mark Phelps on 2014-04-06
> I'm looking for a good steps to get all drivers in my computer recognized in Linux.

This is NOT how Linux works -- it doesn't go through drivers in your PC and try to figure out what they are for...

The Ubuntu installer looks through the hardware on your PC and attempts to install the proper driver for each. Not all hardware devices have Linux drivers -- and in that case, the way you usually find that out is by some piece of hardware not working.

Transitioning to Linux can be difficult for folks steeped in the MS Windows way of doing things.  Reading through the material in the link will get you started with learning how Linux is different:  [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by carl4926 on 2014-04-07
You can install: inxi

Then in a terminal do
```
inxi -F
```

It tells you something like what you are asking.

---

### Post by mastablasta on 2014-04-07
lshw and lspci are CLI hardware detection/listings of programs.

but there are a couple of other GUI programs that will show system hardware. Kubunt has Ksysteminfo or something like that i believe.

but indeed driver in linux are installed very differently as they are mostly built into kernel. unlike in windows where all drivers are separated from kernel.

---

