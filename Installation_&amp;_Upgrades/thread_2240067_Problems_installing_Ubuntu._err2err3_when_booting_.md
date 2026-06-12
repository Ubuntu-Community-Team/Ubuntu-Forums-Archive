---
title: "Problems installing Ubuntu. err2err3 when booting from cd, or usb"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by seedlesstom on 2014-08-17
My apologies in advance if this has been covered already. I've been googling all day and can't seem to find anything covering this.

Yesterday I decided that I was finally going to check out Ubuntu, as I have a few old hard disks laying around. Downloaded the .iso, used LiLi USB creator and slapped it on a usb stick. Shut my system down, unplugged my SSD running windows, and all of my storage HDDs, except for the one I wanted to install Ubuntu on. Plug the USB stick in, power on, F2 into the UEFI BIOS, BIOS recognized the HDD I wanted to install to, as well as my USB stick. Override the boot to the USB stick, save, exit. Err2err3 is all I get. Power down, plug the SSD back in, power on, boot back into Windows just to make sure nothing weird is going on and Windows also recognized the drive. So I go back and try it again, same thing. I called it for the night. This morning, I wake up and I'm like ok, maybe it just doesn't like my USB stick, so I threw an optical drive in the machine, burned the .iso to disc, power down, run through my wiring again just to make sure everything is good. Power on, F2 into BIOS, boot from optical... Same thing, err2err3.

Hopefully, it's just doing something silly. I'm not a super pro when it comes to this stuff. I've done my fair share of windows installs and I built this computer myself, but plugging some components together and booting a windows disc is easy peasey.

If there is any other info you'd like to know about my system, I'd be glad to give it to you.

Thanks in advance.

---

### Post by ubfan1 on 2014-08-17
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by seedlesstom on 2014-08-17
1) Just checked the hash. We're good there.
2) Burned it through windows and verified it. No problems there.
3/4) The CD and/or flash drive never booted. I got the error as soon as I left the UEFI screen.

---

### Post by ubfan1 on 2014-08-18
Can you try the USB/CD in another machine?  I have only ever used unetbootin on Windows, no experience with LiLi.

---

