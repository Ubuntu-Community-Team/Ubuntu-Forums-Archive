---
title: "No Video During Installation"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by starfailure on 2006-08-16
Hi all,
I'm a fairly inexperienced Linux user, but am attempting a [K]ubuntu install on the following:
Athlon 64 3000+ (939 socket) on Asus A8n-SLI Deluxe mobo
Asus x700PRO Radeon 256mb PCI Express video card

I boot from the 6.06 64-bit release and get the Kubuntu menu.

Whether I choose "Install" or "Install in Safe Graphics Mode" or adjust my screen resolution, I always get a blank screen  and my monitor goes to sleep when the install tries to draw X (I assume).  I can hear the startup sound and everything, just no video.

What do I need to do here?

---

### Post by tseliot on 2006-08-16
If you are inexperienced, please use Kubuntu 32bit.

And yes, 32bit operative systems do work with 64bit CPUs.


Now if you want to install Kubuntu please, follow these instructions:

1) Install (K)Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

if it doesn't, repeat step 3 and select the "vga" driver (instead of "vesa"). You might then want to install ATI's (proprietary) driver.

---

### Post by starfailure on 2006-08-16
Just to confirm:

I should use the the "alternate" install iso for 32-bit (NOT alternate for 64-bit and NOT the 32-bit "desktop" iso).  Correct?

---

### Post by avtolle on 2006-08-16
Yes.

---

### Post by starfailure on 2006-08-16
Thank you, gentlemen.  I'll give it a shot.

---

### Post by JayBrook on 2006-08-17
(moved to a reply to tsEliot's post at the top)

---

### Post by JayBrook on 2006-08-18
Buon Giorno (please don't respond in Italiano, I don't understand too much).  Grazie.

--------------------------------------------------------------------------------

I am hoping that this "dpkg-reconfigure xserver-xorg", vesa (or vga), and "reboot" will work for me, but I can't even get to the Recovery terminal prompt.

I have an Nvidia GeForce 6600 video card (Gigabyte GV-N66256DP AGP 8X 256MB DDR), and had to use the "safe graphics" choice on the LiveDVD to get it to display without garbled brown color jumping lines all over the place. I decided to install, did some reading, and set up my partitions with GParted ahead of time and used the alternate TEXT install from the ubuntu 6.06.1 DVD. NOTE: I can only use the live GParted CD if I choose the manual video mode and select VESA (the 24 bit, 1024x768 defaults work fine if I have chosen VESA).

I chose the Text-based install from the DVD so that I could manually tell it what partitions to place everything on. ALL went well, until I removed the DVD and rebooted to complete the installation.

Just as with the default ubuntu or GParted LIVE DVD/CD startups - the screen gave me the same unreadable ubuntu brown themes wiggling bunch of lines. I hit the power switch and it popped me out to a prompt -- but I didn't know what to do so I hit the power switch again. I powered on again and saw the "recovery" menu choice ... but it hung on a line about "IPv6 ... IPv4" ... I powered down and went to bed.

PROBLEM 1: There is NO "safe graphics" choice on the Grub menu when you first reboot after a fresh install.

PROBLEM 2: When I go home tonight, I would like to try your commands above to choose "VESA" -- but will I "magically" be able to get to a terminal prompt this time?

QUESTION: Have I messed up my install by powering down on the first installation boot (and missing whatever it was asking me to do)?

HELP!

I've tried Linux several times over the years on different machines -- and ALWAYS it was a garbled screen issue on install.

Is it REALLY that HARD to get everybody into a safe display mode until they choose a better driver and resolution? 

I noticed on the Freespire LiveCD -- their resolution applet kicks back to your previous settings in 15 seconds if you don't click "Yes" to accept your new choices. I sure hope ubuntu has this fail-safe feature ... IF I can ever get it to boot in readable form.

Thanks for your help.

--------------------------------------------------------------------------------


> **tseliot said:**
> If you are inexperienced, please use Kubuntu 32bit.

And yes, 32bit operative systems do work with 64bit CPUs.


Now if you want to install Kubuntu please, follow these instructions:

1) Install (K)Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

if it doesn't, repeat step 3 and select the "vga" driver (instead of "vesa"). You might then want to install ATI's (proprietary) driver.

---

### Post by starfailure on 2006-08-20
follow-up:
i used the alternate install cd and it wored fine on first use.  didn't have to reconfigure X

---

### Post by JayBrook on 2006-08-21
I also used the alternate install.  I think ubuntu should default to VESA so that we could then adjust it after finishing the install.

NOTE: I was NOT able to get to a command prompt to even TRY the manual re-configuration.  Still dead in the water.

---

### Post by tseliot on 2006-08-21
Are you sure that you can't even boot in **Recovery mode** (you can select it from the grub menu almost as soon as you turn on your computer?

I'm asking you because the Xserver is not started in Recovery mode

---

### Post by JayBrook on 2006-08-21
I use the XP boot menu, which I made a Ubuntu Linux choice for, which then takes me to the Grub menu.  But I don't think that is the issue.

Either the recovery mode has hung on a particular line, or it has produced garbage on the screen when I tapped a key on the MS Wireless keyboard.  I put in new batteries in the mouse and keyboard, so I will try it again and see it it matters.  I wouldn't think so, as the wireless keyboard receiver plugs into the normal KB/mouse ports and should just be seen as a regular KB/mouse.  Anyway, I'll try again and let you know.

---

