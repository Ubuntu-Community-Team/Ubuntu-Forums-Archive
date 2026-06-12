---
title: "hard drive not visible for installation of os"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by barelyhere on 2012-10-06
I have tried multiple distro versions and only slacko puppy will install to the hard drive, however my system requirements are barely adequate for it to operate. 

Would like to try Lubuntu to see if it will run smoother. Lubuntu operates from the Live disc fine.

Problems occur when I reach the screen for partitioning the hard drive, my hard drive is not there to choose. I have partition options but the space for the hard drive is blank. If I click to proceed it says no root file defined.

---

### Post by darkod on 2012-10-06
This usually happens if the disk has been used in fakeraid before and the raid meta data is still left there. The installer ignores it.

Boot into live mode from the cd first, and in terminal remove the meta data with:
sudo dmraid -E -r /dev/sda

After that it should work fine. NOTE: Don't do this if you are actually running a raid and want to install on it. It will break the array. You install on raid in a different way.

---

### Post by barelyhere on 2012-10-06
No raid arrays to worry about ill give it a try thanks

---

### Post by barelyhere on 2012-10-06
invalid option --  is all I get and nothing happens

any other ideas

---

### Post by darkod on 2012-10-06
Make sure the hdd is /dev/sda, it might be different device name especially if you are booting from usb stick.

If you are not sure, check the devices with:
sudo fdisk -l (small L)

That will show the hdd device name.

Also, make sure you type the options correctly, exactly as I posted. Linux makes difference between small characters and capitals.

That message sounds like you either used the command with wrong syntax, or the hdd is not /dev/sda. It might be /dev/sdb or similar.

---

### Post by barelyhere on 2012-10-06
google helped  with the format sudo dmraid -Er did the trick now trying the install again hope for the best

---

### Post by barelyhere on 2012-10-07
problem solved that worked thank you for the help

---

