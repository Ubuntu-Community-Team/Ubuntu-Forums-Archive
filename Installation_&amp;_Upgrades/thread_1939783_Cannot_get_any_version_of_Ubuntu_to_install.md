---
title: "Cannot get any version of Ubuntu to install"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2012-03-12
I have tried Ubuntu 10.10, 11.04, 11.10, and 12.04 pre-Beta.  They all cause problems (kernel panic mostly).  I have even tried LinuxMint12 OS, with the same results.  I can not even get them to operate correctly as a "Live CD".  I can run _System Rescue CD_ okay.

This is on my desktop computer (White box described below).  This computer did fine until it was upgraded to Ubuntu 10.10 which froze up frequently.  I have installed a new HD, removed all the others and tried to get a working install of Ubuntu.  

When I installed the new HD (640GB), I cleaned the terminals on the RAM (2 X 1GB + 2 X 2GB) and the video card.  Just to ensure good contact. I blew all the dust out with compressed air and cleaned up anything I saw.

before all of this I had Ubuntu 10.04LTS working just fine.

At this point I do not know what is causing the problem, either Operating system or hardware.  I get a good Memory test and the BIOS is seeing the 6GB RAM.

---

### Post by 2F4U on 2012-03-12
Are the kernel panics happening during the boot sequence or after some time of operation? Since you have problems with so many versions, I would suspect a hardware problem. For how long did you run the memtest? Some problems only show up after some iterations. I once had a memory module that showed a problem only during the third iteration of memtest (and, of course, during normal operation).

---

### Post by sudodus on 2012-03-12
To exclude hardware error you can also (re-)try Ubuntu 10.04 LTS live from the install CD or USB drive.

If it performs well with 10.04, I suggest that you either try to identify a bug in Ubuntu 12.04 and report it, or simply wait until 12.04 will work for you. 10.04 will be supported for another year...

Edit: You could also try some boot options, although kernel panic seems too bad to be fixed that way
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by todoporron on 2012-03-13
Have you tried the "nomodeset" option?

---

### Post by jlh68 on 2012-03-14
Yes I tried that. I have now tried Ubuntu 10.04, 10.10, 11.04, 11.10, 12.04, LinuxMint12, & Debian6.0.4.  I am now leaning to a hardware problem.  I do  not get any POST codes on my Post Code reader, but I did a memory test and it all checked out BAD?  I took the two 2GB sticks out, leaving in the two 1GB sticks.  I could not get any OS to install, even enough to get back to the MemTest function.  Then I got a BIOS beep that indicated a problem with the video card.  I could not even get into the BIOS to change the setup parameters.  So it could be a failed BIOS, a problem with the video card or a MB that has some failed part of it. Oh I changed the battery on the BIOS, even though I did not know the status of the old battery.

Unless someone offers some trouble shooting techniques for this system, I believe I will just start over and buy a new MB, a new APU, two sticks of DDR3 RAM, and a media card reader.

Any recommendations?

---

### Post by sudodus on 2012-03-14
I doubt that all your RAM sticks are bad. I suggest that you try again. It may be important which slot you are using, I mean that there is one slot that must be used. It is probably at one end of the row of slots (try both ends with more than one stick!).

Maybe there is a bad component that is gradually breaking down, and is or will soon make it impossible to run your computer. Is there anyone near-by, that can have a look at your computer and help you?

---

