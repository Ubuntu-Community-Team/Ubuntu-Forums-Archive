---
title: "Installation of Ubuntu on XPS-13"
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by gerald17006 on 2020-02-05
Dear all,
I have installed Ubuntu 18.04 on Dell XPS-13 using the UEFI. But most of the time some of the applications are not working; i can only have read-only write to directories. When i restart or startup the system i am having snapd issue which i have to fix using the following commands:
fsck -fy /dev/sda1
and then reboot 

Please how can i fix this issue permanently?

---

### Post by CelticWarrior on 2020-02-05
Something is really wrong if you need to be error correcting your drive all the time. Yes, that's what fsck does.

---

### Post by yancek on 2020-02-05
> i can only have read-only write to directories. 

Not sure what your problem is but have read only access to anything as a normal user outside that user /home directory is standard.  More specifics on what applications you are using and what exactly the problem is might help someone to help you.

---

### Post by gerald17006 on 2020-02-12
Thanks everyone for your responses but what i want to know is XPS-13 **(Intel® Core&#8482; i7-8565U CPU @ 1.80GHz × 8 )** compatible with Ubuntu 18.04.3? Because my laptop is showing:
 thermal sensor failure;
steps to correct the SSD drive **(**[COLOR=#000000]**fsck -fy /dev/sda1)** 
****and then ****
initramfs [/COLOR]

---

### Post by mörgæs on 2020-02-14
With a CPU this new you should not consider 18.04. It was released before your computer entered the market, and even though new kernels have been added to 18.04 over time it's still yesterday's news.

19.10 is a better choice.

---

### Post by oldfred on 2020-02-14
Seems to be various models of XPS 13. 
These may or may not be similar.

       Dell XPS13 9370 Developer Edition - Install Windows after Ubuntu
[URL="https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp"]https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp
      [/URL]
 Dell 9380 Dell has 18.04 image with correct drivers
[https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems](https://askubuntu.com/questions/1136409/new-xps-13-9380-with-ubuntu-18-04-flicker-problems)
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Dell XPS 13 9380 + Intel Core i7 8565U Ubuntu Linux Performance Benchmarks
[https://www.phoronix.com/scan.php?page=article&item=dell-xps-9380&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps-9380&num=1)
Dell XPS 13 What to fix with the fresh factory Ubuntu 16.04 April 2017 Updated to 18.04
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en) 
    [URL="https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp"]
[/URL]

---

