---
title: "Upgrade to Lucid Graphics Problem?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by ThePinkWitch on 2010-05-16
I recently installed Lucid after using Karmic since February and it hasn't gone well. My machine is running EXTREMELY slow and when I close a window it leaves parts of it on the screen. I have flame effects when I close a window and segments are left on the screen as well. The machine is unusable (with Ubuntu) right now. I suspect it's a driver issue although I had no problems with Karmic. I have a Radeon X1650 Pro graphics card. Thanks for any help.

---

### Post by ThePinkWitch on 2010-05-16
The computer is running a little faster now but is still very slow. I have not set up Compiz and have no effects enabled and it's still not running well. No one got any ideas why my computer is running like a pig since I upgraded to Lucid?

---

### Post by wilee-nilee on 2010-05-16
In the terminal, 
```
lspci
``` 
```
lspci | grep VGA
```

Also turn off all the visual effects and see what happens.

---

### Post by ThePinkWitch on 2010-05-23
> **wilee-nilee said:**
> In the terminal, 
```
lspci
``` 
```
lspci | grep VGA
```

Also turn off all the visual effects and see what happens.

Here are the results of the code you gave me. Sorry I took so long I haven't been able to use my computer for nearly a week.

kayte@SuperCow:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
00:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
kayte@SuperCow:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
kayte@SuperCow:~$

It runs fine with no effects enabled but It ran perfectly ok with all enabled in Karmic. Whats changed?

---

### Post by ThePinkWitch on 2010-05-24
anyone?? I could use Compiz with all the effects before I upgraded to Lucid. Any ideas why now I can't use any?? The computer is stuttery and slow when I enable any effects.

---

### Post by ngrieb on 2010-07-24
I'm having the same issue...:

02:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
        Subsystem: Hightech Information System Ltd. Device 3000
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 24
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at e2020000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e2000000 [disabled] [size=128K]
        **Capabilities: <access denied>**
        Kernel driver in use: radeon
        Kernel modules: radeon

pretty sure that statement is the cause...now we just need to find out how to make that "access granted".;)

---

### Post by andthewicked on 2010-08-04
check your video drivers, I'm having the same problem except the whole screen goes blank. I'm really not happy at all with the upgrade, I am going to try to downgrade the the orgioanl, I really don't see what is diffrent about it as far as looks I'm sure there is diffrent code running in the background but from what i've seen so far it wasn't worth the 2 hour upgrade. Anyway I had to boot in recovery mode with safe graphics mode, then I check my nvidia settings and it doesn't show its even using it. I've seen a lot of these problems online so probably a dist issue.

---

### Post by ParadoxBlue on 2010-11-23
> **ThePinkWitch said:**
> I recently installed Lucid after using Karmic since February and it hasn't gone well. My machine is running EXTREMELY slow and when I close a window it leaves parts of it on the screen. I have flame effects when I close a window and segments are left on the screen as well. The machine is unusable (with Ubuntu) right now. I suspect it's a driver issue although I had no problems with Karmic. I have a Radeon X1650 Pro graphics card. Thanks for any help.

I have the same graphics card and have the exact same problem with Lucid. Karmic worked just fine with all effects enabled but Lucid is unusable unless all effects are disabled. I enjoy a little eye candy (nothing major) and really hope someone figures out a fix. If I had suspected I would never have upgraded from Karmic. This is progress?

---

### Post by Trevor Burton on 2010-12-05
I have the same problem.
Since karmic was going well, and I didn't want any glitches I held off until now to upgrade to lucid.

I had full effects on in karmic and it was working fine.
Now even "Normal" effects makes the machine unusably slow, so I am on "No effects"
Has anyone solved this yet? Is it a driver problem? Does it need a bug report?

Here's my lspci etc.
```

lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0a.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
02:00.1 Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)

```

With no effects enabled, the machine is fine, but I like the full effects, so if you know how to get them back, I'd appreciate knowing too!

Trevor

---

### Post by efflandt on 2010-12-05
> **ngrieb said:**
> I'm having the same issue...:

02:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
        Subsystem: Hightech Information System Ltd. Device 3000
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 24
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at e2020000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e2000000 [disabled] [size=128K]
        **Capabilities: <access denied>**
        Kernel driver in use: radeon
        Kernel modules: radeon

pretty sure that statement is the cause...now we just need to find out how to make that "access granted".;)Access is denied for that because you did not use **sudo**. (ie, **sudo lspci -v**).

If using default video drivers, simply try adding **nomodeset** kernel boot parameter. [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

I am not familiar with X1650, but nomodeset greatly improved speed in Lucid (eliminated card trails in solitare) and fixed suspend/hibernate issue on a desktop with X1300, and fixed boot glitch with mobile X1300.  Without that glxgears (mesa-utils package) would pause and jerk real slowly.  With nomodeset glxgears was quicker and smooth.

That may have been fixed in Maverick (10.10), because I just booted Maverick iso on USB on the desktop with X1300, and glxgears ran smoothly **without** using nomodeset.

I would not know about graphics issues with proprietary ATI drivers because I do not have any computers that can use those.

---

### Post by Trevor Burton on 2010-12-05
Looks like this is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/544496") which is being worked on.

Also seems to affect Maverick.  

Trevor

**[COLOR="Red"]Edit:[/COLOR]** It seems that this was known about for some time.  In the release notes for Lucid there is [advice on a workaround]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working around bugs in the new kernel video architecture") which disables "KMS" whatever that is, and restores the responsiveness of the graphics.  However, it seems "KMS" is a Good Thing, so hopefully there will be a bug fix sometime.

I followed the workaround, and it restored my graphics responsiveness - can now run my 3D cube just as before.

---

### Post by ParadoxBlue on 2011-01-13
Haven't tried the official work-around but after two months I finally changed the theme from Lucid's Ambiance back to a Shiki colors theme I had been using with Karmic and guess what? I opened up System->Preferences->Appearance and clicked on the Visual Effects tab and I can now set the effects to the 'Normal' setting and I have back all the Compiz effects that I was using under Karmic. It will let me select the 'Extra' setting but after closing appearances and re-opening it I find it reverts back to 'Normal'. Don't know if this setting will allow for the cube or not as I have never tried. The graphics are overall much zippy-er even with the eye-candy effects. Don't use the themes that came with Lucid (Ambiance or Radiance). They seem to be the problem at least on my system and now that I've switched I realize how butt-ugly they are anyway.

---

