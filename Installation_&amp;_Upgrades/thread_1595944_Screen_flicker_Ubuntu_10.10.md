---
title: "Screen flicker Ubuntu 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by eclug on 2010-10-13
Screen flicker Ubuntu 10.10
After installing Ubuntu (Version 10.10 DVD –amd 64Ubuntu 10.10 live DVD).
On the following hardware 
Gigabyte GA-K8VT800-RH motherboard
3GB ram
AMD Sempron 3400 cpu.
ATI Radeon X1600 Pro Video card.  256M ddr2 AGP VGA/TV0/DV1-1
p/no 882c85-03

The screen resolution looked very good with all screen resolutions working well
The colours and fonts very clear.
All other device drivers worked 100%.
But unfortunately the display flashes about every 10 seconds and the partial beak up of the display only lasts a fraction of a second and very distracting and is unusable.

Testing with  Ubuntu 10.10 live DVD. With this months Linux Format Magazine also exhibits this problem.

However deleting the partition and installing Ubuntu  10.04 Beta1 DVD -386.
And all updates downloaded. Works 100% with no screen flicker.

I wonder if anyone is experiences this problem and found a fix.

Tony

---

### Post by vvara on 2010-10-14
I have the same problem in Ubuntu 10.10 32 bits. 
My graphic card is ATI Radeon X1600 512M.

---

### Post by laddielegz on 2010-10-14
yes i have the same, flicker every 5-10 seconds, radeon x1600 , sempron 3400, any ideas please.

---

### Post by corpse1012 on 2010-10-16
[http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600](http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600)

```
sudo apt-get install gksu
```

```
gksudo gedit /etc/default/grub
```

then find this line in the text file: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


then make it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"


then save , then back to terminal and write:
```
sudo update-grub
```

---

### Post by zuerston on 2010-10-16
> **corpse1012 said:**
> [http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600](http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600)

```
sudo apt-get install gksu
``````
gksudo gedit /etc/default/grub
```then find this line in the text file: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

then make it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX="nomodeset"

then save , then back to terminal and write:
```
sudo update-grub
```


[SIZE=6][B]WARNING!!!
DO NOT DO THIS  ,,I did and it blew out grub and I had a hell of a time getting back up it would not load X  !!!!  WARNING[/B][/SIZE] :mad:](*,)

---

### Post by lzieg on 2010-10-16
Same problem here with ATI Radeon X1600!

---

### Post by Liqwid122 on 2010-10-16
I have the same exact problem with a 2.4GHz P4 and a Geforce 4 ti 4800.

Everything worked well in 10.04.

In 10.04 I swear there was a proprietary driver I installed to use with the card. When I searched for proprietary drivers in 10.10, nothing came up.

This is really frustrating and almost unusable....

---

### Post by lzieg on 2010-10-18
I solved the problem by switching back to the lucid kernel 2.6.32-21. Not a nice solution but working.

---

### Post by wakk0 on 2010-10-20
I'm having this problem as well on 10.10 with a Radeon 4670. Anyone know of a solution to this without having to downgrade the kernel?

---

### Post by Liqwid122 on 2010-10-22
I guess nobody has a solution. Maybe I will just downgrade the kernel...

---

### Post by peredur on 2010-10-24
Just to add my 2c (Ceiniogau Cymreig), I've got the same problem and the only solution I've found is to downgrade the kernel.  I hope someone at Ubuntu is looking at this.

Cheers


Peter

---

### Post by MalditohoN on 2010-10-24
i newly installed ubuntu 10.10 on my pc with a phenom processor. and updated the proprietary driver for display but when i restarted the login screen is flickering...

---

### Post by wakk0 on 2010-10-25
Are there any good guides to downgrading the kernel?

---

### Post by ezra4no1 on 2010-10-27
I am using an Old Dell GX280 Stock to run Ubuntu. 10.04 Was working fine and I didn't have an y problems, but I have updated to 10.10 and now my screen is flicking like others who have posted in this thread and it is freaking on my nerves.  Since there appears to be no real fix for this and I am a Linux n00b, like the person before me posted, does any one happen to know directions to downgrade the kernel so I can get back to using my linux OS with out the screen flickering ever 10 seconds or so?

