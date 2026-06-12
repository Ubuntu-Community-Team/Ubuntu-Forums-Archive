---
title: "Graphic problems when installing 10.04 on laptop (Dell D620)"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swedan on 2010-03-21
Hi,

When I try to install 10.04, from daily builds, the alpha or the beta versions, I get a graphics error that I can't get by. I'm trying to install to a Dell Latitude D620 with NVIDIA based graphic card.

It's the same thing whether I'm installing from a usb memory stick or a cd. And it has been the same ever since 10.04 started to become available as test.

I've also had the same problem with a Fedora 12 version. But not with earlier Ubuntu or Linux Mint 8 for example.

Attached are some images to show the error.

All help is appreciated.

---

### Post by oldos2er on 2010-03-21
Click the 'Report abuse' icon, and ask a mod to move your post to Lucid Lynx testing & discussion.

---

### Post by swedan on 2010-03-24
No one ever seen this problem? None of the boot parameters I've tested it with will work (noapic, nolapic, vga=711).

I'm dying here.

---

### Post by ShadowDragon on 2010-03-24
try booting with "nomodeset".

BTW, which kind of Nvidia graphics card do yo have?

---

### Post by swedan on 2010-03-24
I'll try the nomodeset. I have a NVIDIA Quadro NVS 110M buil-in in my laptop.

---

### Post by swedan on 2010-03-24
Yep, the nomodeset worked in that I'm in at a 1024x768 resolution. I can't increase the resolution, and I suspect that if I install Ubuntu from here, it will still be 1024x768 as max when i reboot. Or do you know something more?

---

### Post by ShadowDragon on 2010-03-24
Well, not really, only know the possible work-arounds... :)

I'm having a bug report running for Nvidia-card with fuzzy-screens where "nomodeset" doesn't work ([Bug #539878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878)) and
someone else is having a bug report running for Nvidia-card with fuzzy-screens where "nomodeset" does work, ([Bug #545470](https://bugs.launchpad.net/ubuntu/+bug/545470)), like in your case.
I suggest you subscribe yourself at latter bug, you'll get notified if there are any information updates. Fixing the problem you're experiencing will involve some time of a developer and I don't have the appropriate knowledge to fix it, so that bug report will be your best shot. Unless some comes by this thread and is able to elaborate on the issue of course.

---

### Post by rps63ifid on 2010-03-24
Another data point on this: I too have a Dell D620 laptop and am seeing identical behavior, although the state my screen is left in when it freezes is way wierder in appearance than your photos. The only way I have been able to boot is with "nomodeset" and I get a very low rez. This, too, is a box that is running LinuxMint 8 without problems and has worked well with previous versions of both LM and U to date.

If I am reading the output of dmesg and lspci under LM correctly, it is currently using the nVidia kernel module 173.14.20 and lspci reports the graphics card as an "nVidia Corporation G72M [Quadro NVA 110M/GeForce Go 7300] (rev a1)".

I've tried taking the "quiet" and "splash" options off the boot string and tried it with "nosplash" on the boot string to see if I can get any additional indication of where in the boot process things go wonky, but it insists on going into the splash stuff... any other thoughts on what I might try?

(I also have access to a newer Dell D630 that boots from the same USB stick w/o any problems, for what that's worth. dmesg indicates that the nouveau driver is being used and it reports the presence of an "NV50 generation card", while lspci shows the card in that box as an "nVidia Corporation Quadro NVS 135M (rev a1)".)

---

### Post by QLee on 2010-03-24
> **swedan said:**
> Yep, the nomodeset worked in that I'm in at a 1024x768 resolution. I can't increase the resolution, and I suspect that if I install Ubuntu from here, it will still be 1024x768 as max when i reboot. Or do you know something more?

If you enter the command xrandr into a terminal, you should get a listing of what resolutions your system thinks it's capable of. Perhaps it is a case of the display not correctly identifing it's capabilities or maybe a driver issue that is being worked on, I think I saw some thread about Dells in the 600 series.

---

### Post by swedan on 2010-03-24
> **QLee said:**
> If you enter the command xrandr into a terminal, you should get a listing of what resolutions your system thinks it's capable of. Perhaps it is a case of the display not correctly identifing it's capabilities or maybe a driver issue that is being worked on, I think I saw some thread about Dells in the 600 series.

It all worked after the nomodeset, then after reboot I installed the proprietary NVIDIA drier and everything works now.

Thanks for the help!

---

### Post by rps63ifid on 2010-03-26
Booting beta 1 from my USB stick with the "nomodeset" option works on the laptop in question; I went ahead and installed from there but I seem to be stuck now...

After installation and restart, I can get grub to show me the list of boot selections, but it won't let me edit the boot string for any of the available choices. I press 'e' as shown in the instructions... and nothing. I press Enter and it goes ahead and boots, but since I haven't had a chance to install one of the nVidia drivers, it appears that it is still using nouveau, so the screen goes wonky and I have to do a hard shutdown.

Any ideas on how to get grub to allow me to edit the boot string so that I can get signed in and install the regular nVidia driver?

Thanks..

-- 
/ron

---

### Post by ShadowDragon on 2010-03-26
Boot a live session, mount your internal disk and edit the grub-file on your disk as you wish.

---

### Post by zeroandone on 2010-03-26
I have the similar problem on my Dell laptop. It worked all right until I upgraded to Beta 1 via Update Manager. Now, I can't login, because screen will become fuzzy and just stop there.

How do I use "nomodeset" to boot?

Thanks,

---

### Post by rps63ifid on 2010-03-26
@shadowDragon: Thanks for the response... after editing and saving the grub configuration file from the hard drive, will I need to do anything else before rebooting? It seems like in the distant past there was another step that had to be taken after editing that file, but I could also be remember a distribution based on LILO...

---

### Post by ShadowDragon on 2010-03-26
@zeroandone & @rps63ifid:
1) Open the file /etc/default/grub with sudo rights

2) Edit the file by changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
into
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

3) Safe the file

4) Run the updater:
sudo update-grub

5) Reboot

