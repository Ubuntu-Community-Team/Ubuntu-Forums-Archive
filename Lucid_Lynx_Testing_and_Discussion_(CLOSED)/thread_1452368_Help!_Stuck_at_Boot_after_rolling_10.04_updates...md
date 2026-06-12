---
title: "Help! Stuck at Boot after rolling 10.04 updates.."
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kcleworth on 2010-04-11
Hi, 

So I installed Ubuntu 10.04 this morning Beta 2. And it's been working fine all day other than a few issues with Compiz which a BUG report has been filled for and a fix committed!

Anyway, about fifteen minutes ago I checked for latest updates and it found 16 or so updates. I installed these and then it asked me to reboot my laptop. 

I did so and then was met with this screen:

[ATTACH]152993[/ATTACH]

I had to take a photo with my iphone and mail it to myself and then boot 9.10 from a pen drive. 

ANY idea how I can fix this as my system just hangs there and won't boot. 

I would file this as a bug but i'm not quite sure how to document it. 

If not is there anyway I can revert to 9.10 and access the old root system on my hard-drive.

*sigh*

---

### Post by gilson585 on 2010-04-11
I too have this issue following the new kernel update today to 2.6.32-20

You can boot the old kernel if you hold shift as soon as the bios screen fades to black and wait for the grub menu then select 2.6.32-19

If someone could direct me on how to post the trace of the crash I would be more than happy to.

---

### Post by sirkeith on 2010-04-11
I also have the same experience. :popcorn:

keith

---

### Post by Digital Hick on 2010-04-11
Updated to 2.6.33.20 and everything went down the tubes.  Would not even boot, no plymouth, nothing.  Held down shift and booted into .19.  Everything fine, or as fine as Linux can be...

Reinstalled .20, no go, still will not boot

Uninstalled .20 through Synaptic.  Now boots fine on .19

Me thinks that it is great that Ubuntu Devs are cranking out code on Sunday, me thinks they also need to check for misplaced comma somewhere.

:lolflag:

---

### Post by kcleworth on 2010-04-11
*phew*

I made no backups and was just about to wipe everything and go back to 9.10 when I saw this thread... held down shift and ALL'S good. :)

---

### Post by jsevi83 on 2010-04-11
+1
kernel 2.6.32-20 won't boot

---

### Post by miegiel on 2010-04-11
Anyone posted a bug report yet ?

Is now
> **miegiel said:**
> Reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140)

---

### Post by kcleworth on 2010-04-11
I wasn't quite sure how it should be referenced in a Bug report... but if any of you guys have an idea.

Also do you have instructions on what kernels should be uninstalled so you don't have to hold down shift and select at startup?

---

### Post by ranch hand on 2010-04-11
Have any of you tried booting through recovery mode?

The new kernel, just to make you feel even better, works great for me.

---

### Post by kcleworth on 2010-04-11
I've tried booting through recovery and still no luck....

---

### Post by miegiel on 2010-04-11
> **ranch hand said:**
> Have any of you tried booting through recovery mode?

The new kernel, just to make you feel even better, works great for me.

No, not yet. I just booted ...-19 instead :D Trying to report the bug atm.

Anyways I[s]'m using[/s] was trying to use the 2.6.32-20-generic-pae kernel, 32bit. 

