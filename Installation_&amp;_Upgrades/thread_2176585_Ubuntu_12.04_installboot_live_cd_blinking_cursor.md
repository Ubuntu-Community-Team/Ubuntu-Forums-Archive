---
title: "Ubuntu 12.04 install/boot live cd blinking cursor"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by cdahl7 on 2013-09-25
I have a computer that I am trying to boot 12.04.3 (64 bit) from dvd. I can adjust boot settings ( I have tried nomodset,etc...) but when I try to run Live without installing I get a black screen with blinking cursor. Consequently, I have a live USB with 12.04.2 (32 bit) that I can boot from (although it takes almost 10 minutes to load). I don't think the problem is graphics card related since I can get computer to run on live usb disk. I have DVD-ROM plugged in on SATA3 A0. I have tried booting in both AHCI and IDE and I get same errors either way. The goal is to install ubuntu 12.04.3 AMD64 and dual boot other OS, but want to at least get live to work first to monkey around a bit before I install. All hardware is fairly new (purchased from new egg May 2013) and should be 64 bit compatible so I don't think that is the issue either. Please suggest additional options to try. I am out of ideas. The motherboard is ASUS Z77 Extreme 4 and boots to UEFI not bios upon selecting <del>

---

### Post by oldfred on 2013-09-27
Only 64bit works with UEFI. A 32 bit version would be BIOS only.

What video card or are you using internal Intel video?

While nomodeset works for many, Intel often needs different parameters. 

What Intel chip?  Should not be Haswell as that is newer, but some of the improvements help the old models. The 12.04.3 64 bit should work
 But Haswell seem to need the very newest kernel & related support software including the Intel drivers that are in 13.10. But 13.10 is still beta, so realize it may break and if consistent breakage, you should report as bug. 

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If Intel:
      
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

If one or the other works please post back which. We often suggest several alternatives, but few tell us what works so we can improve suggestions.

---

### Post by BRKsays on 2013-10-17
Exactly same problem. I can Boot up to Ubuntu 12.04.1. But Since Ubuntu 12.04.2, Ubuntu and its derivatives' 64 bit variants don't boot on my laptop. My Dell Inspiron N5050 doesn't have UEFI crap. I am so at lost as to what to do.

---

### Post by oldfred on 2013-10-17
@BRKsays
Please start a new thread as your issue if for a different system. 
I think Intel made major upgrades for Intel's newest video drivers & systems. But those also helped older systems, but then you may need the boot parameters. If after trying boot parameters above do not work, post new thread.

---

### Post by cdahl7 on 2013-12-03
Sorry for the long delayed response. I have been traveling and just changed jobs so I haven't gotten back to my desktop build for quite some time. I am using a ASUS video card. I have tried disabling and try using integrated graphics but same result. I tried the above options. With the top option, after exiting boot menu, my screen goes to sleep (meaning it is not detecting an input anymore). with the second option i get a blinking cursor with one screen resolution and then the screen resolution changes to a smaller blinking cursor (at a different resolution). Eventually the blinking cursor stops blinking and nothing happens. If I just try to 'install' ubuntu without changing any settings, I get a big blinking cursor then screen goes completely black. Just to confirm, I type the above options in the live boot menu by pressing f6, then esc, then typing after the -- , correct?

---

### Post by oldfred on 2013-12-03
Some older Asus needed these type of settings. Comments from others in forum.

>  Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.





---

### Post by cdahl7 on 2013-12-03
[LIST]
[*=left]See system specs below. As noted, I am booting from UEFI not BIOS so I am not sure above comments apply. Please comment on my last comment regarding correctly changing settings you previously recommended. Thank you
[*=left]
[*=left]1 x [ASRock Z77 Extreme4 LGA 1155 Intel Z77 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157293")
[*=left]1 x [Intel Core i5-3570 Ivy Bridge 3.4GHz (3.8GHz Turbo Boost) LGA 1155 77W Quad-Core Desktop Processor Intel HD Graphics ...]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115233")
[*=left]1 x [ASUS ENGT430 DC SL/DI/1GD3 GeForce GT 430 (Fermi) 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121448")
[/LIST]

---

### Post by oldfred on 2013-12-03
I thought it was Asus. 

 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)


 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

### Post by cdahl7 on 2013-12-05
I switched SATA ports on my ROM drive and now i can boot LIVE CD. Thank you! Will report back if I have any further problems with installation.
Thank you again, this has been a pain!
-Chris

---

