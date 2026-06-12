---
title: "Bricked my laptop, now trying to install Ubuntu to fix it"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by RobbyHawkes on 2015-11-06
OK, I have been stupid.

I had a dual-boot Windows/Linux Mint setup on my laptop where I had to switch boot from UEFI to legacy BIOS to go from Windows to Linux and vice-versa. Not ideal, but it worked and I rarely used windows.

I was ssh'd into my Raspberry Pi and was formatting/setting up partitions on a new usb hard drive. Unfortunately, I had another terminal window open next to it and typed some nasty commands in there, thus destroying /dev/sda1 on my laptop. Whoops. Mint now no longer boots. Windows is still accessible.

I tried to install Ubuntu to fix it as I was sick of Mint, and although there is now an Ubuntu install there, it still won't boot. I tried to make it boot in UEFI and BIOS according to various tutorials but with no luck.

The situation now is: Windows works. Ubuntu is installed but doesn't boot. My linux-side data is backed up. I would like to end up with a working dual-boot Windows/Ubuntu situation. I don't care if this is achieved by switching UEFI/BIOS or what.

Any help would be greatly appreciated. Thanks in advance.

---

### Post by grahammechanical on 2015-11-06
Hardware specs? Partition layout? Have you followed the advice in this wiki page?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you considered using Boot Repair?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That is about it, really, Unless you run Boot Repair and get it to create the Boot Info summary. You will get a URL to a PasteBin link. Put the URL as a link into your thread then we can see for ourselves what the situation is. Pay attention to the recommended repair. You may wish to accept it. But, first let us see the Boot Info summary by creating a link to it.

Regards.

---

