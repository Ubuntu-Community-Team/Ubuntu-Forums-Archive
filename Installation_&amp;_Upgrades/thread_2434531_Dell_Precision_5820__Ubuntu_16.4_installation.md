---
title: "Dell Precision 5820 : Ubuntu 16.4 installation"
date: 2020-01-07
forum: Installation &amp; Upgrades
---

### Post by pande824 on 2020-01-07
I have recently bought Dell Precision 5820 workstations (without any OS installed) and have been trying to install Ubuntu 16.4 via Live USB image
but no success so far. The installation has stuck when I chose “Install Ubuntu” and the black screen came up always.
I tried some changes (such as, updating BIOS version, deactivate secure boot etc.) following other posts made on the forum.
 
At the end, I tried to install Ubuntu 18.4 in the same conditions and I could make it installed without any issues.
 
**Does someone advise me why Ubuntu 18.4 can be installed easily but I can not with 16.4?**
What made this difference?  I need 16.4 version working in the PCs as I want to install a specific software that can work in 16.4 version.
I am not so much familiar with Ubuntu so any advises or comments are appreciated!!

---

### Post by dragonfly41 on 2020-01-07
i have a Dell 3268 which came with Windows 10. From within windows 10 I then shrunk the internal partition to half size to allow unallocated space to install Ubuntu 16.04 (this was more than a year ago before i was ready to try 18.04).

I have since added two external drives with Ubuntu 18.04 on each but that is another story. 

You could bootup your LiveUSB 16.04 and choose "Try Ubuntu" before "Install Ubuntu" to see if it works. "Try ubuntu"  should work. I really don't know why you have different installation results across the two distros.
You have gone into your BIOS settings to select UEFI and disabled Secure Boot?

However, I have personally not yet found any apps which ran on 16.04 but not 18.04.  What errors do you have if it does not run on 18.04?  It could be a simple factor. if you run the app in 16.04 [list its dependencies.]("https://askubuntu.com/questions/128524/how-to-list-dependent-packages-reverse-dependencies")

---

### Post by CatKiller on 2020-01-07
> **pande824 said:**
> Does someone advise me why Ubuntu 18.4 can be installed easily but I can not with 16.4?
If you chose a configuration with Nvidia graphics, needing to use nomodeset during the install and initial boot is common. 18.04's newer version of nouveau may have been better at automatically detecting the resolution than 16.04's.

---

### Post by crip720 on 2020-01-07
If it was made after 2016, then Ubuntu 16.04 might not have the right drivers for it.  If you let us know what software you need, maybe someone can tell if it will work with 18.04

---

### Post by oldfred on 2020-01-07
Dell often develops its own drivers for new hardware. See sputnik.
And then it releases that software. But kernel, drivers and then distributions will not have that till later depending on release cycle. 

New Dell 2020 & Sputnik history
[https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)

---

### Post by pande824 on 2020-01-07
[ATTACH=CONFIG]284761[/ATTACH]

Thank you very much for some comments.
I have tried "Try Ubuntu before installation" but the result was same.

Yes, the PC has Nvidia graphic card and tried "nomodeset". However, even with "Try Ubuntu before installation", the process stooped
after showing the attached image.
As you can see, there are two **"Failed to start clean up my mess left by odns-up".**

Do you know what I can do further to proceed with the installation?

Unfortunately, the software I plan to install on this PC was provided by my supplier and it ca be only supported by 16.4 version.
So I need to use 16.4 version otherwise I need to work on modifications with the supplier.

---

### Post by dragonfly41 on 2020-01-07
Through google there are threads discussing that error pattern ..

[https://askubuntu.com/questions/761468/ubuntu-will-not-boot-help](https://askubuntu.com/questions/761468/ubuntu-will-not-boot-help)

Thermal Daemon Service seems relevant to follow up.

---

