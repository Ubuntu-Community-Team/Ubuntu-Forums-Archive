---
title: "CUDA Driver Error on MSI Laptop"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by zaganos2 on 2017-01-16
Hey,

I'm trying to run CUDA on my machine. I've  installed the driver on Ubuntu 16.04 and it worked for like a week  without any problems but then it stopped working for no reason. OS even stopped detecting the driver. 
Then I reinstalled Ubuntu 16.04 more than 5 times and on 14.04 once but  each time, after restarting the laptop I got a different error and had  to reinstall Ubuntu. Once I got a black screen when I turned on my  laptop, once I made it to login screen but it didn't login after typing  my password, it redirected me to the same screen over and over again.  After each installation, I got a different type of error and couldn't  even start the OS.
So I think there must be a problem with the driver or my machine. My  machine is MSI GT72S 6QE Dominator Pro G Tobii. CPU: Intel Core i7  6820HK and GPU: Geforce GTX 980m (you can see the full specs here:  [https://www.msi.com/Laptop/GT72S-6QE-DOMINATOR-PRO-G-tobii.html#hero-overview](https://www.msi.com/Laptop/GT72S-6QE-DOMINATOR-PRO-G-tobii.html#hero-overview))

So I need some help on how to run CUDA on Ubuntu 16.04 properly. Thanks in advance.

---

### Post by efflandt on 2017-01-17
Just a shot in the dark. Is your power LED blue or amber when trying to use CUDA. My older GE60-2OE (in BIOS mode w/Win7 & Ubuntu) would be blue while using Intel graphics and amber when Nvidia was active. Although, the laptop had been having trouble booting up for a while and now when I attempt to power up it just alternates blue and amber as fan and (measured) power use winds down to off in 7 seconds with nothing on the screen, off for 4 sec, then on winding down for another 7 sec, off for 4 sec... until I hold the power button to keep it off (regardless of which drive or mSATA is in it). I have had no problems using an MSI GTX 750 Ti graphics card, but that laptop will not even get to BIOS splash and is a brick at this point.

MSI specifically says that they do not support Linux, but until the hardware failure, I had no trouble running a 13.10 earlier from its hard drive (sda4) or 14.04 booted from Crucial M550 512 GB mSATA SSD with grub on sdb as boot device, even though Crucial could not even verify if their mSATA would work (do to lack of published spec's from MSI). The mSATA SSD is good, in 2.5" SATA adapter it is currently booting 16.10 on my desktop PC. I did not even know that my laptop had (2) mSATA ports until I saw a video and opened mine up (yours has M.2 ports).

---

