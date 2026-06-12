---
title: "unable to install kubuntu 16.04 on ubuntu machine"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by stephan15 on 2016-05-08
I am at a loss. I have a machine running ubuntu 16.04 LTS and now want to change to kubuntu with a clean install. 
I have downloaded the kubuntu 16.04 iso image and transfered it to a usb stick with the Startup Disk Creator. 
Booting from this USB stick gives me a choice of
* Start Kubuntu
* OEM install (for manufacturers)
* check disc for defects

Start Kubuntu and OEM install both start a live system with no options to actually install kubuntu!
What am I doing wrong?

As a side note: Is there a way to install kubuntu and keep /home (it is not a seperate partition).

---

### Post by howefield on 2016-05-08
At the live desktop open the main menu and search for install (as per the image)...

My understanding is that if you choose the existing (Ubuntu) partition to install Kubuntu into but not mark it for formatting, the /home folder will not be removed but everything else will. This is true for Ubuntu, I'm assuming the same applies to Kubuntu.

In any event, a backup of files that are important to you should be taken care of before starting :)

---

### Post by stephan15 on 2016-05-08
Thanks so much for the help. It was spot on.
Kind of weird that the installation from USB is kind of hidden. When I have lots of time to spare I will try and see if it is as hidden when booting from CD/DVD.

---

### Post by howefield on 2016-05-09
> **stephan15 said:**
> Thanks so much for the help. It was spot on.
Kind of weird that the installation from USB is kind of hidden. When I have lots of time to spare I will try and see if it is as hidden when booting from CD/DVD.

You are very welcome.

When I booted from the live media there was a desktop "folder", almost icon size that I couldn't resize or open. It is probably in there but the next best step is as you have done, to search the menus.

---

