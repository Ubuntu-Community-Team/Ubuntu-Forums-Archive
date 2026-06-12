---
title: "Getting - [Errno 5] Input/output error - when trying to install 10.10 via PXE"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by l3dx on 2010-10-10
I've managed to boot up ubuntu-10.10-desktop-amd64 using PXE, but when the installer is copying the files it fails. I've md5sum checked the iso and it is OK. Any other suggestions?

> [Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

---

### Post by annnie on 2010-10-10
I am seeing the same issue here (currently have 10.04 installed, and running the live CD for 10.10 - have tried both installing from the 'live' environment, and choosing Install directly from the initial menu), not aware of any issues with disc or hard drive. Will keep trying things and let you know if I come up with anything... 8-)

(Edited to add: for the 32 bit version of standard Ubuntu)

annnie

---

### Post by l3dx on 2010-10-10
I left it alone for some hours, and gave it another try now. Worked without any problems :) Don't know if it was bad luck, or if the server used for PXE couldn't serve fast enough.. (it's also used for video streaming).

@annnie have you checked the md5 checksum for the cd/iso? If you didn't knew already, this can be done to verify the integrity of your download :) 

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by annnie on 2010-10-10
Glad you got it sorted!

I checked the md5sum etc, all ok so it's a bit of a mystery why all the I/O errors on the CD - I did have the same issue with 10.04 now that I think about it (totally different brand of CD etc though) and tried the burning at different speeds etc - maybe the CD drive is just dodgy on this laptop! :P

Doing it from a USB stick instead and that seems OK so 'solved' in some sense here too (time for a new CD drive though!)

---

### Post by l3dx on 2010-10-10
Good to hear! Good luck with the USB approach ;)

---

