---
title: "Ubuntu 6.10 freezes on while installing!!"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by RageWarp on 2007-01-24
Just to let you all know I am a complete and utter Linux newb. Ive been hearing good things about this distro so i decided to install it as a second boot on my HD. so anyways i download the OS burn it, and run it on start up. My original problem was a NOAPIC error which i think i fixed by typing 'noapic' in on the  F6 option at the main install screen. after doing so i start the install, the little ubuntu splash comes up with the bar going back and forth, all seems normal,  when it finishes i hear the, what i think is, the start up chime and then cursor stoped blinking which tells me that its frozen. Ive tried this a multitude of times and still nothing, help would be much appreciated.  

my specs are:

CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ @ 2.01GHz - 0% Load
Display: 1024x768 @ 60hz on Two  NVIDIA GeForce 7600 GS [SLi]
Hard disk C:\ Free: 45.75GB | Used: 103GB | Total: 149.04GB

---

### Post by rruelas on 2007-01-24
I'm not sure if this would be part of the problem, but how much memory is on your computer?
When you're running Ubuntu from the CD, it all goes straight into the memory, and it uses 200MB or more. That might be causing your problem, but I don't know what a NOAPIC error is... :|

---

### Post by RageWarp on 2007-01-24
i got 1gb of ram so that shouldnt be the prob

---

### Post by RageWarp on 2007-01-25
bump

---

### Post by RageWarp on 2007-01-26
bump

---

### Post by RageWarp on 2007-01-28
bump

---

### Post by had3z on 2007-01-29
indeed, bump
i have xp 3800+ x2, 2 gb of ram, and a geforce 6800gs (leadtek). ubuntu 6.10 freezes evan in safe graphics mode, and the screen scrambles into lines and little sqares

ps: that's a pretty lame advice, thinking that an xp 3800+x2 doesn't have 200 mb of ram. my old duron 900 had 256 mb. ubuntu 6.10 works fine on that one

---

### Post by RageWarp on 2007-01-31
yeh, that was kind of an un neccesary question, anywho

common people, get me a solution!!!

---

### Post by jenks on 2007-01-31
Hello,

  I'm sorry to see that this thread isn't getting more activity, maybe because the other readers don't have a specific solution to suggest - and I don't either. However, I have a few general suggestions that may get you un-stuck. First, I wonder if you were able to boot the live CD successfully? That would show whether the drivers your system needs are present in Ubuntu 6.10. You might also try an earlier or later (development) version of ubuntu, or try kubuntu, since you can always install Gnome after the OS install. If ubuntu continues to give you a hard time, try another popular (i.e., well supported) distro like mephis, pclinuxos, mandriva, etc. The difference between Windows and Linux is much bigger than the difference between distros, and I would hate for your patience to wear out before things start working for you.

  Yours,

    Chris

---

### Post by RageWarp on 2007-01-31
Thanks alot Chris, ill give the earlier verison of Ubuntu a try if get no luck there what distro would you reccomend for an avid gamer, if that has any relevance.

---

### Post by jenks on 2007-02-01
I'm not a gamer myself, mainly I program. I think you would want something known for including all possible drivers (for your latest hardware) and having "non-free" packages for multimedia included. Going on the descriptions I read at [http://www.distrowatch.com](http://www.distrowatch.com) I notice that Mephis and Linux Mint come with the extra multimedia included, so that you don't have to add them, but you might find the review of distros there helpful. My advice is to download several main distros and find one that will install properly. All the distributions use (or can download) the same free software. The main differences, as I understand them, are how the updates for the software are handled, and which programs are included at installation time vs. what you have to download. As far as updates, a nice thing I've heard about Ubuntu is that their update system keeps the software packages compatible and also current. Some other distributions (such as Fedora) take a long time to release packages to ensure that they will be compatible and stable. Usually there is a trade-off between the stability (i.e., lack of bugs) in software and how current it is. The reason Fedora tends to have older packages is that is it based on Red Hat, and the vast majority of Red Hat's market is network servers, which rely on stable (but old) software. You will probably want something relatively current.

  Yours,

    Chris

---

### Post by RageWarp on 2007-02-11
> **RageWarp said:**
> Thanks alot Chris, ill give the earlier verison of Ubuntu a try if get no luck there what distro would you reccomend for an avid gamer, if that has any relevance.

