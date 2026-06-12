---
title: "Ubuntu 16.04 - Cannot boot or install on Dell XPS 13 - watchdog soft lockup"
date: 2019-07-29
forum: Installation &amp; Upgrades
---

### Post by glaserf on 2019-07-29
Hi there,

I am desperately trying to install Ubuntu 16.04 LTS on my Dell XPS 13. I disabled safe boot, set SATA mode to AHCI and created a bootable USB drive with Rufus under the already installed Windows 10. To see the USB drive as a bootable device, I however had to enable "Legacy Boot" in the Dell BIOS.

When I do nothing after selecting the device, I get the following error: watchdog: BUG: soft lockup - CPU#x stuck for 22s! In the call trace below the first message is acpi_pm_good_setup. the last one ret_from_fork.
When I do press a key after selecting the device, I get into what I believe is GRUB. Contrary to many posts on the internet, I however cannot press 'e' to access advanced boot options. I have to press F6, this will open a menu from below and at the same time let me edit the option line. Similarly, I can only press Enter after editing, not F10 as suggested many times on the internet, if I do press F10 i get asked if I want to suspend the PC, this really confuses me.

I tried many options already, nomodeset, noacpi and similar - all without success. The error stays the same.

Does anyone have an idea? Thanks.

---

### Post by rsteinmetz70112 on 2019-07-29
These errors are often due to an unstable power supply. 
I'm not familiar with this model but it may also be getting some of the CPU parameters wrong.

---

### Post by pmaff on 2019-07-29
I had similar errors on a MSI GE63 Raider laptop with a SuSE Leap  15.0.
In my case the SuSE kernel seemed to be too old for this, which was the reason why I tried Ubuntu 18.04 LTS on this laptop which now works for about a year. 
There is some description from me in German here:
[https://forum-de.msi.com/index.php/topic,114680.0.html](https://forum-de.msi.com/index.php/topic,114680.0.html)

---

### Post by oldfred on 2019-07-29
Have you updated UEFI from Dell?
And if SSD updated firmware?

Generally better to use newest LTS version of Ubuntu.
What version of XPS13?

Very newest has special version from Dell with latest drivers.
       Dell 9380 Dell has 18.04 image with correct drivers
[https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems](https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems)
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Dell XPS 13 9380 + Intel Core i7 8565U Ubuntu Linux Performance Benchmarks
[https://www.phoronix.com/scan.php?page=article&item=dell-xps-9380&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps-9380&num=1)
Dell XPS 13 What to fix with the fresh factory Ubuntu 16.04 April 2017 Updated to 18.04
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
    
Dell typically has some driver changes that will eventually get into kernel & then distributions.
       Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

---

