---
title: "ubuntu 18.04 LTS installation problems"
date: 2019-05-18
forum: Installation &amp; Upgrades
---

### Post by chaslie on 2019-05-18
Hi,

I am at my wits end trying to install ubuntu 18.04 on my pc. I have tried all the work arounds suggested and nothing works. It hangs at the updates and other software stage. I have even tried installing 19.04 and this hangs at the same stage.

My system is an [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]Intel® Core™ i9 12 Core Processor i9-9920X,based on the gigabyte x299 ud4 pro motherboard (flashed to bios version f4i). The graphics card is [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]11GB ASUS DUAL GEFORCE RTX 2080 Ti.

I have tried using the switch [LEFT][COLOR=#242729][FONT=inherit]modprobe.blacklist=nouveau and changing quite splash to nomodeset.

I need to be able to have hyperthreading on when its installed, but it do get the error about the acpi and also the problem with nouveau chipset not recognised. 

I am ready to bin Linux altogether and persevere with windows :-(, please help, anyone ?????

thanks in advance

chaslie[/FONT][/COLOR][/LEFT][B][I][U][SUB][SUP]



[/SUP][/SUB][/U][/I][/B][/FONT][/FONT]

---

### Post by DuckHook on 2019-05-18
[list=1]
[*]It is perfectly okay to stick with Windows if that is what works.
[*]Your HW is bleeding-edge and high-end. Linux must reverse engineer drivers for many such components and this takes time and effort. Yours may not be supported yet. OEMs will take care to produce Windows drivers for their products at launch. Linux, if they bother to support it at all, is usually an afterthought.
[*]I would recommend Disco for your build. You need the latest and greatest for best chance of compatibility/success. The downside is that you will be on the upgrade treadmill till at least 20.04.
[*]Will your box run a LiveUSB? (Try both Bionic and Disco.) If so, then it's simply a matter of some sticky configuration issue and is ultimately fixable.
[*]You could try using an absolutely minimal CLI image (server install), then adding a DE afterwards. No guarantees, but you seem to be able to at least get partway in the process. Perhaps a simpler install might work.
[*]There are always alternate distros that might also work. Though not a high probability, you can try Mint or Fedora, which come with slightly different default configurations and drivers.[/list]

---

### Post by cruzer001 on 2019-05-18
You have the 410 driver installed?
[https://www.nvidia.com/Download/driverResults.aspx/138279/en-us](https://www.nvidia.com/Download/driverResults.aspx/138279/en-us)

HyperThreading is a BIOS setting and not found in the operating system.

Why Ubuntu? Are you setting up a Linux gaming machine?

---

### Post by chaslie on 2019-05-18
hi DuckHook,

not sure what you mean by disco? Is that Ubuntu 19.04, if so then i have the same problems with it. I was thinking of trying red hat, is there any milage?

Chaslie

---

### Post by chaslie on 2019-05-18
hi Cruzer001,

The problem is that i cannot get the instalation of ubunto to get past the other software stage, so installing the 410 driver is a long way off.....

---

### Post by DuckHook on 2019-05-18
> **chaslie said:**
> …not sure what you mean by disco? Is that Ubuntu 19.04Yes.
> …if so then i have the same problems with it.
> **DuckHook said:**
> …Will your box run a LiveUSB? (Try both Bionic and Disco.) If so, then it's simply a matter of some sticky configuration issue and is ultimately fixable.Please answer all questions and try all options suggested. Otherwise, we will just be spinning our wheels.
> …I was thinking of trying red hat, is there any milage?
Already answered: Fedora is Red Hat's community edition (both further suggestions restated below).
> [list][*]You could try using an absolutely minimal CLI image (server install), then adding a DE afterwards. No guarantees, but you seem to be able to at least get partway in the process. Perhaps a simpler install might work.
[*]There are always alternate distros that might also work. Though not a high probability, you can try Mint or Fedora, which come with slightly different default configurations and drivers.[/list]
> **chaslie said:**
> …The problem is that i cannot get the instalation of ubunto to get past the other software stage, so installing the 410 driver is a long way off.....
Again, can your box successfully run a LiveUSB?

---

### Post by chaslie on 2019-05-18
Duckhook,
 
I can start a ubuntu18.04 from the he usb no problems, however my WiFI is not recognised..

19.04 crashes at the text screen, (if I had to guess its a graphics issue). it is talking about acpi Bios Error (bug): could not resolve.....

definitely graphics problem because I can get into the 19.04 desktop using safe graphics

---

### Post by DuckHook on 2019-05-18
> **chaslie said:**
> …I can start a Linux session from the usb no problems,That's good news. It means that yours is just a configuration issue and stands a decent chance of being fixable.
> however my WiFI is not recognised....
Let's tackle one issue at a time.

[LIST=1]
[*]You mention that the install "hangs". What do you mean by this? If no activity, how long have you waited? If at some specific point, can you pinpoint what package?
[*]Make sure you are installing through wired connection and not using WIFI.
[*]You mention that you've tried "nomodeset". How have you done this? Did you include it as a kernel parameter at the start of the install process? If so, please give specific steps you took.
[/LIST]

---

### Post by DuckHook on 2019-05-18
> **chaslie said:**
> &#8230;19.04 crashes at the text screen, (if I had to guess its a graphics issue). it is talking about acpi Bios Error (bug): could not resolve.....

definitely graphics problem because I can get into the 19.04 desktop using safe graphics
:confused:
I thought you couldn't install either Bionic or Disco. So how can you get into 19.04 safe graphics mode???

You edited your post after my first reply.

---

### Post by chaslie on 2019-05-18
apologies, 

I have tried both 19.04 and 18.04, they hang during installation (left for 5-10minutes) during the other software screen ( the one after you select the keyboard).

I can get 18.04 to load a desktop from the USB, but WiFI is not recognised.

I can get 19.04 to only load a desktop from the USB in safe graphics mode (no wifi). the other option crashes, with the acpi error and the screen starts blocking (looks like a graphics issue). 

I have insert the commands [LEFT][COLOR=#242729][FONT=inherit]modprobe.blacklist=nouveau and changing quite splash to nomodeset. by pressing 'e' at the boot installer. 

[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2019-05-18
Some issues are by brand and some by chip set.
Asus has wireless issue also.
Asus X299 Wired Internet issue, UEFI system clock
[https://ubuntuforums.org/showthread.php?t=2395036](https://ubuntuforums.org/showthread.php?t=2395036)
[https://ubuntuforums.org/showthread.php?t=2397473](https://ubuntuforums.org/showthread.php?t=2397473)
MSI x299 SLI Also acpi=off boot parameter
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)

Some older Gigabyte have also need acpi=off boot parameter. And just about everyone with nVidia needs the nomodeset boot parameter, so you probably need both.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by chaslie on 2019-05-19
looks like fedora has installed, no problems. thanks for you help.

---

