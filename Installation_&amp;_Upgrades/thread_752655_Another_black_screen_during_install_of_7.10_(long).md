---
title: "Another black screen during install of 7.10 (long)"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2008-04-11
I have read quite a few threads regarding black screens during install, and none of the seem to quite fit my machine, but a lot of them are close.  First, the machine:

Pentium 4 2.4Ghz processor
Intel D845 motherboard
1gb ram
drive 0 is my windows XP drive and it works just fine
drive 1 is the drive I am trying to use for Ubuntu
Graphics is nVidia GeForce 5200FX
Monitor is CTX 17" crt
Using onboard network and sound.
Using Ubuntu Livecd which I have run the checker against.

Now, At one point I had Ubuntu installed on this machine, but that is another very long story.  But I had it all working except for one thing.  when I initially installed it, there was a Riva TNT2 AGP graphics card in the machine.  It was ok, but I was not able to see all the fancy desktop goodies so I put in the GeForce 5200 (pci bus).  I changed the bios so that the PCI was the primary display.  After fighting this for a couple of days, I had it working using the GeForce but ONLY as long as the TNT2 was installed.  The TNT2 did not have to have anything connected to it, but it HAD to be installed.  Take it out and I am where I am now.

Which is the black screen.  I re-arranged the machine so that only the Windows XP drive (IDE primary master) was installed and then I did a fresh install of Windows XP.  No problems at all.  Then I added the Ubuntu drive (IDE Primary Slave) and have been trying to install Ubuntu there.

For starters, I tried to install over the "old" Ubuntu installation but that did not work.  Then I booted XP and created/formatted a NTFS partition on the Ubuntu drive and that did not work.  And I have tried installing with no partition on the drive.  Everything has the same result.  Black screen.

I have read many of the threads regarding this and have tried several of the options.  I have tried removing the "quiet" and " Splash" operands from the command line that starts the install (using F6).  I have tried using many different screen resolutions using F4.  Combinations of the two.  Safe graphics mode.  And turning off apci, etc.  Nothing works.

When turning off the quiet and splash options I see all the messages flowing by on the screen and the last one is "running local boot scripts".  As soon as that last message is displayed the screen goes black and the computer is totally hung.  No key stokes work including CTL-ALT-F1 (or F2), and even CTL-ALT-DEL does nothing.  The power button doesn't do anything either unless I hold it in for 4 seconds and then the machine powers down.  This is what seems to make my problem different from everyone elses.  The machine is completely hung.

There is one thing that may be at the root of all this.  The motherboard SUPPOSEDLY has onboard graphics.  There is the d-15 connector for a monitor on the motherboard, but there is NO option to enable/disable it in the bios.  But I have run a variety of Windows OS's on this machine including Windows 2000 AS, XP, and Vista (ick!) with no problems.

Sorry about going on so long.  Anyone have any ideas on this one??? 

Wayne

P.S.

---

### Post by twist2b on 2008-04-11
Yea, I had the same problem with my hp tx1000 with nividia graphics aswell.

sadly Ubuntu hasnt added better nvidia driver support.
Heres what you do until they get smart :P

go into recovery mode and type this:
apt-get update
apt-get install nvidia-glx-new (this will install the important driver that makes your display tick, when it black screens its just because it sends information to your screen, but without the right driver, NO INTERPRETATION.
SOOOO after it installs (you might have to type "y" to allow the install
then configure your xserver to use the correct drivers
type:
"dpkg-reconfigure xserver-xorg" (by the way NEVER use the quotes :P)
right away go away from the EVIL nv, to the newly added "nvidia"
keep  going through the steps (DONT CHANGE the keyboard settings, this can make the boot crash, dont ask me why, its really weired. If your using a DELL or HP it will be on pc105. keep it that way.)
once done exit
it will boot now.
If it doesn't PM me. there are other fixes, though this is sure fire.

---

### Post by xeddog on 2008-04-11
Thanks for the reply, but there is no recovery mode.  I am REALLY new to Ubuntu, but if I remember correctly you don't get to recovery mode until you have a completed install.  Right???   I can't even get that far.  This is failing during the initial startup before anything actually gets installed.  

The way I remember this happening the first time was that Ubuntu would boot to the desktop and then there was an install icon that you clicked on to do the actual install.  After that, when you boot there is an option for recovery mode.  But since I haven't installed anything . . .?????

Am I missing something?


Wayne

---

### Post by twist2b on 2008-04-12
I'm sorry, It should install the distro even if GRUB does not work. Though if that is not the case:
I really suggest this:
1. Get Hardy Beta, even though its Beta, trust me its freakishly smooth and runs better then my Gusty does. I had one jockey error that was fixed. after that I have had no problems.
2. Get the alternate CD, under the download section, when choosing what you want, check the box that says something like "choose alternate cd"
That always works :P

---

### Post by xeddog on 2008-04-12
Funny you should mention the beta.  I downloaded that last night and after 4 attempts at getting a good cd that verified clean, I used it to install 8.04.  The installation has gone as smooth as a baby's butt.  I am replying to you using Firefox on my Ubuntu installation.  The installation has already downloaded and installed hunnerds of updates and it even installed nVidia drivers and everything.  I be happy again.

Thanks for you assistance.

Wayne

---