common people hellppp!!

---

### Post by jenks on 2007-02-13
I'm still here. Let me know what your situation is now.

  Yours,

    Chris

---

### Post by cquinones on 2007-02-13
I have the same problem. As soon as I get home I will try to install an earlier version of Ubuntu. I've tried the same CD on multiple machines at work and they boot into the OS just fine. Here are my specs:

Pentium 4 HT 3.0ghz
1.5gb RAM
Asus ATI Radeon x700
SATA HD
Asus motherboard

Is there any way I can get more information from the loader? Are there any logs that I can look at to determine what's causing the hang?

---

### Post by jenks on 2007-02-13
Did you try to install this to your hard drive or are you running it from CD? If it is the install that is failing, does ubuntu run from the CD on your home computer?

  Yours,

    Chris

---

### Post by cquinones on 2007-02-13
This happened while loading the Live CD. I have since installed it on my home machine, using the alternative installer. I am experiencing the same problem. It shows progress when loading the OS, but hangs after the progress bar is finished. I'm starting to think it could have something to do with my graphics card (maybe?). I'm going to try and download 6.06 and see if that works for me. This is my first time trying to install any Linux distro... all I'll say is that it's a bit frustrating, not knowing what's going on. Thanks.

---

### Post by Scruffynerf on 2007-02-13
I am having the same problem.

AMD Athlon 64 2000
1 120GB HDD (IDE), 1 320GB HDD (IDE)
GEforce 6800GT 512MB
2GB RAM

Running from the LiveCD works for a short while, then permanently hangs. Have to pull power to reboot. Am running the 6.10 x386 version. AMD x64 also borks. As does Kubuntu.

Install hangs at 34% after partitioning. On all three of the above versions.

One thing to see - from the Live CD, try doing a memtest x86. 

My memory showed a lot of errors (>1000), although apparently this can be common on Athlons. Not sure if this could be the cause. I'd be surprised if a linux distro could not run when an XP Home can run fine. Perhaps 6.10 is very particular about it's memory mapping?

---

### Post by Scruffynerf on 2007-02-13
> **jenks said:**
>  I notice that Mephis and Linux Mint come with the extra multimedia included, so that you don't have to add them, but you might find the review of distros there helpful. 
    Chris

FWIW, looking at the forums over at MEPHIS, the version 6 there is also having critical installer issues.

Similar sounding problem too.

---

### Post by Scruffynerf on 2007-02-13
Perhaps Ubuntu could consider having this as a part of the standard branch?