THX...

---

### Post by naffna on 2010-10-27
I have an older system with an archaic on-board graphics card Sis i think. I removed my AGP based ATI X1300 Pro and started using the on board card. No desktop effects, but no annoying flicker either.
I am thinking of plugging the ATI card after a fix is found.

---

### Post by shellphish on 2010-10-27
Working on a buddies HTPC and ran into the same problem, running a Radeon x1600 pro 512. Really hope that a fix is found soon.

---

### Post by peredur on 2010-10-30
> **wakk0 said:**
> Are there any good guides to downgrading the kernel?

I just arrow down to the previous version on the boot screen.  And I echo what others have said about hoping there's a solution soon.

Does anyone know if Canonical knows about the problem?  It'll certainly not get solved unless we tell them :-)

Cheers


Peter

---

### Post by TonyFordz on 2010-10-30
Hello,

Yeah I get the same problem with my screen which was working 100% no problems until I did the upgrade to 10.10, now if I am lucky I can use the pc for about 2-5mins then it bugs out on me, and I have to force restart my pc.

Motherboard: [Biostar A740G M2+ (AMD)]("http://www.biostar.com.tw/app/en/mb/content.php?S_ID=350")
CPU: AMD Athlon 64 3800+
HD: 4x 500GB SATA II 7200RPM Western Digital, 1x 80GB E-IDE 5400RPM Samsung (Master Boot)

I know its not anything to do with my hardware, I honestly think that something was over looked or left out of the 10.10 upgrade because as I said I didn't have these problems till I went from 10.04 LTS to 10.10

I am not going to atemp to use the terminal codes since someone else said that made things worse for them being I am not native to Linux.

On note of ATI mine is currently onboard as I am not using my cards right now on this PC. ATI Radeon&#8482; HD2100 Graphics, On Board Graphic Max. Memory Share Up to 512 MB

---

### Post by peredur on 2010-10-30
> **TonyFordz said:**
> 
Yeah I get the same problem with my screen which was working 100% no problems until I did the upgrade to 10.10, now if I am lucky I can use the pc for about 2-5mins then it bugs out on me, and I have to force restart my pc.


Have you tried selecting a different kernel from the list Grub gives you when you boot?  You shouldn't have to be restarting your machine all the time.  That's a major irritation as opposed to the minor one of just selecting a different kernel.

Cheers


Peter

---

### Post by shellphish on 2010-10-30
My ubuntu install is brand spanking new so i do not have any other kernel to go back to.
So can someone please refer me to a guide to downgrade my kernel since the solution to this problem is nowhere to be found.

---

### Post by kestsang on 2010-10-31
i have same problem.  very annoying ... cannot use the new ubuntu 10.10 (32-bit, install from CD).

Asus M4A785T-M/CSM / AMD Athlon II X3 435 / ATi AIW1900 / 2GB ram

---

### Post by sportscliche on 2010-11-04
I have the problem on a Dell Latitude E4310 laptop.  Like the others, rolling back the kernel from 2.6.35-22 to 2.6.32-21 (ie. 10.10 to 10.04) eliminated the annoying flicker.  Mine could be as frequent as every 10 seconds or once every 15 minutes, yet distracting enough to make me switch back.  I'm running Lubuntu and did the upgrade primarily to get the automatic notification updates that had been missing in the earlier versions.  I will monitor this thread and would greatly appreciate if someone would post here when the kernel gets fixed.

---

### Post by finwake on 2010-11-04
I am experiencing the same intermittent issue.  Also, streaming music gets choppy cut-outs when the screen does its flicker.

Thinkpad T60, Integrated Graphics

---

### Post by Nomax on 2010-11-08
Hi!

I just wanted to say that I have the same problem. I have an ATI Radeon X1600 XT (RV530). It was working fine in previous versions of Ubuntu but began to flicker when I upgraded to version 10.10.

I use it daily but the frequent flickering is annoying for sure.

---

### Post by finwake on 2010-11-08
My problem may be different from others, but I will post my resolution for laptop users to try -- and for anyone else to try if they so choose.

