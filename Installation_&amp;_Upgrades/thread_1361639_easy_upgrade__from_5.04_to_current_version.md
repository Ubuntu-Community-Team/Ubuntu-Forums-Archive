---
title: "easy upgrade  from 5.04 to current version?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by AlxR on 2009-12-22
Hi - completely new to Linux Ubuntu and to breathe life into an old Toshiba laptop I decided to install Ubuntu from an install disk I picked up some time ago. Well the good news is the laptop works a dream (SO much better than WinXP) but it turns out I have an unsupported version of ubuntu 5.04.

What is my easiest route to upgrade to the current version. I am comfortable using computers but completely new to Linux. What are my best next steps?

Many thanks,

AlxR

---

### Post by Grenage on 2009-12-22
Because that's a really old version, I would *really* recommend you download and install a fresh copy of 9.10.

---

### Post by phillw on 2009-12-22
+1 on new install. If the laptop has a low spec (256 MB Ram etc), then you may want to take a look at xubuntu - It's for low powered machines, but is still 'ubuntu' :-)

[http://www.xubuntu.org/](http://www.xubuntu.org/)

Regards,

Phill.

---

### Post by houseworkshy on 2009-12-22
8.04lts is also very nice and still supported.

---

### Post by coffeecat on 2009-12-22
There is no way to upgrade from 5.04 to the current version. To do version upgrades (dist-upgrades) you have to go version by version (5.04 > 5.10 > 6.06 > 6.10 and so on) but you can't because the packages you need to download for most (all?) pre-8.04 versions are no longer available.

What model is the laptop? Specifications? Try downloading the ISOs for both 8.04 and 9.10, burning them to CD and running them both live before committing yourself to a hard disc install. The reason for trying those two versions is that 9.10 is the latest, but 8.04 is a long-term support version which might support older hardware better than the latest version.

---

### Post by slakkie on 2009-12-22
> **coffeecat said:**
> There is no way to upgrade from 5.04 to the current version. To do version upgrades (dist-upgrades) you have to go version by version (5.04 > 5.10 > 6.06 > 6.10 and so on) but you can't because the packages you need to download for most (all?) pre-8.04 versions are no longer available.

What model is the laptop? Specifications? Try downloading the ISOs for both 8.04 and 9.10, burning them to CD and running them both live before committing yourself to a hard disc install. The reason for trying those two versions is that 9.10 is the latest, but 8.04 is a long-term support version which might support older hardware better than the latest version.


No way? Please read some documentation before making such bold statements. There is way: see the link in my signature, or just google EOLUpgrades. Way.

Anyhows, upgrade from 5.04 to 6.06, upgrade from 6.06 to 8.04 and you have a supported version. 4 upgrades in total: 5.04 to 5.10, 5.10 to 6.06 and 6.06 to 8.04. If you want to upgrade to 9.10 wait 6 months and you can upgrade from 8.04 to 10.04 in the blink of an eye.

---

### Post by coffeecat on 2009-12-22
> **slakkie said:**
> No way? Please read some documentation before making such bold statements. There is way: see the link in my signature, or just google EOLUpgrades. Way.

Thank you for correcting me on a point of fact. I had forgotten the LTS > LTS path.

I am always happy to be corrected if I get my facts wrong, but ask yourself this: could your language have been more diplomatic? Something along the lines of:

"In fact there is a way. You can upgrade directly to an LTS version and then to the next LTS version."

:wink:

---

### Post by AlxR on 2009-12-22
"What model is the laptop? Specifications? Try downloading the ISOs for both 8.04 and 9.10, burning them to CD and running them both live before committing yourself to a hard disc install. The reason for trying those two versions is that 9.10 is the latest, but 8.04 is a long-term support version which might support older hardware better than the latest version."
 
This seems to be a possible route.  I am busy burning the 9.10 version to CD as we speak.  I am presuming I can boot straight from the CD.  Regards the spec, the laptop is probably 2002 Toshiba Portege - not entirely sure of details - 512mb RAM, 40Gb HDU, Centrino chip and built in wifi.  Really struggled to get wifi working on version 5.04 and when I finally managed I realised I may need to start all over again.  
 
It's turning out to be quite an interesting Christmas project however.  Thank you for all your thoughts.  Very much appreciated.  
 
AlxR

---

### Post by coffeecat on 2009-12-22
> **AlxR said:**
> Regards the spec, the laptop is probably 2002 Toshiba Portege - not entirely sure of details - 512mb RAM, 40Gb HDU, Centrino chip and built in wifi.  Really struggled to get wifi working on version 5.04 and when I finally managed I realised I may need to start all over again. 

512MB RAM is enough. With an Intel centrino chip, the inbuilt wi-fi is almost certainly Intel. In fact, I believe it means that it is. Which is good, because Intel wireless in 9.10 should be hassle-free.

Did you find out which your wireless chipset was when you were struggling with 5.04? Things have come a long way since 5.04. You can test wireless from the live 9.10 CD. Simply left-click on the network manager icon near the top-right. If it shows your wireless network, click on it, enter your passkey where prompted and that should be it. Hopefully. :wink:

Good luck!

---

### Post by audiomick on 2009-12-22
Centrino is (was?) indeed a brand name for Intel chip sets, including WiFi, for mobile computers.

---

### Post by AlxR on 2009-12-22
OK - I am now back in the forums on the laptop - that is performing fine after a minor glitch in the updates procedure.  Ubuntu 9.10 now running happily - thank you for your advice.  

Next step get Flash running and the wireless (plugged into my router at present).  Any other key apps I should be installing from the outset?

AlxR

---

### Post by themusicalduck on 2009-12-22
A good package to install is the Ubuntu restricted extras package. This installs a bunch of codecs and will install flash for you. You can find it if you search in Applications > Software Centre.

As for getting wireless to work, start with going to System > Administration > Hardware Drivers to see if there is a driver you can install through that.

---

### Post by coffeecat on 2009-12-22
> **AlxR said:**
> Next step get Flash running and the wireless

For connection the wireless, see my previous post. It really is that straightforward.

For flash, why not install ubuntu-restricted-extras? Have a look in System > Administration > Synaptic for u-r-e. It gives you flash, Java, a whole load of multimedia essentials and MS core fonts. All the things that can't be included in a default install for licensing reasons.

---

### Post by SonicSteve on 2009-12-22
> **AlxR said:**
> Hi - completely new to Linux Ubuntu and to breathe life into an old Toshiba laptop I decided to install Ubuntu from an install disk I picked up some time ago. Well the good news is the laptop works a dream (SO much better than WinXP) but it turns out I have an unsupported version of ubuntu 5.04.

What is my easiest route to upgrade to the current version. I am comfortable using computers but completely new to Linux. What are my best next steps?

Many thanks,

AlxR

I know this is a little off topic but since no one else has asked.....

Where on earth did you dig up a 5.04 install CD? I was just too curious to not ask.

---

### Post by AlxR on 2009-12-22
Hello all,

The U-restricted-extras worked a treat.

The wireless connection has been a pain in the neck - not because of Ubuntu - but because of the rubbish Orange Livebox system.  Put it in pairing mode, switch off security, change channel, reboot, reboot, switch on security, ... I'm not sure how many times I did that until the Orange livebox finally accepted me back.  Anyway - thank you all for your help.  I now have a fully working Ubuntu system, a wife who believes that this has all taken too long, and a system that satisfyingly works so much faster than WinXP.

Oh - and to answer the question as to where the disk came from.  I'm a teacher and the BETT exhibition in January at London Olympia (the education technology show) must have had some disks that were being given away on a stand some years back that I managed to keep hold of one.

Thanks everyone.  Now to explore Ubuntu.

AlxR

---

### Post by slakkie on 2009-12-22
> **SonicSteve said:**
> I know this is a little off topic but since no one else has asked.....

Where one earth did you dig up a 5.04 install CD? I was just too curious to not ask.
old-releases.u.c ;)

---