BadRAM - how to get linux running on bad RAM systems.
[http://rick.vanrein.org/linux/badram/download.html](http://rick.vanrein.org/linux/badram/download.html)

---

### Post by Scruffynerf on 2007-02-14
Bumpity Bump.

---

### Post by fakeh on 2007-02-14
I think I have the same problem, 

I boot from the CD and am greeted by a very good looking Ubuntu screen with options for "Start or install Ubuntu" etc. I want to install so I just hit enter. The progress bar goes back and forth for a bit and then X loads which wasn't what I was expecting as I want to install, not start unless Ubuntu uses an X based installer now (if so, very swanky). The cursor changes to "Wait" or "Loading" or whatever and there it stays with a patented Ubuntu beige background. I'm wondering if I missed the whole installation step and it's trying to boot like a live CD?

Anyway, Ctrl+Alt+F4 doesn't show any errors and syslog complains only of not being able to get a DHCP address, which is expected on this system at present.

I have an amd64 3000, 2gb of ram, ATI Raedon 9600, SATA HDD, nVidia 2 chipset and Gentoo is already installed.

Thanks in advance for any help give,
Dan.

---

### Post by jenks on 2007-02-14
I tried searching the forum for other threads like this one. Searching titles for "troubleshooting"  didn't help, but "installer freezes" turned up a few other people having the same problems. There were a few suggestions, like using the "acpi=off" and "nosplash" boot parameters, but what seemed to actually work was to resort to an older version of Ubuntu (6.06). There was very little progress on decent troubleshooting methods, other than using Ctrl-Alt-F4 to get a text console and looking at log files, if this even works. Not many experts replied.

  Yours,

    Chris

---

### Post by Scruffynerf on 2007-02-14
FWIW, i've found that the Ctrl+Alt+F4 doesn't work. When my system freezes, it really freezes.

Have to power off from the wall power point in order to re-boot.

---

### Post by secretspicy15 on 2007-02-14
> **fakeh said:**
> I think I have the same problem, 

I boot from the CD and am greeted by a very good looking Ubuntu screen with options for "Start or install Ubuntu" etc. I want to install so I just hit enter. The progress bar goes back and forth for a bit and then X loads which wasn't what I was expecting as I want to install, not start unless Ubuntu uses an X based installer now (if so, very swanky). The cursor changes to "Wait" or "Loading" or whatever and there it stays with a patented Ubuntu beige background. I'm wondering if I missed the whole installation step and it's trying to boot like a live CD?

Anyway, Ctrl+Alt+F4 doesn't show any errors and syslog complains only of not being able to get a DHCP address, which is expected on this system at present.

I have an amd64 3000, 2gb of ram, ATI Raedon 9600, SATA HDD, nVidia 2 chipset and Gentoo is already installed.

Thanks in advance for any help give,
Dan.

If your only problem is that its booting into the live cd version instead of installing, you don't have a problem at all. You boot into live, and then double click the install icon that is on the desktop (probably the only icon on the desktop). This starts the installer. If there are any hangs, try just waiting. I know that sounds silly, but when i installed there were pretty long periods with  seemingly no activity. I just got up and walked away, got a snack, watched some tv, etc before returning, and lo and behold it had progressed and finished. I hope that was helpful...
TJ

---

### Post by RageWarp on 2007-02-15
without any avail, I've yet to come up with a solution to this problem. Ive tried the i386 version and still the same problem. i was wondering if anyone has the APIC problem that i have too, i have to type in NOAPIC to even get to the ubuntu loading screen if i dont, i get something about my kernel not syncing. anyways im going to try 6.06 and see what i get, but post any additional commands other that NOAPIC that may help me.

thanks.

---

### Post by 1doeish1 on 2007-02-15
I have installed Ubuntu on my machine-no problem, smooth install, so I know it is possible. My boyfriends computer differs with problems as stated above. He has a ASUS A8n5x Motherboard; an AMD Opteron 146 processor; SATA 160 GB Seagate Barracuda Harddrive, fresh & Clean; 768 MB 0f RAM and an ATI Radion X850XT vid card. I went through the Hardware compatibility list and found that Ubuntu will install on a system such as this but w/errors that the "noapic" and "nolapic" commands should fix. I ran the commands after entering F6 @ the boot menu, (Start/install Ubuntu, etc. . . ), did not work. I tried Kubuntu 6.10, Kubuntu 64bit and Kubuntu 6.06, all fail to load the OS. He thinks I am nuts and wants his windows back. ACCKKKKKK! Please can we find a solution?

---

### Post by RageWarp on 2007-02-15
that seems to be the exact problem Im having, a fix would be much appreciated

---

### Post by freebirdwil on 2007-02-15
I experienced the same type of problem installing amd64 version of 6.10 "Edgy".  I installed 32-bit w/o problems, but want the 64-bit to use my AMD Turion 64 X2 processor.  LiveCD will not load, I get the "kernel panic - not synching, etc, etc" freeze.  I used F^ options to add no apic to install and it worked fine (did pause and fiddle forever but I just waited it out).  It's working fine now but what did I disable with :no apic" and how do I determine if I am using the dual core processor in 64 bit mode or not?

                            thanks... freebirdwil

Averatec 2370, 1 GB, 100G HD, nVidia, PCI Express

---

### Post by jenks on 2007-02-16
These are frustrating problems, especially since I haven't seen any good general answers in the forum yet. My main experience is with Debian, which also happens to be the distribution that Ubuntu is based upon. The ubuntu documentation says, "As a community, we choose places to diverge from Debian in ways that minimize the difference between Debian and Ubuntu." I've seen procedures to convert a debian system to a ubuntu system, although I haven't tried them. The main thing I've heard about the difference between debian and ubuntu is that ubuntu distributes the package versions differently, in a way that makes the desktop applications more stable, and that debian users who switch to ubuntu or kubuntu are happy with this change. Personally, I've been very happy with debian, and the installer works very well. Two things debian is known for is installing on many different kinds of hardware (12 different processor architectures), and being provided in many different languages. Come to think of it, I can't remember a single machine that I have been unable to install debian on. Of course, there has been hardware without driver support after some installs, but that would have happened with any distribution. The installer has always been text based, which I think is a plus here.

  So what I suggest is to download the debian testing (Etch) installer (about 130 MB) from:

[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-netinst.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-netinst.iso)

and burn it to CD. Unlike ubuntu, this installer only contains the essentials to get debian booted, and then the apt packaging system (the same one used by ubuntu) is used to retrieve the remaining packages over the network and install them. I like this procedure better because you don't have to download packages you don't want (in the installer isos) and you get the llatest packages as you install. The downside is that you can't run a live CD. If you would like to do this, let me know if you encounter any problems at all, because I've found the installer very flexible. Also, I've found the benefit of debian vs. ubuntu to be very small compared to the benefit of no linux vs. linux, and you may be happy enough with debian to stay with that. If you want to switch to ubuntu later, it seems to be possible (see [http://www.linuxquestions.org/questions/showthread.php?t=487673)](http://www.linuxquestions.org/questions/showthread.php?t=487673)), and I'll look for specific methods if anyone gets that far.

  Yours,

    Chris

---

### Post by RageWarp on 2007-02-16
Alright ill give teh Debian a shot. I'll post any problems if i encounter them.

thanks again, 

ryan

---

### Post by freebirdwil on 2007-02-16
Debian installer may be a good solution, but for me I will stay with Ubuntu as I have used  it before on other systems and as a general newbie to command line use I prefer the graphical GUI at this time.  I would still like to know what precisely using "noapic" option at install does as opposed to not using it and how I can check whether both processors (64 bit) are being taken advantage of.  I certainly appreciate the users of these forums, especially for their general patience with Linux newbies.

                                       Best regards... freebirdwil

---

### Post by freebirdwil on 2007-02-22
No Answers, Oh Well... Poof

---

### Post by broy55 on 2007-02-22
I had a similar problem with my Inspiron e1505 laptop. I could move the mouse around but couldn't click on anything. Never figured out the problem so I gave up.

---

### Post by p1r0 on 2007-02-22
Hi,
i had the same problem installing Ubuntu 6.06. 
This is not exactly a solution but may be it helps, here is the link to my original post:
[http://ubuntuforums.org/showthread.php?t=333436]("http://ubuntuforums.org/showthread.php?t=333436")

---

### Post by jenks on 2007-03-02
I came up with two more suggestions:

  1) Try installing Feisty Fawn. I know it's still the Alpha version, but with the release only about seven weeks away, and glaring problems shouldn't remain long. I just upgraded to it today and haven't had a problem yet.

  2) Put the live CD into your Windows partition. This is a new way of using ubuntu, and should be a much less painful way of running Ubuntu than running it off CD, without the actual partitioning + installation process. See:

