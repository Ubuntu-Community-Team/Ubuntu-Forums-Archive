---
title: "Unable to boot from USB installation media (Asus Z97 Deluxe/USB 3.1 &amp; NVIDIA GTX 960)"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by Alex_Dunkel on 2016-05-05
Hi!  I'm a noob.  Though I've used Unix-based systems off and on since 1994, I've never run Linux at home and I haven't done much administration at work.  I can probably get around okay, but please talk to me like I'm brand new to Linux just to be safe.  Anyway, I'm trying to do my first Linux install at home, and it's leaving a very bad taste in my mouth.


First, here's the hardware pertaining to this problem:



[LIST]
[*]Asus Z97-DELUXE/USB 3.1
[*]EVGA GeForce GTX 960
[*]SM951 M.2 SSD (MZHPV512HGL)
[*]Seagate Hybrid Drive ST2000DX001
[*]Seagate STBD6000100
[*]Seagate Barracuda XT ST33000651AS
[/LIST]


To start, I downloaded the Ubuntu 16.04 Desktop (64-bit) ISO and used Universal USB Installer 1.9.6.4 to create a bootable USB drive.  (I also tried using Rufus 2.8 using the "Check device for bad blocks" option.)


When I boot from the drive, I do not get a GUI (boot screen), but I do get a text-based menu giving options to try Ubuntu, install it, perform an OEM install, etc.  When I choose the option to try Ubuntu, I get:


nouveau 000:01:00.0: gr: failed to load frecs_inst
sd 9:0:0:0: [sdf] No Caching mode page found
sd 9:0:0:0: [sdf] Assuming drive cache: write through
usb 3-1: device descriptor read/all, error -110
usb 3-1: device descriptor read/all, error -110
usb 3-1: device descriptor read/8, error -110
usb 3-1: device descriptor read/8, error -110
ata6.00: exception Emask 0x52 SAct 0x0 SErr 0xffffffff action 0xe frozen
ata6: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }
ata6.00: failed command: IDENTIFY PACKET DEVICE
ata6.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 2 pio 512 in
            res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x56 (ATA bus error)
ata6.00: status: { DRDY }


It then hangs completely; keyboard unresponsive.  I have to hold the power button for several seconds to turn the computer off.


Also, I went on to try Linux Mint instead.  I got a different error, but same ultimate result: completely frozen.  It seemed to have problems with nouveau more-so than the ATA bus.


I'd appreciate any help I can get.

Edit: I just tried booting to Fedora from USB, and it also froze.  However, it froze in a GUI, ~75% of the way through the loading icon.  No errors were given.

---

### Post by ubfan1 on 2016-05-05
With NVidia hardware,there are a whole slew of options to try, starting with the "nomodeset" on the vmlinuz line replacing the "quiet splash". edit the "Try Ubuntu" grub bootcommands and add the option. Edit/Boot instructions for this should be at the bottom of the grub menu screen.  Search the forums and askubuntu for Nvidia 960 for additional options if nomodeset does not work.  After you find what works, edit the install boot, then after the install, edit the installed grub, to at least get to a working virtual terminal (ctrl-alt-Fn1) (terminals on 1-6, the gui will be on 7). and add the proprietary Nvidia drivers.  That's a summary, lots more details in various threads/questions, depending upon specific hardware.

---

### Post by Alex_Dunkel on 2016-05-06
> **ubfan1 said:**
> With NVidia hardware,there are a whole slew of options to try, starting with the "nomodeset" on the vmlinuz line replacing the "quiet splash". edit the "Try Ubuntu" grub bootcommands and add the option. Edit/Boot instructions for this should be at the bottom of the grub menu screen.  Search the forums and askubuntu for Nvidia 960 for additional options if nomodeset does not work.  After you find what works, edit the install boot, then after the install, edit the installed grub, to at least get to a working virtual terminal (ctrl-alt-Fn1) (terminals on 1-6, the gui will be on 7). and add the proprietary Nvidia drivers.  That's a summary, lots more details in various threads/questions, depending upon specific hardware.

I've solved the problem.  I would like to say that this reply was helpful.  However, the truth is that it was indirectly helpful.  It forced me to go back, comb not only the forums but also Google (which led me to askubuntu.com).  To summarize quickly for people with the same problem:

_**Connect your CD/DVD/BD player to a SATA connector on your motherboard, not an ASMedia connector.**_  The manual mentions that these connectors can only support AHCI mode (data drives only), though looking at the motherboard only (on a Z97 Deluxe/USB 3.1), there's no such indication that it's anything other than SATA.

Re: ubfan1 -- I had already tried "nomodeset" the night before, but had forgotten to mention it.  After searching, I tried disabling/enabling/forcing UEFI (a.k.a. Secure Boot) and disabling FastBoot... but no luck.  The error messages changed very slightly, though.  The last line I got before freezing was: "ata7: hard resetting link" ... which let me to: [http://askubuntu.com/questions/228927/boot-failure-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/boot-failure-failed-command-identify-packet-device)

Though disheveled, it pointed me back to the manual for my motherboard, where I learned which connectors were ASMedia connectors and that they only support data drives.  It's a good thing I had a couple margaritas in me, otherwise I would have punched the wall...

My one lingering question: Why did Windows 10 (and previously Windows 7) handle this misconfiguration while every distro of Linux I tried failed before I could even load the installer?  In Windows, I was able to rip CDs and play DVDs & BDs without any issues.  I find that odd....  I would love to know why something as half-baked as Windows--out-of-the-box--can handle something so badly misconfigured, while multiple distros of Linux (with all the eyes combing their lines of code) won't let it pass.  But then again, maybe I answered my own question...  Either way, technical or not, I would love an explanation as to how Windows could let something like that pass and--more importantly--function without flaw.

---

### Post by grahammechanical on 2016-05-06
> I would love an explanation as to how Windows could let something like that pass and--more importantly--function without flaw.

Windows pre-installed or installed from an off the shelf purchased copy? The answer is; Cooperation and collaboration between the manufacturer & Microsoft to produce a commercial product that works "out of the box." If they did not do that customers would return the product and demand their money back.

Whatever you think of Windows it does not mean that Microsoft or Apple or Google for that matter are half-baked when it comes to making profit from selling commercial products.

If that machine was sold with Ubuntu pre-installed you would find that still-being-baked Linux would work "out of the box." Commercial necessity & government retail sales legislation would force the manufacturer to make sure the product was of merchantable quality and fit for sale.

Regards

---

