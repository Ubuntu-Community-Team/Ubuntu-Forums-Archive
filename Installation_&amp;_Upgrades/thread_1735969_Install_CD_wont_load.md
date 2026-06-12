---
title: "Install CD wont load"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by xb3rtx on 2011-04-22
Ive tried to install ubuntu 10.10 about 5 times now all on different cds i burned.  Each time i verify the .iso and it is complete.  My laptop is an Asus G51J, has an nvidia 360m graphix card, i7 1.6ghz processor, and 6 gigs of ram.  

When i run the cd it shows the ubuntu logo and acts like its loading, then after several minutes of waiting the screen craps out and turns into a bunch of black and white blocks.  

This guy is having the exact same issue and has the same laptop [http://www.linuxforums.org/forum/ubuntu-linux/171100-installation-problems.html](http://www.linuxforums.org/forum/ubuntu-linux/171100-installation-problems.html) 

From reading his post it seems to be a graphics driver problem that was built into ubuntu.  Id love to use ubuntu but need a fix to this issue.  Please help,.. thank you

---

### Post by tommcd on 2011-04-22
First run the option to check the CD for defects. When the live CD boots, hit the space bar and you should get the option to check the CD for defects.
Assuming that the CD is good, try booting with the *nomodeset* option and see if you can get to the desktop. Hit F6 when the computer boots and select the nomodeset option. See this: [http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)
If this works, and you install Ubuntu, you will likely need to boot with nomodeset after Ubuntu is installed until you install the nvidia driver.

---

