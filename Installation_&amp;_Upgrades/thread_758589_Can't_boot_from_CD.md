---
title: "Can't boot from CD"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by Raquel Domage on 2008-04-18
The machine is a workstation with AMD Athlon X2 4400+ with 4GB memory &  ATI X700 video card. It runs Vista currently, but want to set up dual boot with Ubuntu. The mobo is a DFI LANPARTY UT nF4 Ultra-D. Using the ubuntu-7.10-desktop-amd64.iso.

Problem: I shove the CD into the drive, it boots from the CD, brings up the initial menu (w/Logo & with the F key options along the bottom). I hit Enter, I get a couple of lines of text output near the bottom of  the screen, but after that, the screen goes dark and a moment later the monitor goes into power save (no signal) mode.There's no other visible output message.

I tried changing VGA to 640x480x16, but didn't help. I tried taking out the 'quiet' option from the default startup command (F7?) to no avail. I verified the ISO image and my Dell laptop boots the CD OK.

So, how to tell where it's having the issue? It's not sending out messages, so I'm stumped as to the exact issue here.

Thanks,
RD

---

### Post by dstew on 2008-04-18
Do a CD integrity check first. It could be the Dell doesn't load a file that the AMD needs, which could have an error in it. If it checks out OK, use the F6 key to boot in Safe Graphics mode. If it still doesn't work you can use the F6 key to try various boot options. Commonly used options that help in some cases are **acpi=off**, and **noapic nolapic**.

If none of that works, consider installing with the Alternate Install CD. It installs the same Ubuntu desktop using a text-based interface that is easier on the hardware. You get it from the Ubuntu download page, just check the box below the Start Download button.

---

### Post by Raquel Domage on 2008-04-19
Thanks. I tried all the options acpi=off, and noapic nolapic, but none helped. 

So... I installed successfully with the Alt CD image (x64), but now that installation won't boot from the hard disk and is showing the same failure behavior as the boot CD did in my first post (monitor turns off as if no signal is present).

The box does boot in recovery mode and I was able to start X successfully from the command line (by typing: X<enter>). 

So I'm at a loss as to what's happening. The unsuccessful boot does not appear to be logged in /var/log so I have no clue what the problem is or what step in the boot process the issue is occurring.

Thanks for the help.
RD

---

### Post by Maintech on 2008-04-19
Try booting with the option nomsi or pci=nomsi. I had the same issue. That cured it. After using it to boot the live disk I installed then when I rebooted it went back to the same issue. In other words, it wouldn't boot. I edited the boot line in grub and added nomsi there and saved it. When I booted it came right up. A lot of these new motherboards have this issue. It took me months to find the correct boot command.

---

### Post by Pumalite on 2008-04-19
Use Envy to install the driver for your card.: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Raquel Domage on 2008-04-20
I think I got it figured out. When I removed the 'splash' default boot parameter, it booted up fine.

---

