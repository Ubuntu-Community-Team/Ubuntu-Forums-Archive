---
title: "Ubuntu install blank screen Nvidia GPU"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by studiologe2 on 2014-04-26
Hi together,
I just got a new computer and I'm having severe problems starting the install of Ubuntu 14.04 as a first OS.

It always goes into a blank black screen and shows a blinking coursor for a while and then it goes completely black (backlight still on)
I'm using the following Hardware components:

Mainboard:    Asus Rampage iv extreme
CPU:        Intel Core i7-4930K
GPU:        EVGA 04G-P4-3688-KR GeForce GTX 680 (NVIDIA GeForce)
PSU:        OCZ ZX Series 1250W Power Supply
Memory:    Corsair CMD16GX3M2A1866C9 DDR3 1866 (4 Modules at 8GB = 32GB)
HDD:        Seagate Barracuda ST2000DL003 (2000GB) SATA3 6Gb/s connected at an SATA3 6Gb-Port
DVD:        Some HP DVD SATA3 also connected to SATA3 6Gb/s Port (would have to look what model it is, but it recognizes it and boots from it)


I'm absolutely unsure what settigns I need in the BIOS to make sure it boots ok.
I've seen many other posts already, but couldn't find anything that applies to my sprecific situation.

I tried different settings in the BIOS, but I'm absolutely clueless on which settings I need in the BIOS.
Further I did already try the different boot options from the install menu 
acpi=off
noapic 
nodmraid
nomodeset
But that also didn't make a difference.
I personally think the problem is in the bios settings and I'm not sure where. If someone installed any Linux flavor successfully before with this HW Configuration or a similar one, please advise me through the settings in the BIOS as there are so many options....
Do I need AHCI, UEFI and what is all that stuff anyways :-(

I'm so excited and would love to use the weekend to get this working and sorted out and I would absoulutely appreciate any support you guys can give me!!

Please help :-(
Thanks

---

### Post by Bashing-om on 2014-04-26
studiologe2; Hi !

I do not run Intel, and have never yet encountered UEFI; so I have no direct experience to offer.

However, this link is  similar to your situation, and offers a solution. 
[http://askubuntu.com/questions/340223/ubuntu-13-04-on-uefi-system-hangs-at-black-screen](http://askubuntu.com/questions/340223/ubuntu-13-04-on-uefi-system-hangs-at-black-screen)

Also ran across this from another 17 installer ->
> 
Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.



See oldfred's most excellent advise:
[http://ubuntuforums.org/showthread.php?t=2146179](http://ubuntuforums.org/showthread.php?t=2146179)

[INDENT]once we know what we are dealing with
[INDENT][INDENT][INDENT]we can take it from there
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by studiologe2 on 2014-04-26
Hi again!

I did try all the hassle with
acpi=off
noapic
nodmraid
nomodeset
and also 
Before "quiet splash," I included "acpi _ osi=Linux acpi _ backlight=vendor".

But I just can't get Ubuntu install to start it always goes to the black screen :-(

Then I downloaded a gentoo liveCD and I was able to boot into the LiveCD,
that basically just confirms, that I do NOT have any Hardware issues right? As the PC seems to be
working fine, just that there is an issues with getting the graphics mode or AHCI or UEFI or whaterver functioning right to
get to launch the installer... Am I correct with that?

Thanks for any suggestions, Please help me getting Ubuntu up and running as I'm not familiar with Gentoo at all :-/

---

### Post by Bashing-om on 2014-04-26
studiologe2; Hey.

All I can do is try, which I am willing to do. We still do not know what the booting method here is - UEFI or BIOS ?

What results when booting , as soon as the bios screen clears, depress and hold the right shift key ( small wind of opportunity here for grub to recognize a key has been pressed) .. I hope that the grub boot menu pops up .. like I have advised, no experience with UEFI ->

We still need to determine where the bootloader is installed to. As we can not boot anything I do not know of a way to find out software-wise.
What is set up in 'bios' as for the location of the boot code ?

[INDENT]in my ignorance will
[INDENT][INDENT]availeth some
[/INDENT][/INDENT][/INDENT]

---

### Post by studiologe2 on 2014-04-26
[ 						 							Hi ]("http://ubuntuforums.org/member.php?u=1111508")[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")
Thanks for your answers! I really do appreciate that you're taking the time to reply!

I'm clueless when it comes to UEFI and I haven't work much with Computers since 1998, of course I have used them, but not to this
building new systems extend.

So far I tried the following distros:
Ubuntu 14.04
Ubuntu 13.10
Gentoo livedvd-amd64-multilib-2012.1 (Here I was able to load the LiveDVD -> that indicates that my HW is working ok)

The Bios settings should be all good, as the boot order and that simple stuff.
But I don't know what AHCI is, UEFI and all that.

I will try a different HDD now and see if that makes a difference. I doubt it though.

Any other ideas, maybe like disconnecting everything and disabling all onboard devices and see if it makes a difference?

Thanks

---

### Post by Bashing-om on 2014-04-26
studiologe2; Well.

No I would not think sparring off that hard drive to have any effect. The i7 chipset is well supported, once booted I would not expect any problem.

The problem is to boot it !
Square 1 is how are you booting ? UEFI or bios ? Let's see if we can get some indication.

Boot the liveDVD, as soon as the boot screen clears, depress and hold the right shift key - now do you get a purple splash screen with a stick figure and keyboard icons at the bottom of the screen? OR -> do you see text on a black back ground ?

Once we can get to some type of terminal we can get the additional info to see where the boot codes are located.

[INDENT][INDENT]my ignorance does have
[INDENT][INDENT][INDENT]a cure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-04-26
Perhaps this will help:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It shows pictures. Tell us what you have.

Regards.

---

### Post by Bashing-om on 2014-04-26
@ grahammechanical ;

Thanks heapsl

[INDENT]2 heads are better than 1
[INDENT][INDENT]even if one is a goat head
[/INDENT][/INDENT][/INDENT]

---

### Post by studiologe2 on 2014-04-26
Hi again Bashing-OM
Thanks for sticking with me through this!

I just wanted to let you know that I appreciate your help so damn much! And give you an update and every-one else here.
All I did is, I bought 
1. an older GPU (an EVGA GeForce 210 PCIe 2.0 with AGP, HDMI and DVI) 
2. also bought a new Harddrive a Hitatchi 80GB SATA 3.0 (cheapest one they had)
3. connected the HDD and DVD drive to SATA 3.0 ports
4. booted into Ubuntu 14.04 liveDVD and started install from there.

First it seemed like it was hanging and I thought at some point my HDD is not being detected, I left the PC untouched until
the screen turned off (scared the crap out of me at first), woke it back up and the install continued...?

when it was done I removed the DVD rebooted and everything is good since then :-D

The installation finally worked out, if I find out more I will definitely post my experience and hope that it can help others that are going through this.


AWEESOME :-) THANKS to everyone who contributed!

---

### Post by studiologe2 on 2014-04-26
Hi [ 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanica[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")l,
I just now saw your Post and I will save the website you linked in my files, just for in case!
Also a lot of thanks to you for trying to help! :-) Thanks guys thanks thanks thanks, made my daaaay :-D

---

### Post by Bashing-om on 2014-04-26
studiologe2; Hey !

Glad things have worked out. - My norm on a new install is I never choose to install the updates during the install and never install the 3rd party software.
These can be added after a successful install, I watch the install and as well what get's installed afterward. To be honest, it is rare that I have a problem at all in any installs  - but again, I have done several Lubuntu installs and DSL  on very low spec hardware.

As all is good now, please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

[INDENT][INDENT]if it ain't got the hosses
[INDENT][INDENT][INDENT]don't load the wagon
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