My battle-scarred Thinkpad has apparently started sending a message that the laptop lid has been closed; this caused my screen to turn-off and back on with a flicker.  I fixed it by changing the power management properties to 'do nothing.'

As documented in this [post]("http://www.rebelzero.com/fixes/karmic-gnome-power-manager-hides-do-nothing-from-the-gui/223").

---

### Post by the.scarecrow on 2010-11-08
Is this deja vu?

[http://ubuntuforums.org/showthread.php?t=1473580](http://ubuntuforums.org/showthread.php?t=1473580)

I was hoping a fresh install of 10.10 would at last fix this problem for me.

---

### Post by knowledgeispwr on 2010-11-10
I am having the same issue with Ubuntu 10.10 on a ThinkPad T60 and I believe a Radeon X1400 chip.  Usually the desktop is usable for awhile, and then the flickering, jumping and distortion becomes so bad that the computer is unusable.  I dual-boot with Windows 7 and I have no such problem with it.

---

### Post by the.scarecrow on 2010-11-11
Well, I did a fresh install of 10.10 64bit on my Dell Latitude 1750 and I seem to be in luck as the flashing screen has stopped. The only problem I have had with 10.10 is with gPodder 2.6 (it has a major bug in it), cured by installing the latest version 2.9.

---

### Post by b00tl3g on 2010-11-12
Got a similar issue, not sure if same as everyone else. The flicker I'm experiencing seems to be linked with compiz and my cube setup. Ran 10.04 no problems, after upgrade to 10.10 one of the two screens I have goes blank for a split second every time I open a new app, rotate my cube, or sometimes when switching between applications. Not a deal breaker, but very annoying. This is my main dev machine at work, and a clean install would be a pain to execute as I have my whole dev environment set up on this Ubuntu box.

andre@it-dev:~$ sudo lspci
[sudo] password for andre: 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)

---

### Post by TonyFordz on 2010-11-16
Yeah,

I don't know what the deal was but I am running from live version now on my 8GB thumb drive... I gave up on installing it & just run from live now which is just as good as installing & I can use it any place not losing any of my downloads, files, etc... If only I could get windows to do that

---

### Post by mpbio01 on 2010-11-22
I've got the same issue with a Dell E4310 running 10.10 64-bit.
Annoying to say the least.



00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation Device 3b57 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by TinaPotter on 2010-11-24
I have managed to fix this on my Dell Latitude E4310 by changing an option in grub

change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.powersave=0"

and then update grub as root

update-grub

No more flicker!

---

### Post by pembertonq on 2010-11-24
Here is the bug report for this bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+bug/666441?comments=all](https://bugs.launchpad.net/ubuntu/+bug/666441?comments=all)

If you have this bug, please go there, and click on ¨This bug also affects me¨, because at the moment it looks like only three people have it, and so will get low priority.

---

### Post by sportscliche on 2010-11-24
Thanks for the link Steven.  Note that you'll have to register on Launchpad to report this affecting you.

I tried Tina's GRUB patch on my E4310 without success.  My flicker is typically only once every 5 minutes, so I'm learning to live with it.

---

### Post by knowledgeispwr on 2010-11-25
After the recent batch of updates, including kernel 2.6.35-23, I have not noticed the crippling, work-ending flickering.  I guess I cannot be certain yet, as the problem previously seemed to happen randomly after an indefinite amount of time.

---

### Post by jadacyrus on 2010-11-28
just installed 10.10 netbook edition on my gf's thinkpad (with a radeon video card), im having this same problem. As soon as the GUI comes up, it flickers on and off every 2 seconds and is completely unusuable

---

### Post by peredur on 2010-11-30
Just updated to the latest kernel.  Still got the problem.  I used to be able to get around it by selecting an earlier kernel (21), but this will no longer boot successfully after latest update.  So I'm having to live with the flicker until I can find the time to install a different distribution that doesn't have the problem.

>> sigh <<

Or it gets fixed, of course.

:-)

AMD64 running 32 bit Ubuntu 10.10 ATI Radeon X1300


Peter

---

