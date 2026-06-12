---
title: "How not to install Ubuntu Gutsy"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by abyssius on 2008-02-07
**Background**

After spending many years in the M$ world and then trying Vista, I am finally convinced that Microsoft is fascism. I considered a MAC but Apple seems cultish and similarly [INDENT]proprietary. Therefore Linux, with its free and unfettered OS and software, must truly be computing power to the people. With my new mindset and a spare computer on hand, I enthusiastically embarked on my migration to Linux. 

I began with the following hardware configuration:

[INDENT]AMD Sempron 3000+ CPU
ASROCK motherboard with SiS chipset
SiS AC'97 onboard sound
512 MB DDR RAM
80 Gig Seagate IDE
NEC DVD-RW
nVIDIA GeForce2 MX200
D-LINK DWL-520E PCI Wireless adapter
[/INDENT]
First, I tried several live CD distros, including Ubuntu. I never achieved wireless connectivity or sound right off the bat with any of them. A little research led to the discovery of the ndiswrapper utility for windows drivers. I tried to set up the DWL-520E via ndiswrapper with different distros. I was never able to get the DWL-520E working, even though  ndiswrapper reported that the windows driver was loaded and that the hardware was present. Okay. I replaced the DWL-520E with a DWL-120 USB adapter from my parts bin. This adapter + ndiswrapper worked fine with the SLAX live CD. Confident that I mastered my first command line challenge, I assumed that if the DWL-120 worked with SLAX, it would work with any Linux version.

Next, I selected the Ubuntu 7.10 distro for the hard disk install because I liked the GUI the best, and the name inferred Humanity to Others. What could go wrong?

In the spirit of simplicity, I opted to use the entire hard-disk. The install went smoothly. However, as expected upon boot-up:
[LIST]
[*]no wireless connectivity (D-LINK DWL-120)
[*]no sound (onboard soundcard, SiS '97)
[/LIST]

**Challenge 1 - Connecting to the Internet**

My first task is to connect to the Internet. Ubuntu doesn't detect my USB wireless network adapter. But, I've dealt with this before. Oops. Where is ndiswrapper? It was not installed with my Ubuntu distribution. The wireless troubleshooting guide says run Synaptic Package Manager and install ndisgtk. Okay, but a slight problem, Synaptic Package Manager can't connect to the Internet!

Luckily, I had Internet access via my Windows computer. Since Ubuntu is based on Debian, I searched for ndiswrapper at debian.org. I downloaded ndisgtk (from debian.org) and transferred it to my Linux machine via a usb flashdrive. I double-clicked on the .deb file to install it. Oops. a dependency problem. I need ndiswrapper-utils. Okay. back to the Windows computer. I downloaded ndiswrapper-utils. Oops! I need ndiswrapper-common. Long story short, after all the needed ndiswrapper packages are downloaded and installed, finally ndiswrapper is functional. I run ndiswrapper, iwconfig, ifconfig, dhcpcd, etc, via command line (the only way I knew how to do it). Tip: using Windows Wireless Drivers via the Admin Menu is a lot easier! Anyway, Voila! Internet connectivity! End of challenge 1.

**Challenge 2 - Enabling Sound**

My next problem was no sound (speaker icon marked disabled). However, now I'm online! I followed the very clear instructions in:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting"). 

First, I issued the command:
[INDENT]aplay -l
**** List of PLAYBACK Hardware Devices **** (note no card shown)[/INDENT]

Next, I used the command, lspci -v, which listed my sound source:

[INDENT]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: medium devsel, IRQ 20
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>[/INDENT]

I'm encouraged that Ubuntu detected my audio controller. Continuing to follow the instructions, I checked to see if an ALSA driver for my sound card existed. The closest match I found:

[INDENT]driver: snd-intel8x0
description:  Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
[/INDENT]
Next, following the advice on the ALSA site, I entered the command:
[INDENT]
sudo modinfo soundcore
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 586 [/INDENT]

Returning to the troubleshooting instructions, I entered:
[INDENT]
sudo modprobe snd snd-intel8X0[/INDENT]

No error messages!!! cool.

Next, I entered:

[INDENT]sudo nano /etc/modules[/INDENT]

I added: snd-intel8x0, and saved the file.

I tried aplay again: 

[INDENT]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/INDENT]

Progress! Now aplay shows a sound source!

I reboot the system. The disabled icon for sound is gone! I was able to access the ALSA mixer. Everything looked alright. Nothing muted. However, there was still no sound!

At this point, I confess my patience was running thin. I made the radical decision to rip my SB Audigy out of my windows machine. After all, I'm a Linux-ite now - and soundblasters work with everything. I installed the SB card into the Ubuntu computer and disabled the onboard sound via the BIOS. Wow! Ubuntu knows the SB Audigy. Everything looked good. Oops! no sound. Actually, this one was easy. Back to Ubuntu Forum. Hah! I need to switch off the digital output. I HAVE SOUND!!! I laugh maniacally. End of challenge 2.

**Challenge 3 - Update Computer**

