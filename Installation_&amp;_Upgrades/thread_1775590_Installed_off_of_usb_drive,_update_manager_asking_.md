---
title: "Installed off of usb drive, update manager asking for CD to be inserted"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by kelean on 2011-06-04
I have just installed 11.04.  I used a usb drive I installed ndiswrappers packages from the ubuntu 11.04 

ndiswrapper-common_1.56.3_all.deb
ndiswrapper-utils-1.9_1.56-3_all.deb
ndisgtk_0.8.5-1_i386.deb

I installed the three packages and installed the win wireless driver.  Everything is running very well.  One problem is that when I run the update manager it tells me that I have two packages to install.

ndiswrapper-common_1.56.3_all.deb
ndiswrapper-utils-1.9_1.56-3_all.deb

After I click okay and enter my password I get a pop up that states I need to install the install cd in the cd drive.

I never seen this in a long time.

---

### Post by papibe on 2011-06-04
Uncheck the CD/DVD option in the Software Sources (System -> Administration -> Software Sources). More info [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Hope it helps.

---

### Post by kelean on 2011-06-05
Thank you papibe, that did the trick.

---

