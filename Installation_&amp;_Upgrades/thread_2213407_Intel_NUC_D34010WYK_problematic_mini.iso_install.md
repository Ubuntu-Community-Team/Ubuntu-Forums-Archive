---
title: "Intel NUC D34010WYK problematic mini.iso install"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by pumkinut on 2014-03-26
I checked via search to see if anyone else saw this issue, and didn't find anything.

I just got a new Haswell-based i3 NUC to use as an XBMC box.  I tried using the 13.10 minimal ISO as the install base.  Everything seems to go well, until I get to the drive partitioner.  It will not recognize the 32GB Samsung mSATA drive I have installed.  The NUC BIOS sees the SSD just fine, and a Linux Mint live CD sees the drive as well if I boot into that.  It's just the minimal install routine that doesn't see the drive.  I've rebooted the NUC twice, but still no-go. Any tips or tricks I might be able to try? Or should I try another minimal ISO to see if it works there?

---

### Post by oldfred on 2014-03-26
Do not know why you would have a partition issue.
Is system only UEFI and minimal still only BIOS?
Only 64 bit versions of Ubuntu are UEFI, but you can install that in BIOS mode on a gpt partitioned drive (with parted or gdisk) and then convert to UEFI. You would need to have efi partition to convert and bios_grub to boot in BIOS mode.

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)

---

### Post by pumkinut on 2014-03-26
I've tried it in UEFI mode and Legacy, with identical results.  It's not that the the installer can't see a partition, it can't see the disk at all.  It doesn't show up under /dev when I drop to a shell and search for it, but the USB thumbdrive I'm booting from shows up as /dev/sda and /dev/sda1.

---

### Post by oldfred on 2014-03-26
Operating systems will only work with drives that UEFI or BIOS enumerate. If not seen in BIOS then operating system cannot use it. 
Sometimes there just is a setting to activate or turn on a drive? 
Otherwise check connections and cables or other physical issues.

---

### Post by pumkinut on 2014-03-26
It's an mSATA drive, it only goes in one way, no cables. It's screwed down and both the NUC and a Mint LiveCD see it at it's full capacity, so it's being enumerated by the NUC's hardware.

---

### Post by oldfred on 2014-03-26
The threads I posted above seem to say the NUC have a lot of internal settings.

Not sure why one Linux system would see drive and another would not. Underlying system tools should be the same, except some version differences. 

Have you tried anything other than the mini? And what version? You probably need to most current version.

---

### Post by pumkinut on 2014-03-26
As I posted in my OP, I am using the most current minimal install ISO, i.e. 13.10 (not sure if it's 32b or 64b though).  Also, as I've said, the Mint Live CD sees it, and Mint is Ubuntu-based. I can try an full-fledged Ubuntu Live version, but that's not what I want to install.  Seeing as how the NUC sees the mSATA drive, and the Mint Live sees it, it's definitely a minimal ISO issue, and not the hardware. I was just asking to see if I can do anything from the CLI to see if the kernel sees the disk at all, or if there were any commands I could feed it to see the disk or re-enumerate the hardware for the kernel.

I don't want to do a full fledged install, as I'll never go to the desktop, nor will I need any of the other tools that require a desktop environment/window manager.  My plan is to install Ubuntu without a WM, then install XBMC and have that come up upon power up. I have no need for the extra space on the drive to be taken up with things that I don't need.  I could possibly try the server ISO and see if that recognizes the drive and work from there.

---

### Post by warren3 on 2014-04-16
Hello.

Did you get your problem sort pumpkinut?

I have been thinking about getting a NUC or Brix to run Ubuntu on so I been reading reviews and such not.  I came across an article today that might help you with your problem.

[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)

Scoll down about 2/3 of the page and read.

Hope it helps you out.

Cheers.

---