In case it's only with certain hardware :
```
user@machine:~$ sudo lshw -short
[sudo] password for x139137: 
H/W path               Device     Class       Description
=========================================================
                                  system      Aspire 3810T
/0                                bus         Aspire 3810T
/0/0                              memory      1MiB BIOS
/0/f                              memory      4GiB System Memory
/0/f/0                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/f/1                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/17                             processor   Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
/0/17/18                          memory      3MiB L2 cache
/0/17/1a                          memory      32KiB L1 cache
/0/17/1.1                         processor   Logical CPU
/0/17/1.2                         processor   Logical CPU
/0/19                             memory      32KiB L1 cache
/0/100                            bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                          display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                        display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/1a                         bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                       bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                         multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                         bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c/0            wlan0      network     Wireless WiFi Link 5100
/0/100/1c.2                       bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.2/0          eth0       network     AR8131 Gigabit Ethernet
/0/100/1d                         bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                       bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                       bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.3                       bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1d.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      ICH9M-E LPC Interface Controller
/0/100/1f.2            scsi1      storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0.0.0      /dev/sda   disk        320GB WDC WD3200BJKT-0
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      64GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      234GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5  volume      4094MiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0/2/6  /dev/sda6  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/7  /dev/sda7  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/8  /dev/sda8  volume      206GiB Linux filesystem partition
/0/100/1f.3                       bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                       generic     82801I (ICH9 Family) Thermal Subsystem
/1                     vboxnet0   network     Ethernet interface
```

---

### Post by kcleworth on 2010-04-11
Thats interesting... you are running a 3810t and i'm on a 5810t... 

If i'm not mistaken, they are both Acer Timelines?

---

### Post by kcleworth on 2010-04-11
We are running much of the same hardware....

```
kristian@kristian-laptop:~$ sudo lshw -short
[sudo] password for kristian: 
PCI (sysfs)  
H/W path           Device      Class       Description
======================================================
                               system      Aspire 5810T
/0                             bus         Aspire 5810T
/0/0                           memory      1MiB BIOS
/0/16                          memory      4GiB System Memory
/0/16/0                        memory      2GiB SODIMM Synchronous 800 MHz (1.2 
/0/16/1                        memory      2GiB SODIMM Synchronous 800 MHz (1.2 
/0/1e                          processor   Intel(R) Core(TM)2 Solo CPU    U3500 
/0/1e/1f                       memory      3MiB L2 cache
/0/1e/21                       memory      32KiB L1 cache
/0/20                          memory      32KiB L1 cache
/0/100                         bridge      Mobile 4 Series Chipset Memory Contro
/0/100/2                       display     Mobile 4 Series Chipset Integrated Gr
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Gr
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c/0        eth0        network     AR8131 Gigabit Ethernet
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1/0      wlan0       network     Wireless WiFi Link 5100
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.3                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M-E LPC Interface Controller
/0/100/1f.2        scsi1       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        500GB TOSHIBA MK5055GS
/0/100/1f.2/0/1    /dev/sda1   volume      365GiB Extended partition
/0/100/1f.2/0/1/5  /dev/sda5   volume      365GiB Linux filesystem partition
/0/100/1f.2/0/3    /dev/sda3   volume      99GiB Windows NTFS volume
/0/100/1f.2/1      /dev/cdrom  disk        DVD-RAM UJ862AS
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                    generic     82801I (ICH9 Family) Thermal Subsyste
/1                             power       OEM_Define4

```

---

### Post by miegiel on 2010-04-11
> **kcleworth said:**
> Thats interesting... you are running a 3810t and i'm on a 5810t... 

If i'm not mistaken, they are both Acer Timelines?

Yes, it's an acer ](*,)

---

### Post by kcleworth on 2010-04-11
Oh dear. Well, let me know how the bug report goes... I guess we are going to have to carry on with -19. 

Did you have the problem in changing your visual effects aswell?

---

### Post by miegiel on 2010-04-11
Reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140)

---

### Post by ranch hand on 2010-04-11
That is what we are here for.  Not to make it run with work arounds.

We are here to have it break on our hard ware.  File bugs.  Let the devs work their voodoo on it.

This is how we get a great release.

Good work.

I hope every one that has this problem subscribes to that bug so that;

A>The devs know it is real (it has to be confirmed)

B>The devs have folks they can contact for more info

---

### Post by NightwishFan on 2010-04-11
I can confirm this as well. I will collaborate in the bug report.

---

### Post by Crunchy the Headcrab on 2010-04-12
Same here.  I'm using an Asus, not an Acer.

---

### Post by JMFTheVCI on 2010-04-12
Also affecting my Lenovo T61. Looks like it is a more widespread issue and probably not HW related.

---

