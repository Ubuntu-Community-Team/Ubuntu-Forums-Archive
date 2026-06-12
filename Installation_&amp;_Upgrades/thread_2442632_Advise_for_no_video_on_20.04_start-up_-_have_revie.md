---
title: "Advise for no video on 20.04 start-up - have reviewed sticky extensively"
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by austinwi on 2020-05-05
Hoping that someone can help with being unable to see on start-up any grub, graphics, other than a frozen cursor, after a fresh install of 20.04LTS. My system is a 2010 iMac with AMD graphics chip no longer supported, so requiring nomodeset. In addition, since OSX will not work due to the AMD graphics having gone bad, it is single boot and had been running 18.04.4LTS perfectly. 

I tried 20.04 first with the Live USB and no permanent install and it worked fine. Unfortunately I didn't make the install from the Live USB, but started over and used the "go direct to install without trial" option, which was a mistake. I set up encryption. The install went without any problems. I then rebooted at the requester. The system seems to be starting fine, but it is stuck first with a backlit blank screen with a frozen cursor mid-screen. Then, obviously after following a programmed time, the screen goes completely black, with no back lighting evident. My problem also is that the Mac efi boot option menu will no longer appear, when I hold the appropriate key after the chime on start-up, so I can do a re-install. I can't reset PRAM either.

I have reviewed the sticky on this forum, done numerous searches and tried every suggestion: shift, esc, etc. Thinking that my keyboard may not be functioning, I have a new one ordered, but doubt it will accomplish anything.

Any help appreciated. Thanks in advance.

---

### Post by austinwi on 2020-05-11
Solved. I was able to resolve the issue in the following manner:

1) Purchased a new usb hard wired keyboard that enable me to successfully bring up the iMac efi boot options and run the 20.04 LiveUSB.
2) Re-installed a new fresh installation of 20.04. Upon completion, I did NOT go with the immediate re-boot option to avoid the blank screen with frozen cursor issue, but continued in the LiveUSB session.
3) While in the LiveUSB session, I did a search and got the following result on askubuntu.com: [https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu).
4) Following the directions of the 3rd answer by Christian (No. 11, bottom of page), I was able to successfully revise and add "nomodeset" to /etc/default/grub on the hard drive installation of 20.04. Many thanks to Christian:KS!
5) On reboot, I got the same empty screen, with frozen cursor.
6) I had earlier made a reFind usb stick for "just in case" scenarios. I rebooted the system to the reFind USB and among the various options was: Boot fall back loader, or, Boot EFI\refind\refind_x64.efi from EFI system partition. Tried this and "success:)."
7) In reFind's webpage, there is a link to how to set-up and apt-get reFind through Ubuntu repositories. Followed the directions, did this and now it is on the system hard drive.
8) Rebooted using hard drive and the reFind menu comes up. Among the options is: Boot EFI\ubuntu\grubx64.efi from EFI system partition. Tried this and Life Is Good:D.

On start-up today, everything was fine.

---

### Post by daniewicz on 2020-05-11
Glad you got things working. Linux on macs is my thing and it can get complicated. Apple doesn't always like to play nice. I have a 2008 MacPro. It has a 32-bit EFI but the rest of the hardware is 64-bit. Not fun.

---

### Post by austinwi on 2020-05-12
Thanks for your comment. It is good to know that someone checks the posts and can give advice from their own experiences. Regards.

---