---

### Post by zeroandone on 2010-03-26
> **ShadowDragon said:**
> @zeroandone & @rps63ifid:
1) Open the file /etc/default/grub with sudo rights

2) Edit the file by changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
into
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

3) Safe the file

4) Run the updater:
sudo update-grub

5) Reboot

The problem is the screen displays "fsck from linux...." and then becomes completely fuzzy, I can't see anything and can't log in.

---

### Post by ShadowDragon on 2010-03-27
@zeroandone: Do you have a Nvidia card? If so what driver are you running, nouveau (open-source) or nvidia (closed source)? Nouveau tends to make your screen fuzzy, since the support, at this moment, it will change in the future, is not a good as that of the closed one.

---

### Post by rps63ifid on 2010-03-27
> **ShadowDragon said:**
> @zeroandone & @rps63ifid:
1) Open the file /etc/default/grub with sudo rights

2) Edit the file by changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
into
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

3) Safe the file

4) Run the updater:
sudo update-grub

5) Reboot
@shadowDragon: Thanks again for your help on this. I had already dropped back and reinstalled Linux Mint 8 on this laptop, then installed 10.04 next to it from the USB stick (previously, I had just dropped 10.04 on top of Linux Mint, so it was the only OS on the box). Oddly, this time grub allowed me to edit the bootstring for 10.04, so I could add the "nomodeset" option to the boot string on the initial reboot after installation. At that point, I was able to install the proprietary nVidia drivers and I'm back to full res and desktop effects.

About the only side effect of this approach I've seen is that the boot screen (and shutdown screen), although purple, obviously is not the really nice one... it looks like it's running in text mode at 640x480... but it works and my desktop is definitely back to where I would have expected.

Thanks again for your help.

---

### Post by ShadowDragon on 2010-03-28
@rps63ifid: If you were able to install the proprietary nVidia drivers and removed the nouveau drivers, you should try to boot without the "nomodeset". The workaround is only intended for the nouveau drivers; with the propreietary nVidia drivers everything _should_ work without the "nomodeset" and you should even have a nice purple splash screen. So give it a shot and let me know how it went. If it doesn't work out, you can still add the "nomodeset".

---

### Post by rps63ifid on 2010-03-28
> **ShadowDragon said:**
> @rps63ifid: If you were able to install the proprietary nVidia drivers and removed the nouveau drivers, you should try to boot without the "nomodeset". The workaround is only intended for the nouveau drivers; with the propreietary nVidia drivers everything _should_ work without the "nomodeset" and you should even have a nice purple splash screen. So give it a shot and let me know how it went. If it doesn't work out, you can still add the "nomodeset".
@shadowDragon: I should have been a little clearer in my follow-up. After installing Ubuntu next to Linux Mint, I was able to edit the boot string within grub in order to boot Ubuntu with the "nomodeset" option on the initial restart of the system after installation -- something I was unable to do previously when I had overwritten my existing LM install with U. I then installed the nVidia drivers and everything worked fine, except (as I indicated) for the boot/shutdown screens not being the nicer looking ones. As a result, I never actually had to go through updating the grub configuration file and regenerating the grub menu.

Something else I noticed was that after running the update manager and getting several hundred package updates, I am back to the nicer (albeit clearly lower res and low color depth) boot and shutdown screens.

---

### Post by zeroandone on 2010-03-31
@shadowDragon: This is how I did finally:
1. Install Ubuntu Beta 1 from scratch with nomodeset option (hit F6 when menu shows up)
2. Follow your instruction to add nomodeset in grub

The only problem is that some screens are distorted as this thread mentioned [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406), but I can live with it. The strange thing is in Ubuntu 9.10, I solved the distorted screen issue by using nomodeset, but no luck in 10.04.

Thanks,

---

### Post by ShadowDragon on 2010-03-31
You're welcome. If I may ask: what driver are you running now? Nouveau or Nvidia?

You can find out by running
```
dmesg | grep -i 'nouveau'
```
or
```
dmesg | grep -i 'nv'
```
and see which one gives the most reasonable output. :)

---

### Post by zeroandone on 2010-04-02
The first one does not give anything.

The second one gives some output which I have no clue about it:

```

0.040013] ftrace: converting mcount calls to 0f 1f 44 00 00
0.642068] rtc0: alarms up to one day, 114 bytes nvram

```What does it mean?

---

### Post by zeroandone on 2010-04-02
I updated my PC this morning and found out that the Visual Effect is set to Normal. I have never been able to change Visual Effect on this PC since the first day of my Ubuntu days, every time I try to change it to Normal, it gives me an error. There must be something changed in the video card driver that enables the Visual Effect. Hooray!

Also, after I found out the change of Visual Effect, I removed "nomodeset" from Grub, everything still works fine and even System Monitor screen is back to normal.

:popcorn::popcorn::popcorn:

---

