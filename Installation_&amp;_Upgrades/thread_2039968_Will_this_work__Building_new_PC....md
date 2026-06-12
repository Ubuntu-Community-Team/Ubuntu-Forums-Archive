---
title: "Will this work???  Building new PC..."
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by shockfi3nd on 2012-08-10
Hey all,

New to the forums, but I've been using Ubuntu on one of my laptops for a bit now.  I am building a custom PC, but I've never tried to install Ubuntu on a brand new machine straight from the box (no OS or anything installed, fresh). My question is, will Ubuntu 12.04 (or any build for that matter) work on the components listed below?  If so, is there anything special I need to do to install Ubuntu on this?  I plan on using the install from USB option, if that matters.  Thanks for any help on the matter...

Here are my components...

Motherboard: Gigabyte GA-Z77X-UD5H WiFi

Processor: Intel i5-3570K 3.4 GHz LGA 1155

RAM: Kingston HyperX 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600

HDD: Seagate ST2000DM001 Barracuda 7200 2TB SATA 6 GB/s, 64 mb

Video Card: MSI R7850 Twin Frozr 2GD5/OC Radeon HD 7850

DVD/CD:  ASUS 24X DVD Burner

I still have a few days before all of the parts get in.  I'll order Win7...if I HAVE to.

Thanks for any assistance.

---

### Post by JrockZ on 2012-08-10
> **shockfi3nd said:**
> Hey all,
 
New to the forums, but I've been using Ubuntu on one of my laptops for a bit now. I am building a custom PC, but I've never tried to install Ubuntu on a brand new machine straight from the box (no OS or anything installed, fresh). My question is, will Ubuntu 12.04 (or any build for that matter) work on the components listed below? If so, is there anything special I need to do to install Ubuntu on this? I plan on using the install from USB option, if that matters. Thanks for any help on the matter...
 
Here are my components...
 
Motherboard: Gigabyte GA-Z77X-UD5H WiFi
 
Processor: Intel i5-3570K 3.4 GHz LGA 1155
 
RAM: Kingston HyperX 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600
 
HDD: Seagate ST2000DM001 Barracuda 7200 2TB SATA 6 GB/s, 64 mb
 
Video Card: MSI R7850 Twin Frozr 2GD5/OC Radeon HD 7850
 
DVD/CD: ASUS 24X DVD Burner
 
I still have a few days before all of the parts get in. I'll order Win7...if I HAVE to.
 
Thanks for any assistance.
 
Im new here but it should work from what i can tell Boot from the usb first make sure it works fine, then choose install

---

### Post by shockfi3nd on 2012-08-10
Ok, thanks.  I will try when I put get all the components and assemble them.  I know you said you are fairly new to the forums.  Any idea if there is support for all of the components?

---

### Post by shockfi3nd on 2012-08-10
If anyone knows if this will, or will not work, please let me know.

---

### Post by chadk5utc on 2012-08-10
Welcome,
Although I am not familiar with all the hardware that you have listed but I do have a couple suggestions to aid in your search to find compatible hardware. Most operating Systems have whats known as an HCL or Hardware Compatibility List which lists known working hardware and some that partially works and sometimes lists any known issues. 
 What you can also do is try a google search for the OS your going to use along with the hardware like so: Ubuntu GA-Z77X-UD5H WiFi  which yields About 26,500 results
Hope this helps a little in your quest

---

### Post by whatthefunk on 2012-08-10
> **JrockZ said:**
> Im new here but it should work from what i can tell Boot from the usb first make sure it works fine, then choose install

Theres no need to do that if its a fresh install and theres no other OS.  just burn a CD and install.

The main thing to worry about is the graphics card and the motherboard.  Most motherboards will work, but some special features may be Windows only.

One of the commenters on Newegg.com said he tried Fedora on it with no problem.  It will probably work.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545)

This guy here got an HD 7850 card working properly with only a minor hang up so you should be able to do the same.
[http://askubuntu.com/questions/172495/why-wont-hdmi-audio-work-with-radeon-hd-7850](http://askubuntu.com/questions/172495/why-wont-hdmi-audio-work-with-radeon-hd-7850)

---

### Post by drmrgd on 2012-08-10
As far as I can tell the hardware looks OK.  One thing I want to point out, which is something I learned the hard way with my recent build), is to be sure to be careful with your Ubuntu installation in regard to UEFI.  I see the motherboard supports this, and so your installation will be slightly different than before.  If you're not dual booting, this should be fairly easy, though.  If you want to dual boot, still not bad, but requires a little more effort.

You'll need to be sure to grab the 64-bit version of Ubuntu, as it has native UEFI support built in already.  Then when you boot from the .iso, make sure you're booting in UEFI mode instead of BIOS mode.  I would recommend you do manual partitioning of the drive, and partition in as GPT rather than MBR (which you'll want to do with a 2TB HDD anyway!), putting ~200MiB efi_boot partition as the first partition of the drive.  You can partition the rest as you like.  That efi-boot partition will be where you'll assign Grub, and the rest of the install should be just like normal. 

If you have trouble getting the UEFI install to work, and / or need some advice with dual booting (if you go that route) post back and let us know.  There's a few people here that are quite good at getting that configuration to work.

---

### Post by shockfi3nd on 2012-08-10
Ok, thanks for all the info.  I will post back if I have issues, or what worked for me.

---

### Post by shockfi3nd on 2012-08-14
OK,

So I was able to install Ubuntu 12.04 on this new setup.  I was having issues with the install at first.  After it installed and downloaded updates, the screen would go black.  I am using a TV as my monitor through HDMI.  Eventually, I was able to install and no install the updates.  Then I would install the driver for the video card and it would work.  I am still getting a small icon in the lower right corner saying "AMD Unsupported Hardware".  I have seen some stuff on this, but if anyone has a fix, I would appreciate it.  It doesn't hinder anything, but if there is a fix...

---

### Post by forkandles on 2012-08-15
Did you see this:

[http://ubuntuforums.org/showthread.php?t=2042108](http://ubuntuforums.org/showthread.php?t=2042108)

---

### Post by shockfi3nd on 2012-08-15
Thanks for the link forkandles.  I followed the directions under the wiki installation guide for the watermark and it removed it.  Thanks again.

---

