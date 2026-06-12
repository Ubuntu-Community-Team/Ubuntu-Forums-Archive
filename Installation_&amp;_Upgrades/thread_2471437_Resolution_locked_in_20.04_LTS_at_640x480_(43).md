---
title: "Resolution locked in 20.04 LTS at 640x480 (4:3)"
date: 2022-01-30
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2022-01-30
20.04 was working fine yesterday.
Today boot up and resolution locked in 20.04 LTS at 640x480 (4:3). Everything is very large and can't change it!
No other choices available when looking to change it in Displays.

Usually there are several choices in Displays to choose from.
All I get now is one choice, 640x480 (4:3)  

What is needed to set Screen Resolution back to (1920 * 1080) in Ubuntu 20.0.4?

---

### Post by Impavidus on 2022-01-30
Have you tried booting an older kernel? This can be done from the grub menu. It's not a long term solution, but at least tells us where the problem lies.

Which kernels are installed on your system? Can you tell a bit more on your graphics hardware? Do you use any proprietary graphics drivers? Have you installed a kernel upgrade yesterday? You can look it up in your logs: /var/log/dpkg.log.

---

### Post by cybrsaylr on 2022-01-30
Can't boot from another kernel. 

Believe grub got messed up when installing 20.04 on a partition made in a new 1TB SSD recently installed. 
After installing 20.04 I connected two other SSDs in my system that run Windows 10 and 18.04. 
The other SSD ran 14.04 and 16.04 and grub didn't give me any bootloader for 20.04. 

Would boot up by hitting F12 button shortly after powering up, then selecting the SSD desired and each one of those OSs would open and run fine with a grub bootloader. However 20.04 never showed any bootloader but started up when selecting the newly installed 1TB SSD from its F12 SSD choice. 

Meant to get around to repairing grub but haven't done that yet. In the mean time all ran well until today. Boot up today and 20.04 resolution locked up 20.04 LTS at 640x480 (4:3).

Made this post using 18.04 on one of the other SSDs in my system.

---

### Post by Impavidus on 2022-01-31
Try [boot-repair](https://help.ubuntu.com/community/Boot-Repair) and create a boot info summary. That may tell us which Ubuntu system is in charge of the grubs on your different hard drives. Normally, each of them should offer you to boot every installed Ubuntu with every installed kernel, but sometimes they may be outdated, not offering the latest options.

---

### Post by cybrsaylr on 2022-02-01
Ended up reinstalling 20.04 and this time leaving the other 2 SSDs plugged in, with the third new 1TB SSD where 20.04 was installed.

Now I get a full bootloader showing all 5 OSs, namely 20.04, 18.04, 16.04, 14.04 and Windows 10. They all run fine when selected.

However I only get to this bootloader after hitting the F12 button when powering up with the Dell splash screen being shown, then selecting that new 1TB SSD. 

Otherwise by trying to do a normal boot up I keep getting a black screen with a text saying, can't find device ..... 'grub rescue' is needed.

Don't know what to do?

---

### Post by Impavidus on 2022-02-01
That means that the first drive (first in boot order) has a broken grub. You may be able to change the order permanently in UEFI settings. Else, find out which drive has a broken grub and reinstall the grub on that drive. Choose which system you want to be in charge of that grub.

It's probably best to use the grub of the system you use most often. That one is best kept up to date. Besides, Ubuntu 14.04 and 16.04 are no longer supported, so no updates and not safe to use, unless you signed up for extended security support.

---

### Post by cybrsaylr on 2022-02-02
Impavidus thanks for the help so far.

Here's basically what happens now.

On normal boot up I keep getting a black screen with a text saying, Error, can't find device ..... 'grub rescue' is needed.

By hitting F12 button when powering up during the Dell splash screen, it goes to a list showing at the top, 480GB SSD, the 1TB SSD under, followed by the 120GB SSD under that.

When selecting the 480GB SSD choice, then hitting enter, a GNU GRUB version 2.02 bootloader appears showing the following order;

*Ubuntu, which is 18.04
  14.04
  Windows 10
  16.04

When selecting the 1TB SSD after pressing F12 button, it goes to the same list showing at the top, 480GB SSD, the 1TB SSD under, followed by the 120GB SSD under that.

When selecting the 1TB SSD choice, then hitting enter, a GNU GRUB version 2.04 bootloader appears in a black screen, showing the following order;

*Ubuntu, which is 20.04
  18.04
  14.04
  Win 10
  16.04

In this case all 5 OSs run fine when selected with the 1TB SSD choice.

Right now plan to use 20.04 on the 1TB SSD most often and have no idea how to fix the broken grub. 

I realize 14.04 and 16.04 are no longer supported but kept them back then to be able to go into them at times to easily move some fav files over to the newer current systems. Funny how the time does fly....lol.

---

### Post by Impavidus on 2022-02-02
> **cybrsaylr said:**
> 
When selecting the 480GB SSD choice, then hitting enter, a GNU GRUB version 2.02 bootloader appears showing the following order;

*Ubuntu, which is 18.04
  14.04
  Windows 10
  16.04Which indicates that Ubuntu 18.04 is in control of the grub installed on the 480GB SSD. That grub isn't aware of the existence of your Ubuntu 20.04 system. When you install the regular upgrades, it should eventually find it and offer to boot it.

> When selecting the 1TB SSD choice, then hitting enter, a GNU GRUB version 2.04 bootloader appears in a black screen, showing the following order;

*Ubuntu, which is 20.04
  18.04
  14.04
  Win 10
  16.04
So 20.04 is in control of the grub on the 1TB SSD. I guess that your broken grub is on the 120GB SSD.
> Right now plan to use 20.04 on the 1TB SSD most often and have no idea how to fix the broken grub.
So set the 1TB SSD first in boot order. How you do that depend on the details of your UEFI. Those aren't highly standardised, so I can't tell you.

---

### Post by cybrsaylr on 2022-02-02
> **Impavidus said:**
> Which indicates that Ubuntu 18.04 is in control of the grub installed on the 480GB SSD. That grub isn't aware of the existence of your Ubuntu 20.04 system. When you install the regular upgrades, it should eventually find it and offer to boot it.
This usually happened in the past when installing a new SSD but it hasn't happened so far for 20.04. Assumed it was some kind of auto-correct to fix bootloader.

> **Impavidus said:**
> So 20.04 is in control of the grub on the 1TB SSD. I guess that your broken grub is on the 120GB SSD.

So set the 1TB SSD first in boot order. How you do that depend on the details of your UEFI. Those aren't highly standardised, so I can't tell you.

Believe I fixed it by hitting F2 key when powering up to get into Setup. Over the years very seldom if ever used this F2 key so had to try figuring how it worked. 

Power up and after seeing the Dell splash screen, hit F2 key for Setup.
Then get into CMOS Setup Utility:
Click down to Boot Device Configuration, hit enter.
On 1st Boot device, 120GB SSD was listed first.
Changed that and made 1TB SSD as 1st Boot Device.
Hit F10 key to save & exit Setup.
Hit OK and PC went to Bootloader showing all 5 OSs. with 20.04 as default OS to boot first as was desired. 

So all seems to be corrected with bootloader. Did a quick test and all 5 Systems boot up and started and seem to run fine.
It was an easy fix once I figured out how to use the F2 key on startup, something I almost never used in the past.


Impavidus again thanks for the help.

---

