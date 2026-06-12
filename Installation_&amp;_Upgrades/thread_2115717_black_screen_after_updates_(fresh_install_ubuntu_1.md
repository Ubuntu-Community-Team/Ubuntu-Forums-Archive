---
title: "black screen after updates (fresh install ubuntu 12.10)"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by dumble on 2013-02-13
I tried three installations allready. In previous installations I thought it had to do with options I changed for optimizing ubuntu for SSD. Now I know it is not so, it is because of the updates right after installation.. 

Just after fresh install. I restart no problem. I update (+- 190mb of updates). I restart, it starts booting, I hear the login sound but only see a black screen. When I type in my password (blind) and press enter I get into ubuntu but the screen is all cracked up and unreadable.

Current setup is a dualboot.
Windows 8 x64 - on 1st SSD
2TB data partion minus 4GB for swap - on HDD
Ubuntu 12.10 x64 - on 2nd SSD

Hardware;
Gigabyte GA-Z68X-UD3H-B3 (rev. 1.3)
AMD Radeon HD 6950

All bios's/firmware are up-to-date

I have NOT installed the video-drivers. I still have to figure that out as well. IN previous installations it did not work via software sources - additional driver and than change to proprierty. But first things first, **How do I get rid of this black-screen problem?**

[B]
I can login[/B], if via grub bootloader go to advanced > recovery > resume.

---

### Post by dumble on 2013-02-13
problem fixed, I installed amd drivers via this method. This solved the problem:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

