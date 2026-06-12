---
title: "Installing Kubuntu 10.04 on iMac Intel Core i5"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2010-08-11
Which version (32bit or 64bit) of Kubuntu should I install on my iMac Core i5?

I'm removing the stock HDD and installing an OCZ Vertex 2 SSD which will be home to Kubuntu. I appreciate any tips. 

I have both a Magic Mouse and a Magic Trackpad. Will I run into any hardware support issues?

---

### Post by MountainX on 2010-11-02
> **MountainX said:**
> Which version (32bit or 64bit) of Kubuntu should I install on my iMac Core i5?

I'm removing the stock HDD and installing an OCZ Vertex 2 SSD which will be home to Kubuntu. I appreciate any tips. 

I have both a Magic Mouse and a Magic Trackpad. Will I run into any hardware support issues?

UPDATE:
For the iMac 11,1 (the model I own), I have to install 32 bit Linux (even though OS X on the iMac can access over 4GB of RAM).

I did install the OCZ SSD. Now the iMac is totally silent! And fast.

There are plenty of issues with the Magic Mouse and the Magic Trackpad in Ubuntu. I can't get either one to work to my satisfaction.

The best installation guide I have found is here:
[http://ubuntuforums.org/showthread.php?t=1476226](http://ubuntuforums.org/showthread.php?t=1476226)

However, at this moment, I still don't have Ubuntu working on my iMac. Many, many installation issues.

---

### Post by MountainX on 2010-11-02
Here's the problem. It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me. I gave up installing Linux on my particular iMac model.

This issue does not affect all model iMacs. Mine is a 27" late 2009 model.

Here is how to check the serial number to determine the model.

On the bottom of your iMac stand, you'll find a label with the serial number printed on it, or from the Apple menu, choose About This Mac. Configure To Order (CTO) models are designated with an asterisk (*). Check the last three characters on the serial number:
iMac (Mid 2010)
DAS, DNM* iMac (21.5-inch, Mid 2010)
DB7, DNN* iMac (21.5-inch, Mid 2010)
DB6, DNP* iMac (27-inch, Mid 2010)
DB5, DNR* iMac (27-inch, Mid 2010)
iMac (Late 2009)
5PC, B9U, CY8* iMac (21.5-inch, Late 2009)
5PK*, B9S* iMac (21.5-inch, Late 2009)
5PE, 5PJ, CYB* iMac (27-inch, Late 2009)
CYC*, 5PM*, 5RU* iMac (27-inch, Late 2009

---