[http://wiki.ubuntu.com/install.exe/Prototype](http://wiki.ubuntu.com/install.exe/Prototype)

  Yours,

    Chris

---

### Post by nexus2xl on 2008-01-13
Hello everybody, I've been  a user of Gentoo for 4 years and have recently been trying ubuntu (as I'm downright sick of compiling). Anyways, I've solved this issue. This issue seems to apply to other ubuntu based distros and even gOS.

This issue is caused by a combination of bad RAM and a failing /etc/X11/xorg.conf

You are unable to tell you have failing ram blocks as the video doesn't load.


1. Pull the ram chip with bad blocks. It causes ubuntu to hang; giving several thousand "bad block" and memory read errors (which you cannot see as the xserver is failing).

2. Boot from CD and purposely fail the xserver by starting with the "vesa" video driver by using the "safe graphics option" at boot.

3. After ubuntu loads and the xserver subsequently fails, Ctrl+Alt+F2 (to go to a terminal).

4. Ctrl+Alt+Backspace approximately 6-7 (successful) times to get gdm to fail.

5. sudo killall gdm (this will stop gdm from starting again in 2 minutes)

6. sudo dpkg-reconfigure xserver-xorg (correctly enter in all requested info; the correct graphics driver and the PCI port the card is plugged into [it will be in a _:_:_ format and can be found by reading xserver errors]. Choose not to use the frame buffer.

7. sudo gdm (to start up the default install).


[email]nexus2xl@gmail.com[/email]

---

