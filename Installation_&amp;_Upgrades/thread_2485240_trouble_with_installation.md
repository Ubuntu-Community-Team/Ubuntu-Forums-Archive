---
title: "trouble with installation"
date: 2023-03-23
forum: Installation &amp; Upgrades
---

### Post by krzsksz on 2023-03-23
hello,
I am trying to install ubuntu in dual boot with windows 10, i don't have much knowledge about the subject .I boot from usb stick, everything goes without any problem i choose language, keyboard language, connect to wifi, but every time i get to the page where i choose "normal installation" (i tried with and without downloading updates option) it just gets stuck there. After some time the "ubuntu 22.04 LTS is not responding" window pops out. I tried it with different usb sticks the problem doesn't change.

---

### Post by ubfan1 on 2023-03-24
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
  If using USB install media, use a  tool like unetbootin or rufus. 
  Don't just copy files to the USB.  
  See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  
3) Did you select the media check before trying to install?  
  See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by guiverc on 2023-03-24
I'll give some thoughts, alas there maybe no answers.

You've not provided enough details so we can't know which 22.04 product & thus not which installer you're actually using, so we're guess.

Ubuntu 22.04 LTS Server uses `subiquity` as its installer, Ubuntu 22.04 LTS Desktop uses `ubiquity` as do some *flavors* but not all with some using `calamares`. As you didn't say which 22.04 product we cannot know which you're trying to use  (*there was also a 22.04 Desktop ISO that uses the canary installer though that's unlikely as that ISO was hard to find*).

If I have issues during install; I'll ignore the installer window & switch to a text terminal & explore issues there...  I'll scan for *squashfs* & other media errors that highlight issues with your installation media itself (ie. *esp. if you didn't validate the ISO as per documentation, or the write of ISO to USB-flash drive which is where I experience issues most*).  This scan will be the same regardless of what 22.04 ISO you're using. This will be using `dmesg` & `journalctl` usually; to go further requires I know which 22.04 product which you didn't specify.

Next I explore for what the installer is doing (*here it matters which installer you're using, `ubiquity` I find the easiest, `calamares` next, with the snapped installers more difficult*), but general system messages will provide clues as to what the system is doing, or if it's having trouble with drive errors etc.  I do this using tools such as `top` etc; as well as reading logs via `dmesg`, `journalctl` etc... and again if I know which 22.04 product I can go a little further (eg. read the installer logs)

In most cases, I'd expect I have answers or clues from the two steps I just described.. Finding causes from  this point on get more specific, ie.
 
- how was the ISO written to media (*this can influence problems if not done as QA tested which is pure clone only*)

- what 22.04 media & how will that kernel stack match with your specific hardware; 22.04 media currently exists that will default to the GA stack (22.04 using linux 5.15), HWE stack with 5.15 at install (22.04.1 Desktop), or HWE stack with 5.19 (22.04.2 Desktop; 22.04.2 Server still uses GA) and you weren't specific as to which 22.04 ISO nor about your hardware...

etc.

---

### Post by yancek on 2023-03-24
In addition to answers to the questions above, what software did you use to create the bootable USB?
Did you use Disk Management in windows to create free space on which to install Ubuntu?
Do you feel comfortable enough to try to use the manual option to install, Something Else?

---

