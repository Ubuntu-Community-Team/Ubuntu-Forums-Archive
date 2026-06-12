---
title: "Lucid NVIDIA driver update fail"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by oohbuntoo on 2010-05-05
I've been running Lucid since it dropped.  Decided to upgrade my NVIDIA 6600gt graphics card to the newest driver I found at the website.  Installation went flawless.  But after reboot, I got this:

**[SIZE="4"]Ubuntu is running in low-graphics mode[/SIZE]**

The following error was encountered.  You may need to update your configuration to solve this.

(EE) May 05 12:24:17 NVIDIA(0): Failed to initialize the NVIDIA
kernel module.  Please see the
(EE) May 05 12:24:17 NVIDiA(0): system's kernel log for
additional error messages and
(EE) May 05 12:24:17 NVIDIA(0): consult the NVIDIA
README for details.
(EE) NVIDIA(0):  ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

I have no idea what to do at this point!  HEELLPPP

---

### Post by oohbuntoo on 2010-05-05
Let me add the driver just installed:

**[FONT="Arial Black"][COLOR="DimGray"]195.36.24 Certified[/COLOR][/FONT]**

---

### Post by Jose Catre-Vandis on 2010-05-05
What kernel version are you on? I just upgraded to 2.6.32-22-generic and it killed my nvidia driver

---

### Post by oohbuntoo on 2010-05-06
> **Jose Catre-Vandis said:**
> What kernel version are you on? I just upgraded to 2.6.32-22-generic and it killed my nvidia driver

I am running 2.6.32-21-generic.  There's got to be a way to get my drivers back up and running.

---

### Post by YuiDaoren on 2010-05-06
The update to 2.6.32-22-generic killed my nvidia drivers (195-36-24) too.

The drivers installed by jokey-gtk (reported as 195-36-15 in NVIDIA X Server Settings) seem to still work. Something to fall back on while this is sorted out.

You can always use GRUB to boot to the older kernel if you need to use 195-36-24, I suppose. Assuming you have the older kernel.

---

### Post by oohbuntoo on 2010-05-06
> **YuiDaoren said:**
> The update to 2.6.32-22-generic killed my nvidia drivers (195-36-24) too.

The drivers installed by jokey-gtk (reported as 195-36-15 in NVIDIA X Server Settings) seem to still work. Something to fall back on while this is sorted out.

You can always use GRUB to boot to the older kernel if you need to use 195-36-24, I suppose. Assuming you have the older kernel.

I ran through the upgrade process again and everything is working fine.  However, I am deathly afraid of rebooting.  If I reboot I am going to get the "you are running in low graphics mode" error again.  Then I will have to do the upgrade process again.  Luckily my suspend feature still works.  SO I should be good until this driver's issues are solved.  

You're right though.  I was utilizing nvidia driver 195-36-15 with Karmic flawlessly and even after upgrading to LUcid 10.04 all was calm in Whoville!  lol...

Moving forward...

However, I am clueless as to selecting a kernel, finding out if I have more than one kernel, etc.  If you could shed some light on how you go about selecting a kernel that would be awesome.  I will search the forum here also, but, considering you are experiencing an identical issue, your insight might be the most expeditious.  This weekend I am going to re-install the 195-36-15 driver.  If that goes well, I will just wait until I get word that driver 195-36-24 is fixed.  Thanks!!

---

### Post by Jose Catre-Vandis on 2010-05-06
See [here]("http://ubuntuforums.org/showpost.php?p=9249626&postcount=16") for my fix for this problem

---

### Post by oohbuntoo on 2010-05-07
> **Jose Catre-Vandis said:**
> See [here]("http://ubuntuforums.org/showpost.php?p=9249626&postcount=16") for my fix for this problem

[COLOR="DarkOrchid"]That does sound straight forward.  I'mma bookmark that link and utilize it at my next reboot, which hopefully will be never!  lol

Thanks a lot 'cuz this was drivin' me bananas B!!!![/COLOR]

---

