---
title: "Cannot update computer in any fashion, what-so-ever, not live usb/cd or anything."
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by trolling1856 on 2014-06-01
Hello, I'm on an HP 2000 running Ubuntu 12.04 lts. I'm going to start off frankly, I've messed up my computer in some way. It did not have any problem installing new operating systems before i came along, er-go my reason for having ubuntu. I've got one 14.04 live usb, two 12.04 live usb, and even a 12.04 live cd. None of them even conisider booting, theyre all readable and writable on the system but nothing happens but a boot as normal with any of the live storage devices. Will answer any question.

Edit: I plug in usb, reboot and it boots as if there is no device plugged in, going straight into ubuntu. I've f2'd and checked my boot options and it shows no options other than the main os.

---

### Post by Bashing-om on 2014-06-01
trolling1856; Hi ! Welcome to the forum.

Have you reset the boot priority order in bios (or UEFI, if this applies ) in order to boot from a DVD (USB)?
> 
 but a boot as normal with any of the live storage devices

is indicative that the boot priority has not been changed.

[INDENT][INDENT]hope this helps;
[INDENT][INDENT][INDENT]else: greater detail in your process is required ->
[INDENT][INDENT]I did this, I expected this to happen, and this is what did happen[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by trolling1856 on 2014-06-01
The boot order has been messed with probably too much for its own good. I have changed the order, i believe usb is first then dvd.

---

### Post by ubfan1 on 2014-06-01
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And once you get it to boot:
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by trolling1856 on 2014-06-01
Ive used several iso's and several different usb's and cd's. I burned it as slowly as it wanted. The liveusb wont boot to begin with so i cant integrity check. Should i do the extensive or quick media check or are either satisfactory. What do i stand to gain from doing this memory check?

---

### Post by Bashing-om on 2014-06-02
trolling1856; Hello,

All I can think of next is your burning procedure, in that no boot code is found on the install mediums.
The .iso file (that you did verify with md5sum) must be burned to disk as an 'image' NOT data.
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) <- create bootable Live USB drives
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Please to advise on your end goal and we can assist greater. Are you trying to install as dual boot, and if so what is the other operating system. What is the operating system you are working from to make the install mediums ?, Is this machine of recent origin such that EFI booting is the determining factor ?

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