### Post by wakk0 on 2010-12-01
Everyone should make sure and go to the bug report and select the link at the top that states the bug affects you. Without higher numbers this will remain a very low priority.

---

### Post by peredur on 2010-12-02
Already done.

---

### Post by Claudin on 2010-12-03
Got the same thing. I have noticed that the flickering goes away for a minute or two if I "shake" my cube around :D There is also no flickering as long as I don't do anything, i.e don't move the mouse pointer.

---

### Post by Claudin on 2010-12-08
Finally found what caused my flickering screen, namely the screensaver Electric Sheep. After uninstalling I've had no more problems.

---

### Post by ecatodarcus on 2011-01-25
i have the same problem.
i reported it to launchpad.
i hope this will be fixed soon

---

### Post by derver on 2011-02-21
> **corpse1012 said:**
> [http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600](http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600)

```
sudo apt-get install gksu
```

```
gksudo gedit /etc/default/grub
```

then find this line in the text file: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


then make it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"


then save , then back to terminal and write:
```
sudo update-grub
```



Thanks, I did that and solved my problem. I have an ATI x1600, ubuntu 10.10 maverik

---

### Post by DonL on 2011-02-21
I put an old ATI TV card into my desktop box running 10.04 and I noticed flicker coming and going at certain intervals. I tried googling for answers and upgraded to 10.10. No difference.
Just tonight I noticed that when my oil filled portable heater clicked on thermostatically, I got screen flicker. When I turned it down, the flicker went away. So I put it on a different circuit and all's well.
I'm not saying that's your problem, but it sure was mine. I must have spent a whole day mucking around trying to sort it.

---

### Post by DonL on 2011-02-22
Spoke too soon. It's back to haunt me.
I don't understand. It comes and goes. Just when I think I've got it fixed, it's back.

---

### Post by DonL on 2011-02-22
Finally solved it! The old ATI TV card I installed was the problem. As soon as I removed it, the flicker went away. I'll let you know if it comes back, but I think this was the cause.
Unfortunately, I can no longer watch tv on the computer, but the lack of flicker is well worth it!

---

### Post by pembertonq on 2011-03-01
The problem went away with an update that happened today.

---

### Post by sportscliche on 2011-03-02
I upgraded from kernel 2.6.35-24 to 2.6.35-27 today and my screen flicker (Dell Latitude E4310) disappeared.  This is consistent with my experience that a kernel rollback will also cure it.

---

### Post by shaip on 2011-03-07
> **derver said:**
> Thanks, I did that and solved my problem. I have an ATI x1600, ubuntu 10.10 maverik

i tried this but, it did not worked. i can't logg in afther making  the grub changes, only in safe mode. any ideas ?

---

### Post by shaip on 2011-03-07
> **corpse1012 said:**
> [http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600](http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600)

```
sudo apt-get install gksu
```

```
gksudo gedit /etc/default/grub
```

then find this line in the text file: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


then make it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"


then save , then back to terminal and write:
```
sudo update-grub
```

this i what i tried  to be exact. i also have a ati x1600pro

---

### Post by stalagmit on 2011-03-19
> **corpse1012 said:**
> [http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600](http://ubuntuforums.org/showthread.php?t=1473580&highlight=x1600)

```
sudo apt-get install gksu
``````
gksudo gedit /etc/default/grub
```then find this line in the text file: 
GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet splash&quot;


then make it like this:
GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet splash nomodeset&quot;


then save , then back to terminal and write:
```
sudo update-grub
```

Another happy user, solved my problem with ATI Mobility Radeon HD 2300 on Ubuntu Maverick fresh install.

---

### Post by ross9885 on 2011-04-23
Same problem here, flickers every few seconds or so, sometimes. I tried adding "nomodeset" to the GRUB parameters, but it prevented X from starting. I reverted it from the login shell, it was worth a try.
  Only 32 people have have notified Launchpad that this affects them too, I suspect that this actually affects thousands of people. Hit that button! [link]("https://bugs.launchpad.net/ubuntu/+bug/666441?comments=all")

---

### Post by crafter on 2011-06-14
This fixed it for me.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

