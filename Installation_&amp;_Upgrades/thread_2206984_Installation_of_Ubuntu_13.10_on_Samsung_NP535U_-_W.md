---
title: "Installation of Ubuntu 13.10 on Samsung NP535U - Win 8.1 not detected"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by livio2 on 2014-02-21
Hello everyone,
I have tried installing Ubuntu 13.10 on my new laptop Samsung NP535U at 64bit with AMD processor and Windows 8.1 as OS.
Since there is no CD/DVD reader, I tried the installation via USB.

In the BIOS boot settings, I see the following options:
[COLOR=#101010][FONT=Ubuntu]- UEFI: General USB Flash Disk 1.0 (which I set as first)[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]- Windows Boot Manager (which I set as second)[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]- UEFI: ST500LT012-9WS142 (it appears twice, I disabled both)[/FONT][/COLOR]

Here is the screenshot I did with my phone: [http://share.pho.to/4nQOw](http://share.pho.to/4nQOw)[COLOR=#101010][FONT=Ubuntu] [/FONT][/COLOR]

Then I click on "Install Ubuntu", but the next page appearing says "The computer currently has no detected operating systems."
This is of course wrong, as I have WIN 8.1.. But it seems Ubuntu does not see it...

here the other screenshot: [http://share.pho.to/4nQNE](http://share.pho.to/4nQNE)[COLOR=#101010][FONT=Ubuntu]  [/FONT][/COLOR]

I really do not understand why WIN is not detected..Could some of you help me solve this problem ?

---

### Post by livio2 on 2014-02-23
fastboot and secureboot are deactivated..
I really don't understand why WIN8.1 is not detected during the installation of Ubuntu.. I see many people complaining about this but no solutions are working for me..

could anyone help me ?

---

### Post by marort2 on 2014-02-23
Livio2, I just went through that and installed Ubuntu 13.10 successfully on my Pre-installed Win 8.1 on an HP Pavillion TS 14z. 

You are supposed to create a volume within Windows first; just leave as unallocated space. Then reboot with your LiveDVD or USH and select 'Something Else'.
You should see the volume you are going to use as 'Free Space' (check the size of this drive).

You will have to create SWAP space first by clicking on '+', then add EXT4 by clickin on '+' again. Continue with installation from here.

Look at this link [http://www.intowindows.com/dual-boot-windows-8-and-ubuntu/](http://www.intowindows.com/dual-boot-windows-8-and-ubuntu/)

---

