---
title: "Configuring using Live CD, then transferring settings on install"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Saiing on 2012-04-27
We have an old machine running Ubuntu 6.06 Dapper Drake.  It came out of LTS last year and so has been running unpatched and is potentially becoming more vulnerable as the months pass.

It's one of those machines that no one has dared touch, because it runs certain legacy in-house applications that are critical to our business.  It also has a quite a lot of customization, uncommon package installs and configurations.

I have one weekend in order to upgrade it (the machine needs to be back up and running on Monday morning).  As a safety precaution, I was considering using the 12.04 Live CD (perhaps on a usb stick) to set things up and configure what we need.  My understanding is that you can download packages and configure stuff even in a live CD environment.  And then once I was happy that everything was running smoothly, duplicate this exact setup to the hard drive of the machine.

To cut a long story short, is it possible for the Live CD environment to be exactly duplicated to the hard drive in this way, or will it just wipe all my previously configurations and changes the moment I do the install?

The point of doing it this way was so that if I screw things up and I'm not ready to go by Monday, I just reboot the machine back into its currently installed 6.06 and can continue the Live CD work the following weekend.  But I don't know if it's even possible to do it this way, or whether the Live CD can handle this kind of demand.

---

### Post by techsupport on 2012-04-27
> **Saiing said:**
> I have one weekend in order to upgrade it (the machine needs to be back up and running on Monday morning). .

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

Ask them what they recommend. They might have something that can do exactly what you want very easily too.

Hiring someone to help you with something like that would probably cost about 400 US Dollars.  If you want that running on Monday morning without any (zero) problems.

---

### Post by oldfred on 2012-04-27
I had just built my computer and my first Ubuntu was 6.06. But my computer was one the first to boot with USB. Many about that time do not. So does your computer support booting from USB?

If so then by a new 16GB flash drive and do a full install to the flash drive. Do not do a liveUSB install as that is not updateable. Persistence will let you save some files but it does not change the base install as it still is the CD image for installing. I have a full install of 12.04 alpha to test on my laptop. I expect to do a new full install shortly to the flash drive. I have it in a 8GB partition with 8GB just for data, mostly ISO for installing or repairing systems that I directly boot with grub2's loopmount feature.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Some settings that make for a better flash drive install may not be best for a full install to a hard drive.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by Saiing on 2012-04-27
Yes, similar to yours it was one of the first machines we got that supports usb boots.  Doing a full install on a usb sounds like a much more sensible idea.  Don't know why that didn't occur to me before.  I guess I'll need some kind of disc imaging utility to copy the image from the usb stick to the main drive, but I think I can probably figure that out.

Thanks for the help.

---

