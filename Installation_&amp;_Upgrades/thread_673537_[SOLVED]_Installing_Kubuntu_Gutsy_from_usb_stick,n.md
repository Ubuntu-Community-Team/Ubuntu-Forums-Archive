---
title: "[SOLVED] Installing Kubuntu Gutsy from usb stick,not seeing the hard drive"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by debest on 2008-01-20
Hi, folks. I am installing to a small-form-factor PC (no optical drive) and followed the steps from this page:

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Everything went exactly as advertised to the end of the HOWTO.  The computer booted up like a charm from the image I loaded onto the stick.  My problem comes when I go to install on the PC's hard drive.  The installer does not recognize the drive!

I know the drive and the controller on the mobo are both fine: it boots to Windows off the drive just fine if I bypass USB in the BIOS.

I don't think this is a particularly exotic computer: its a Compaq EVO D510 Slim PC.  How do I tell if Ubuntu is not capable of recognizing the controller?  What other reasons could there be for the installer not seeing the drive?

Thanks in advance.

---

### Post by Whiteice on 2008-01-21
first of some computers from the mfg have different hard drives in them. So what you need to do is first check on Compaq's website for the computer you are looking to install ubuntu onto. I know that on for example HP's website you can simply look up the modle number and find the specification's for a pc im sure compaq as a similer search. Once found find the specs and look for the hard drive and possibley get the mfg and modle if listed.

---

### Post by debest on 2008-01-21
> first of some computers from the mfg have different hard drives in them. So what you need to do is first check on Compaq's website for the computer you are looking to install ubuntu onto. I know that on for example HP's website you can simply look up the modle number and find the specification's for a pc im sure compaq as a similer search. Once found find the specs and look for the hard drive and possibley get the mfg and modle if listed.

Thanks for the reply.

The PC is the D510 Ultra-slim desktop PC (specs from the HP website [here]("http://h18000.www1.hp.com/products/quickspecs/11349_div/11349_div.HTML")).  It is about 5 years old, with a P4 1.7GHz processor and Intel 845G chipset.  The hard drive is an old WD ATA-100 20GB drive I pulled from an old system (it has an old copy of Windows 98 on it).

The computer boots to Windows 98 (of course it chokes on finding unexpected devices), so I know that the controller and drive are good.  The issue is whether or not Linux (or Ubuntu) supports it.

Curiously, this PC was certified to be good with Linux, according to [this page]("http://www.hp.com/wwsolutions/linux/products/clients/evod510us-cert.html").

So, to sum up, I have a PC that will boot Kubuntu from USB, but will not recognize the hard drive (it does not show up in /dev).  I suppose that I could download another distro to see if Ubuntu is at "fault", but if anyone else has any other ideas, I'm open to them.

(By the way, when I'm done I'm not really going to be needing to keep this drive.  I'm following [this guide]("https://help.ubuntu.com/community/DisklessUbuntuHowto") to make the PC a diskless workstation that will eventually boot from the network.  The HOWTO mentions that the best way to proceed is to install locally first, then transfer the image to the server so it can be booted from the network.  Then I'll pull the drive back out.  However, any **other** ideas on how I can accomplish this goal are also welcome!)

Thanks.

---

### Post by debest on 2008-01-24
Thought I'd follow this up, in case its useful to anyone....

For some reason, Kubuntu Gutsy wouldn't identify the drive if it was set to "master" even though it was the only hard drive in the system.  As noted above, Windows 98 had no issue with it this way either.  On a lark, I changed the jumper to "cable select", and whaddaknow, it popped up in Ubuntu just dandy!

Something for others to try if they can't get Ubuntu to see a hard disk during install.

---

