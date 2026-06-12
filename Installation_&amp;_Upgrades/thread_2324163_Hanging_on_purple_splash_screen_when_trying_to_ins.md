---
title: "Hanging on purple splash screen when trying to install/run from USB/cd"
date: 2016-05-11
forum: Installation &amp; Upgrades
---

### Post by alex539 on 2016-05-11
So I got a laptop for my PhD and It had a preset partition (windows 10 on ssd and Linux mint on Hard drive) there was an issue that meant I now want change mint to Ubuntu. So I tried to install from a USB but it hangs on the purple screen and the dots stop moving after a minute or two and it just hangs. I am new to Linux and is there a way to fix this I have tried installation via cd aswell but the same thing happened, I have a nvidia. GTX960M and an Intel i7  and I'm trying to install Ubuntu desktop 16.04 LTS (not sure what other info is needed ask if any more needed)

---

### Post by grahammechanical on 2016-05-11
Anyone installing any Linux distribution on a machine with Windows 10 pre-installed will need to read this first and follow the guidelines.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In regards to the problem of getting the Ubuntu live session to load you may need to change one of the boot parameters and add the nomodeset option. See this wiki page under the heading Change the CDs Default Boot Options. See section 6 - F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At the first purple screen with the icons of a human & a keyboard press Enter. Select a language (Default English). At the underlying screen press F6 and a small menu will appear bottom right. Select nomodeset & press Enter. Then press Esc to get back to the underlying screen and select Try Ubuntu without installing or Install Ubuntu.

Sometimes we need to use a combination of these F6 options to get a live session to load. To install Ubuntu over Linux Mint you will need to choose the Something Else option. Are you clear about what to do when you choose that option? If you need assistance with that please tell us about the partition layout of the hard disk. At the Try/Live session desktop run the Disks utility. That will show you the partition layout.

Regards.

---

