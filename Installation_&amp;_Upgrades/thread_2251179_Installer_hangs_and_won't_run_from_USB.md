---
title: "Installer hangs and won't run from USB"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by Chris_Fischer on 2014-11-02
I'm trying to build a home theater PC running the amd64 build of Ubuntu 14.04. I'm new to both linux and building computers in general, so I'm sure there are plenty of ways I could be the problem here. There are no optical drives in my build, so booting from USB is my only option.

I can't get the installer to start. 
When booting from USB using UEFI, I'm taken to this screen:
[http://www.sunsetdesign.com/chris/bootfromuefi.jpg](http://www.sunsetdesign.com/chris/bootfromuefi.jpg)

When I select any of these four options, then screen goes black and nothing happens. I can hear the CPU fan running, but the screen doesn't refresh.

When booting from USB, I get this purple screen with an images of what looks like a film strip, an equals sign, and a stick figure inside of a bubble:
[http://www.sunsetdesign.com/chris/purplescreen.jpg](http://www.sunsetdesign.com/chris/purplescreen.jpg)

After some googling, I've found that people have been able to get the installer to run by hitting either Enter or F6 at this screen. In my case, it's been unresponsive to any keypresses once it reaches this point. Others have had success by being patient and letting this screen run for around 10 minutes. However, at the time of this post, it has been an hour and I've seen no change.

I'm open to suggestions on what else I can try on the software end, but since this is the first computer I've ever attempted to build, I'm almost positive it's a hardware problem. Right now I suspect the hard drive might be the problem? There is an LED on my case that indicates hard drive activity that I have never seen lit since I first turned on the machine. I would think that I'd see some kind of activity here while the OS is being installed on it. However, the BIOS does at least show that there is a 32GB storage device plugged in to one of the SATA ports, so I'm not sure what else could be wrong with it. 

Here's a screenshot of the setup screen on my BIOS if that helps, it at least looks like everything is plugged in correctly from here:
[http://www.sunsetdesign.com/chris/bios-specs.jpg](http://www.sunsetdesign.com/chris/bios-specs.jpg)

Here are my specs:

Motherboard - MSI AM1I, recently flashed with the latest BIOS
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130759&cm_re=MSI_AM1I-_-13-130-759-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130759&cm_re=MSI_AM1I-_-13-130-759-_-Product)

CPU - AMD Sempron 3850, 64-bit, 1.3Ghz
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819113366](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113366)

Memory - Crucial Ballistix Sport 4GB DDR3x1
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820148539&cm_re=ballistix_4gb-_-20-148-539-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148539&cm_re=ballistix_4gb-_-20-148-539-_-Product)

Storage - ADATA 32GB SSD
[http://www.amazon.com/ADATA-Premier-2-5-Inch-Synchronous-ASP600S3-32GM-C/dp/B009SKB5HA](http://www.amazon.com/ADATA-Premier-2-5-Inch-Synchronous-ASP600S3-32GM-C/dp/B009SKB5HA)

Any help would be greatly appreciated!

---

### Post by oldfred on 2014-11-02
What video card or just internal AMD?

Often nomodeset or other boot parameters are required.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
If you are getting grub menu at initial boot, then you are booting in UEFI boot mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Chris_Fischer on 2014-11-02
Thanks for the reply.

There is no dedicated video card in my setup, just the integrated Radeon in the CPU.

I have the option to boot in Legacy mode and in UEFI mode, but for now, I'm going to try booting from EFI since I seem to have more options there.

Sorry, I dug through some of the boot options that were suggesting in the links you posted, but without having a good idea of what the problem is, I'm not sure what options/combinations would be beneficial or if any are detrimental to my setup. I did try adding in 'nomodeset' to the boot options, but it still gets stuck at a black screen when I hit F10 to continue with the installer. Here's a screenshot of what my "edit" screen looked like before hitting F10:
[http://www.sunsetdesign.com/chris/nomodeset.jpg](http://www.sunsetdesign.com/chris/nomodeset.jpg)

Does this look right?

---

### Post by oldfred on 2014-11-02
That is ok, I usually take out the quiet splash so I can see boot process and then if it fails somewhere. If it does fail it usually is not the last thing posted but something a few lines above. New systems now scroll by very quick. But it all is in a log file.

If you try recovery mode I think nomodeset is already the default.

I have nVidia so I do not know AMD nor the integrated AMD.

I just build a new system but it was Intel with nVidia. But I had a lot of UEFI settings to change to get it to work correctly. And I was surprised that the open source driver did work to boot. I always before had to use nomodeset for install and first boot or until I install proprietary driver.

       MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
This thread had the similar issue of modified UEFI to only boot entry that says Windows.
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

    
Work arounds for systems that only boot Windows.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

