---
title: "Problems installing on Zotac Nano"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by waterwheel3 on 2016-09-22
I'm attempting to install ubuntu 14 on a Zotax Zbox Nano vd01.  That's one of those minipc/media boxes.  I have run other linux distro's on it in the past.

Problem: after install, it brings up the desktop and asks for the password for the user.  I enter that and hit enter.  All it does is go blank for a short period of time, the return to the login screen.

Other info: Complete new install of ubuntu. overwriting everything.  I had other problems intiailly (maybe related) where it wouldn't install at all. This was resolved by hitting 'F6' during install and adding --xforcevesa to the install string.  Doing so then allowed me to complete the installation and reboot, ended up with the problem as above.  Also, during the install, I indicated it should automatically login and not ask for a user/password.

Thanks for any assistance!

---

### Post by T.J. on 2016-09-22
Sounds like you are having a driver issue.  There is a test you can try.

Edit your Grub boot line when it starts by pressing E, and then add "nomodeset vga=0x318" to your startup parameters.  They will force the video card into standard VGA mode and should allow you to log in regardless of your driver.  If it lets you log in, it is likely you have a driver problem.  If it still does not, then something is not installed properly.  If it is a bad video driver, that can be corrected.

---