Actually, this shouldn't be a challenge. I'll simply run the Update Manager (done this a million times in windows).

Oops! I get the message:

[INDENT]Not all updates can be installed

Run a partial upgrade, to install as many upgrades as possible.

This can be caused by:
- A previous upgrade that didn't complete
- Unofficial software packages not provided by  Ubuntu
- Normal changes of a pre-release version of Ubuntu[/INDENT]

WTF???

[I]re cause 1: This was my first attempt at upgrading - no previous uncompleted attempt.
re cause 2: I did install ndiswrapper that I downloaded from Debian site (hmmm!). Could this be the unofficial culprit?
re cause 3: I don't think that Ubuntu 7.10 is a pre-release[/I]

Anyway, with no other choice available, I click [Partial Upgrade] to see what happens.

Oops!

[INDENT]Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.[/INDENT]

Panic begins to set in. I go online to report the bug. I search for the problem. Others have seen the same thing. However, bug is not resolved. Okay! I'm feeling that after several hours of effort already, I'm not going to tackle a problem of this apparent magnitude. Challenge 3 failure.

**Challenge 4 - Start Over**

I made the decision to start over from scratch. However, I elected to keep the first install for future reference. This way I can still try to figure out what went wrong with the generic install no-update-possible problem. I download the Ubuntu Studio iso and burn a DVD. Bolstered by all my newfound Linux skills, I install Ubuntu studio to a new partition. I install the ndiswrapper packages as I did before. I ran ndiswrapper (this time using the Windows Wireless manager). Wham Bam - I'm online, but no sound from the SB. Big deal! Turn off the digital output. With this install, I'm fully functional in a relatively short time. It almost seems TOO easy. I sheepishly invoke Update Manager. Wow! 186 updates available -  downloading - installing. NO PROBLEMS! End of challenge 4.

**Conclusions**

In retrospect, I've set-up many Windows machines, and although tedious, it never took me as long as this particular install. And, I have never personally experienced an unresolvable problem with Windows such as the apparent Update Manager bug I encountered with Ubuntu. Having said that, I'm now persuaded that Linux has finally become a viable desktop system. However a complete divorce from windows will not be possible for me until I find a true equivalent to Sony Vegas, which I use professionally. 

I'm especially thrilled by the Ubuntu Forum Community. I was at first leery, expecting to run into obnoxious partisans like those I've encountered too many times in video editing forums. In contrast, the level of expertise and politeness here is truly exemplary. I'm cautiously optimistic that Linux is indeed the promised land. All I need is a Sony Vegas for Linux for me to throw my windows machine away for good.

---

### Post by tact on 2008-02-07
You did pretty darn good!   My first ever install was much less painful (all my hardware was happily supported, detected, and worked, out of the box).   But even so it wasn't long before I decided I needed to reinstall and do things like put /home on a partition all its own etc..

I have reinstalled a few times since, also to try out something new like "whole disk encryption" etc...  

Great work.  All the best.  And you are right the community here in this forum is fantastic.

---

### Post by daengbo on 2008-02-07
One of the most important pre-install steps is to check whether your hardware is fully supported or not. Having a machine with fully available drivers makes the install process a breeze.

If you intend to put Ubuntu on a computer, try running the live CD for a while and find out what issues you have before you install. I prefer to buy pre-installed or buy known working components and build myself.

---

### Post by abyssius on 2008-02-07
You make a good point daengbo. I haven't had to worry much about hardware compatibility since the Win'98 days. Obviously, market forces dictate where hardware manufacturers focus their development efforts in terms of drivers. In this regard, there are millions of  Windows users that wouldn't know what "chipset" means, or even be able to distinguish between the hardware components that comprise a computer. 

Ultimately, the winning desktop computer solution will be the platform that turns the computer into a true consumer appliance.In this regard, windows is a distinct failure. There are so many ways for the no-clue user to get themselves into trouble with Windows, that a cottage industry of "gurus" sprung up for routine rescue of the heedless horde This is where I think Linux can really shine. I'm still a newbie user. However, the OS seems so streamlined once you get it working, it may be far less likely that an unaware user screws up during regular usage. I hope this is the case. I can imagine that a computer purchased with Linux properly pre-installed might well become the first real computer appliance as easy to use as a refrigerator.

---

### Post by coolen on 2008-03-02
My congratulations on sticking with it. Many users have given up facing fewer problems.

My first proper Linux experience was with Debian. I'd tried the Knoppix Live CD, liked it, so I got the Debian discs and installed (net install). Lcukily, I'd read up beforehand, so I managed to find my way around the terminal I found myself stuck in, and after a few days, I had a nice KDE environment. I installed others, played around. I wound into trouble with a dist-upgrade which effectively broke my X server. I spent three days tracking down and removing conflicting packages before I resolved the issue. It was a pain in the ****, but so satisfying to resolve.

Then, I started using Ubuntu. A friend of mine who'd been using Gentoo told me he was amazed at how everything just works, and it's true. There are still holes, some of them pretty embarassing, but on the whole, the situation has improved and is improving remarkably.

---

