---
title: "Grub &quot;broken&quot; on distribution update"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by colehill on 2011-09-11
A friend of mine has installed Ubuntu 11.04 with the Unity desktop and I thought to upgrade my 10.04 (Lucid) installation to the new release.  The update manager would only allow me to update to 10.10 (Maverick), so I upgraded to Maverick.  In the process it has c*cked up Grub and now I can't boot.  Initially I had the error message "symbol 'grub-xputs' not found".

I have been through the steps in thread 1580752 and 9836539 to reinstall Grub and/or purge and reinstall but I am now at the stage when I just get a black screen when I boot.  I am getting the resolution problem error when trying the apt-get commands once I am chrooted into the real system.  I don't get these problems if I at the standard Ubuntu prompt live disk, but overinstalling GRUB from there has given me the black screen issue.

My installation is fairly standard, dual booting with Windows 7, the Ubuntu partition is on /SDA5 and a "shared" data partition.  The partition table is still intact - I can view it with Acronis Disk Director and/or fdisk -l.

Please advise how I can fix GRUB to give me back my multibooting notebook?

TIA

KD

---

### Post by YesWeCan on 2011-09-11
Hi and welcome. :)
Probably best to download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt file here in code tags (highlight text and click # above)

---

### Post by drs305 on 2011-09-11
Do you get the Grub 2 menu and the problem occurs later? A Grub 2 problem should be accompanied by a Grub error message. If you are getting a black screen (perhaps a blinking cursor in the upper left) without an error message it is probably not a Grub 2 error per se. 

If it's a video driver error, at the Grub menu press 'e' to edit the menuentry.
Go to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'.
Press CTRL-x to boot. 
If it boots to a visible Desktop, try adding your video card via Additional Drivers.

If it is a Grub problem posting the RESULTS.txt as *YesWeCan* suggests should help us help you.

---

