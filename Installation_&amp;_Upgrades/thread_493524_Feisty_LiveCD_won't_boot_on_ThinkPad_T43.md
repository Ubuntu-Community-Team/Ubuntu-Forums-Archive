---
title: "Feisty LiveCD won't boot on ThinkPad T43"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by davidsiegel on 2007-07-05
I'm trying to install Feisty on a ThinkPad T43. I've triple checked the BIOS settings to make sure booting to cd is supported and the devices are in the correct boot priority. When I boot with the live cd, I get a black screen with an underscore in the upper left corner for about four seconds, then the laptop just boots Windows by default. What can I do? There's no floppy drive or anything.

---

### Post by jimrz on 2007-07-05
> **davidsiegel said:**
> I'm trying to install Feisty on a ThinkPad T43. I've triple checked the BIOS settings to make sure booting to cd is supported and the devices are in the correct boot priority. When I boot with the live cd, I get a black screen with an underscore in the upper left corner for about four seconds, then the laptop just boots Windows by default. What can I do? There's no floppy drive or anything.

are you sure you burned the disk "as an image" and did you check the md5sum for the cd after burning it? sounds like a bad disk. since you are not even getting the initial options screen from the cd, it appears that your machine does not see it as a bootable disk

try burning again at the slowest speed your burner will support. there are frequent problems with disks burned at high speeds.

---

### Post by davidsiegel on 2007-07-05
I have already burned two cds that booted just fine on my other ThinkPad but are both no-goers on the T43.

---

### Post by jimrz on 2007-07-05
> **davidsiegel said:**
> I have already burned two cds that booted just fine on my other ThinkPad but are both no-goers on the T43.

strange...is it giving you any error msg's?

never had anything similar on either of mine (T42 + 600x) ot on the r20something i set for a friend.

---

### Post by davidsiegel on 2007-07-06
No error messages - as I said, it just displays a black screen with a white underscore in the upper left corner, then proceeds to boot Windows XP.

---

### Post by davidsiegel on 2007-07-08
bump - please help! If we can resolve my issue (and the solution is probably trivial) there will be one less WIndows user and one more Ubuntu user in the world.

---

### Post by just_bruce on 2007-07-25
i downloaded both ubuntu and kubuntu feisty and they boot on a T43 and a T60.  I burned the iso to cd using burncdcc rather than the sonic burner that comes with the thinkpad.  the burncdcc worked great and it is very simple. install it on one of the T's, download to there, and burn.
the website is [http://www.terabyteunlimited.com/utilities.html]("http://www.terabyteunlimited.com/utilities.html")
and it is free.

---