### Post by rogerdean on 2010-04-12
...but it doesn't happen for a 32-bit install within VirtualBox. hardware-dependant?

---

### Post by gmc on 2010-04-12
This is the exact same problem I had with 10.04-rc5 on my Asus UL20A. I thought I'd buggered my SSD drive when it happened and went back to 9.10 to test it. Then upgraded to 10.04 beta 1 which seemed to work just fine.

---

### Post by mfraser on 2010-04-12
I'm getting this on a Toshiba NB100. Can't even get into the GRUB2 menu to choose another kernel.

---

### Post by teh603 on 2010-04-12
Glad I came to the boards early. I'm not going to run the updater at all until this gets settled.

---

### Post by dentaku65 on 2010-04-12
I did this (and worked):
when the screen of plymouth + fsck stops at 72% I waited 2 minutes, then I press ALT+PrtScreen+REISUB (REISUB are the letters R E I S U B on keyboard; see: [http://kember.net/articles/231/reisub-the-gentle-linux-restart);](http://kember.net/articles/231/reisub-the-gentle-linux-restart);) on next reboot the boot is fine; I think that the problem is plymouth and not fsck (that's why I've waited 2 minutes).

:-)

---

### Post by Digital Hick on 2010-04-12
> **dentaku65 said:**
> I did this (and worked):
when the screen of plymouth + fsck stops at 72% I waited 2 minutes, then I press ALT+PrtScreen+REISUB (REISUB are the letters R E I S U B on keyboard; see: [http://kember.net/articles/231/reisub-the-gentle-linux-restart);](http://kember.net/articles/231/reisub-the-gentle-linux-restart);) on next reboot the boot is fine; I think that the problem is plymouth and not fsck (that's why I've waited 2 minutes).

:-)


Wow, Plymouth having trouble, who would have ever believed it!
:lolflag::shock:[-o<

Anyway I am on a Compaq and it did not want to boot for me either.  Totally removed anything marked higher than 2.6.33-19 through synaptic and it boots now without holding down Shift.

---

### Post by JoeWheeler on 2010-04-12
What do you remove through synaptic? I don't want to try and get rid of it and screw up my whole system

---

### Post by BrokeMahPC on 2010-04-12
Took the plunge and updated to 2.6.32-20-generic - 12 April at 12pm GMT
No problems with 10.04 i386 Desktop Beta2
Boots fine - all up and working

I notice some of you are using 2.6.33 - the latest Kernel, is this problem occurring with that kernel or also with 2.6.32?

---

### Post by Xorlathor on 2010-04-12
> **gilson585 said:**
> I too have this issue following the new kernel update today to 2.6.32-20

You can boot the old kernel if you hold shift as soon as the bios screen fades to black and wait for the grub menu then select 2.6.32-19

If someone could direct me on how to post the trace of the crash I would be more than happy to.

Same here - Wouldn't boot into the desktop after the 2.6.32-20 kernel update. I can boot into 2.6.32-19 using the GRUB menu, that's how I'm posting this. Any help?

---

### Post by Xorlathor on 2010-04-12
> **rogerdean said:**
> ...but it doesn't happen for a 32-bit install within VirtualBox. hardware-dependant?

Could be, this problem seems prevalent with Compaq computers - my laptop's a compaq and I have to revert to 32-19-generic to boot in at all.

---

### Post by OhadE on 2010-04-12
same here.
I'm with Lenovo Thinkpad X60s.

---

### Post by The Pixel Developer on 2010-04-12
[COLOR="Silver"]I can also confirm this bug affects my desktop computer. I'll have the specifications and bug report when I get the system up and running again.

As for booting into the older kernel, no such luck here. Everything hangs when I type a sudo command.[/COLOR]

**[Edit]: Disregard that, I think it was ndiswrapper's fault.**

---

### Post by miegiel on 2010-04-12
> **dentaku65 said:**
> I did this (and worked):
when the screen of plymouth + fsck stops at 72% I waited 2 minutes, then I press ALT+PrtScreen+REISUB (REISUB are the letters R E I S U B on keyboard; see: [http://kember.net/articles/231/reisub-the-gentle-linux-restart);](http://kember.net/articles/231/reisub-the-gentle-linux-restart);) on next reboot the boot is fine; I think that the problem is plymouth and not fsck (that's why I've waited 2 minutes).

:-)

No such luck here :| I even [s]waited[/s] whent to do something else for 20min.

---

### Post by His on 2010-04-12
This is strange, because after my upgrade to 2.6.32-20 my computer boots and shuts down faster than it ever has, and everything seems smoother than ever. I mean ever.

---

### Post by sirkeith on 2010-04-12
I am running a T-23.

Thanks for filing the bug report. WIll subsribe to it.

keith

---

### Post by timosha on 2010-04-12
> **His said:**
> This is strange, because after my upgrade to 2.6.32-20 my computer boots and shuts down faster than it ever has, and everything seems smoother than ever. I mean ever.

That's not strange because Lucid Beta is like a lottery, some people win others loose.

---

### Post by dino99 on 2010-04-12
have to wait a little: new release has been released 1 hour ago (bug 561151)

---

### Post by JoeWheeler on 2010-04-12
> **dino99 said:**
> have to wait a little: new release has been released 1 hour ago (bug 561151)
This come through for anyone yet? Ive no idea how long it takes to make it into the repositories

---

### Post by miegiel on 2010-04-12
> **JoeWheeler said:**
> This come through for anyone yet? Ive no idea how long it takes to make it into the repositories

I got some new updates, but not this one yet. It can take a couple of hours I think, depends on the mirror. I'm in no hurry 2.6.32-19 works fine, 2.6.32-20 can wait till tomorrow ;)

---

### Post by pieface on 2010-04-12
im stuck to,when i enter startx it hangs,the mouse curser cannot move but the little bar is still blinking ready for text to be input.  Using a dell xps m1530 and updated yesterday

---

### Post by miegiel on 2010-04-12
> **pieface said:**
> im stuck to,when i enter startx it hangs,the mouse curser cannot move but the little bar is still blinking ready for text to be input.  Using a dell xps m1530 and updated yesterday

That might be a different bug. The problems people are having here is with something ACPI related in kernel 2.6.32-20. Try getting the latest updates, I saw something X related fly past when I updated last.

---

### Post by gilson585 on 2010-04-12
The new kernel 2.6.32-20.30 released today solves my issue. Thx everyone

---

### Post by JoeWheeler on 2010-04-12
I seem to be OK after todays kernel update :)

---

### Post by Xorlathor on 2010-04-12
Updated again and it works fine - thanks for the prompt fix, but it would be nice if this didn't happen in the first place. Guess it's my fault for using Lucid. ;-) I love bleeding edge software, and I'll use it no matter the cost. (At least most of the time...)

---

### Post by Digital Hick on 2010-04-12
Back in business, had to manually install.  Did not show up in updates for tonight.  That is partially my fault I guess.  Might wait a day on kernel updates from now on, just to see if anyone else hollers about breakage.

---

### Post by fruitz on 2010-04-13
I tried to hold shift...but simply nothing happens...i have the grub screen with the -20 kernel... moreover, I use startup manager to only show the last kernel on grub...so I have no idea about what to do...

---

### Post by NightwishFan on 2010-04-13
If you can see recovery mode, go into it and drop to a netroot prompt. Then run this command to upgrade (you dont need sudo):
```
aptitude safe-upgrade
```

---

### Post by miegiel on 2010-04-13
> **fruitz said:**
> I tried to hold shift...but simply nothing happens...i have the grub screen with the -20 kernel... moreover, **I use startup manager to only show the last kernel on grub**...so I have no idea about what to do...

That's not a good idea, it's better to show the current and previous kernel. This 2.6.32-20 kernel hiccup is a good example why. ;) But I think you still can edit the kernel and initrd lines from the grub menu and just change 2.6.32-20 to 2.6.32-19, unless the old kernel has been deleted from */boot/*.

---

