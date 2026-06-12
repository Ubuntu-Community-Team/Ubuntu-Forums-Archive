---
title: "Touch issues (tablet software)"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by Mol3000 on 2013-05-20
So following the instructions here: [https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install) .... i am having issues

I am having a issue now when it comes to updating my nexus 7
 So i did the steps below:
 "On your computer, press Ctrl+Alt+T to start a terminal.
 sudo add-apt-repository ppa:phablet-team/tools"
 Then this:
 "sudo apt-get update
sudo apt-get install phablet-tools android-tools-adb android-tools-fastboot"
 and everything went alright. Next i rebooted the device in recovery  mode and type this cmd in "sudo fastboot oem unlock" It sits there  forever and nothing happens with the device.  So i tried hitting the  power on the device and it just boots into regular old android and then  13.04 picks it up
 So i tried the manual approach using this cmd "adb push /path/to/your/downloaded/raring-preinstalled-armel+grouper.zip /sdcard/autodeploy.zip"  but it acts like it cant find it while its in recovery mode but any  time i hit the power button and it goes back into regular old android it  picks it up.  I even tried putting the software in a sdcard folder  while in andriod mode then restarting it back in recovery mode hoping it  would pick up from there but it wont.
 Please help!!!!!!

---