### Post by oohbuntoo on 2010-05-08
> **Jose Catre-Vandis said:**
> See [here]("http://ubuntuforums.org/showpost.php?p=9249626&postcount=16") for my fix for this problem

Dude you rock 'cuz this saved my life.  10.04 without the drivers is just not the business.   Once again, thank you so much for posting this fix.  Ahhhhh, Lucid is great now  !!!! ):P

---

### Post by casals on 2010-05-09
Installation completely hosed. 

Started with a well-functioning 8.04 installation on a fairly old machine (Athlon 3200) with an Nvidia 5200fx card. Clicked in Update Manager to start upgrade to 10.04. Message somewhere in there about Nvidia driver. When done, boot leads to regular splash screen, then regular home user account, but screen/keyboard completely unresponsive. Booting in recovery mode printed a lot of error messages too fast to read, I think about video driver, then screen blank, whole system completely unresponsive. Booting to the prior kernel very early on complained about a /dev/blahblah missing and went into the ash shell. 

Machine able to run XP (had to boot from my Ubuntu 8 cd to fix grub). 

Any suggestions? I can just wipe the whole thing and start over with 8.04; burn a 10.04 cd; or somehow fix what I have?

(Doesn't look like any prior kernel works: there's an error about finding the monitor. Not an issue about a mounted usb volume, even though there probably was one when I did the upgrade, since mounting it again doesn't help.)

---

### Post by herveb on 2010-05-09
didn't work for me unfortunately

same sort of error message, using kernel 2.6.32-21 (I think). Maybe it's because i'm coming from a fresh install and didn't have any nvidia drivers to fall back to

---

### Post by Rim on 2010-05-10
I updated to the latest kernel and it killed my Nvidia driver :(. The whole system seems to be having issues with the proprietary drivers since 10.04. Boot screen goes low res and now the driver failed completely on the latest Ubuntu version of the linux kernel.  

:confused: The Nouveau drier seems to work gr8, but sadly it lacks 3D so i'm very disinclined to use it :(..i need 3D maaan.

PS: since i couldn't fix it i'm on the Nouveau drier now. Hopefully either Nvidia or Upstream or Ubuntu or someone will have a fix for it ready in the updates within a month or so.

---

### Post by dlowerre on 2010-05-10
> **Jose Catre-Vandis said:**
> See [here]("http://ubuntuforums.org/showpost.php?p=9249626&postcount=16") for my fix for this problem

I spent the weekend updating from Hardy to Lucid on a machine that came with Linux (Dapper) when I bought it.  It has NVIDIA hardware and has always worked fine.

As soon as I started the upgrade from Hardy, the NVIDIA driver started failing at boot time.  Picking the low-res option always got me a desktop where I continued upgrading.  This happened for every upgrade.  I figured that by the time I got to Lucid it would work.  Well almost.

But not quite, and that is where your post came in real handy.  See the system was in a weird state where it thought it was running the NVIDIA drivers (Hardware Driver said it was active) but no NVIDIA features would work.  Your simple steps of removing and then re-activating it cleaned up whatever was left of the mess and now I have a very functional desktop that boots correctly and everything.  Thanks for your post.

---

### Post by herveb on 2010-05-12
a set of update has just been release apparently, one of them mention nvidia.

after running the update, I couldn't even install the nVidia driver - when trying to do so nothing seems to happen

---

### Post by krishan404 on 2010-05-12
mine is broken too.. and the fix a few posts earlier doesnt work for me :(

this is supposed to be an LTS release ffs then why does it break nvidia......... :( :( :(

---

### Post by krishan404 on 2010-05-12
what worked for me was manual install of the NEWEST nvidia drivers (190 didnt work)

[http://www.nvidia.com/object/linux-display-ia32-195.36.24.html](http://www.nvidia.com/object/linux-display-ia32-195.36.24.html)

ugly fix, but it works for now. i hope this gets fixed soon so i can use vdpau again

---

### Post by snip3r8 on 2010-05-12
I cant even install the dam driver in lucid,it doesnt like the kernel,help!

---

### Post by doughoist on 2010-05-14
I am now installing Windozzxp because of this very reason. I am so pissed that Canonical can't get their **** together on these graphics issues. my card worked on every release until 9.10 and now you can't even count on Intel graphics working correctly.

I hate windows and I hate haveing to do a long winded windozz install. But lets face it, without good graphics support, Ubuntu sucks.

Puppy linux works, slitaz works, fedora works, 9.04 works, 9.10 and beyound sucks out of the box and it doesn't seem to get any better.

---

### Post by Shooree on 2010-05-15
Just upgraded from Karmic, seem to be having the same bug with my gfx drivers. I had a manual install of 195.36.15 
I downloaded the newest driver from Nvidia and tried to manually run it via console login. However, the installer failed, as well as reported that the older drivers were installed. Lucid says I don't have any drivers installed and none of the two options I have in "hardware drivers" are activated. 

How exactly did you manually install the drivers, krishan404? I tried just "sudo sh nvidiadrivername". What am I missing?

EDIT> found a tut on what I was looking for [here.]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") Will try immediately.

---

### Post by PoHandle on 2010-05-16
I am getting the same graphics error as reported in this thread.  I've found a workaround that seems to fix all graphics issues.  However, the workaround must be performed at every boot. :(

What I do is boot up,
select the low-graphics option from the prompt,
switch to TTY with CTRL+ALT+F1,
stop gdm,
```
sudo service gdm stop
```
and then start gdm.
```
sudo service gdm start
```

For the record, I'm running nvidia-current (195.36.15)

I hope a fix is released for this soon.

---

### Post by rmeu on 2010-05-17
I had the similar problem.

My Kubuntu installation has been upgraded from 9.10 to 10.04.
This process has completed normally and apparently successfully.

Although some days after, the NVidia driver has been updated and then after reboot the X server refused to start.

Following some comment found in this thread regarding incompatibility between kernel and driver, I digged in and found out the reason.

That's indeed an incompatibility but the faulty part isn't the driver but the kernel.

Actually the upgrade process has installed a new kernel but haven't modified the grub's menu.lst and result is that I was running 10.04 with the "old" kernel. So I referenced the new kernel... Et Voilà...

just vi... problem solved.

hope it will help you,

):P

---

### Post by herveb on 2010-05-17
Thanks rmeu - that's quite interesting. Could you explain how to do that for less advanced users?

---

### Post by PoHandle on 2010-05-17
I just checked my grub configuration, and everything appears to be in order.  I am still having this issue.  What makes things more frustrating is the issue changes a bit if I'm running on battery power.  Then, not only will my display driver fail, but my wireless card as well.

I don't know if this helps, but here's the output of **dmesg | grep 'nvidia'**
```
[   17.564614] nvidia: module license 'NVIDIA' taints kernel.
[   21.499827] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   21.502774] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   21.502783] nvidia 0000:00:05.0: setting latency timer to 64

```

---

### Post by reddemon666 on 2010-06-01
Thanks rmeu, that sorted my problem :)
For other users, depending if you have Grub (v0.97 in my case) or Grub 2. Note, Grub 2 has menu.lst replaced by grub.cfg.
To check the version:
```
grub-install -v
```
For grub users:
1. backup menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
2. edit menu.lst
```
sudo gedit /boot/grub/menu.lst
```
3. Enter the reference to the new kernel (2.6.32-22 as of today) by copying and pasting the old kernel reference and modifying the kernel version:
eg (1st two paragraphs with the new kernel version):
[HTML]title		Ubuntu 9.10, kernel 2.6.32-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=/dev/mapper/nvidia_ecaecbhb5 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 9.10, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=/dev/mapper/nvidia_ecaecbhb5 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/nvidia_ecaecbhb5 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/nvidia_ecaecbhb5 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/nvidia_ecaecbhb5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/nvidia_ecaecbhb5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

title		Windows
rootnoverify	(hd0,1)	# use the correct partition of Windows, ofcourse
makeactive
chainloader +1[/HTML]
4. Save and reboot
That should work, good luck!

For grub2 users:
I'm not too sure, but it may be a similar method, but by modifying the reference for /boot/grub/grub.cfg
Although, I don't think it would be a problem as my other computer with grub2 had the grub.cfg updated automatically to reference the new kernel

---

### Post by cespinal on 2010-06-02
> **rmeu said:**
> I had the similar problem.

My Kubuntu installation has been upgraded from 9.10 to 10.04.
This process has completed normally and apparently successfully.

Although some days after, the NVidia driver has been updated and then after reboot the X server refused to start.

Following some comment found in this thread regarding incompatibility between kernel and driver, I digged in and found out the reason.

That's indeed an incompatibility but the faulty part isn't the driver but the kernel.

Actually the upgrade process has installed a new kernel but haven't modified the grub's menu.lst and result is that I was running 10.04 with the "old" kernel. So I referenced the new kernel... Et Voilà...

just vi... problem solved.

hope it will help you,

):P


How did you do this please?

---

### Post by reddemon666 on 2010-06-03
> **cespinal said:**
> How did you do this please?
Hey Cespinal, 
My previous post explains the steps to take

---

### Post by enaction on 2010-06-06
Sounds like I have a similar 64 AMD motherboard with Nvidia geForce card.  First graphics cut-out on install CD and had to use the "nomodeset" work-a-round. Then persistent problem with low graphics mode after grub.  No tweak on the grub worked for me.  The Nvidia geForce fix that finally worked for me was found here: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates).

---

### Post by Inoki on 2010-06-20
What I did was I went into low graphics mode, uninstalled the driver, re-booted, re-installed the driver, re-booted and it worked perfectly.

Since the driver you used to use used to work, it should work again after you re-install it. It's also the recommended driver so it should work.

---

### Post by jalampi360 on 2010-06-20
Seems to me that Canonical doesn't want Ubuntu users to be able to install the latest from NVidia. This sucks because I would like to be able to run the latest drivers. Canonical doesn't keep up with the latest drivers fast enough. I mean it worked fine in 9.10, so why the big switch?

---

### Post by snip3r8 on 2010-06-21
Mabe they are trying to control users the way windows does...

---

### Post by dlowerre on 2010-06-22
Well, here I am once more.  I just installed updates and when my computer was done re-starting, the display configuration had gone all to hell again.  I had to 're-start X' to get my desktop.  Then I had to bring up hardware drivers, REMOVE the nvidia driver, then activate it again. Oh and then I had to re-configure my s-video output.

Now my system seems to be back to normal.

So...I really like me some Ubuntu but it is really hard to assert that anyone who is in any way technically challenged could manage their own system.

---

### Post by andthewicked on 2010-08-07
Seems everyone is having this issue, been doing some reading and nothing for sure, a few do thisis and try this but no definitive answer. My answer is downgrade...now if I could just figure out how.

---

### Post by Soulmaster on 2010-08-08
I have the Nvidia driver version 195.36.24 on Lucid Lynx and after the past few kernel updates I've run:

```

sudo aptitude install linux-headers-generic
sudo modprobe nvidia-current
sudo service gdm restart

```and magically everything is back to normal.  It's slightly modified from the bug fix found here: [https://bugs.launchpad.net/ubuntu/+bug/575997](https://bugs.launchpad.net/ubuntu/+bug/575997).

---

### Post by kent2 on 2010-08-20
Hi-- I'm new to Linux and running a Wintv HVR-1600 card and a Galaxy 210 video card with Nvidia GeForce 210. I've been fighting all kinds of problems and many reinstalls of Lucid. The answer for me was right here. [http://ubuntuforums.org/archive/index.php/t-1009612.html](http://ubuntuforums.org/archive/index.php/t-1009612.html)  
 I am running the drivers that I got by clicking on System, Administration, Hardware Drivers. I have had so many errors I don't recall what they were anymore. Following jumping_snakes edit to the GRUB file did the trick. Many thanks. I hope this helps someone else.

---

