---
title: "Ubuntu 16.04.2 - Dell Inspiron 5565 AMD FX 9800P stuck on initial installation screen"
date: 2017-07-19
forum: Installation &amp; Upgrades
---

### Post by deepak.s on 2017-07-19
Hello everyone.

I have tried to google about the installation problem I am having and have had no luck.

I am trying to install Ubuntu desktop 16.04.2 LTS. on a Dell Inspiron 5565 new laptop. Has below configuration:

[B]CPU: AMD FX 9800P RADEON R7, 12 Compute cores, 4C+8G 2.7GHz processor.
RAM: 16GB
System type: 64bit, x64-based processor
OS: Pre installed with windows 10.
GPU: ATI Radeon MX455 4GB[/B]

I followed the installation guides every step of the way.

1. Downloaded the iso.
2. Verified the download.
3. Prepared bootable USB using rufus.
4. Created a separate partition of unallocated space using windows disk management utility.
5. Plugged in the USB drive and did a reboot to enter the boot menu.
6. Could recognize and boot from the ubuntu USB.
7. The process starts, but just gets stuck showing ubuntu logo (Not even started the installation process like choosing the partition and all. Once I choose "Install Ubuntu", the progress bar begins to load and then stops after a while).

I read in many posts that this could be because of the safe boot being enabled. So **tried disabling safeboot. No luck.**
Also **tried by changing boot option to legacy. Still the same.**

Also while creating the bootable USB using rufus, I initially chose the recommended option of **ISO image mode**.
Then since this didn't work, I also tried using the **DD image mode**. Had no luck either ways.

I tried to gather some logs. Apparently I should have been able to access the CLI as to see if any error are showing up during installation by pressing F6. This is also not working for me.

I found a post similar to my situation on askUbuntu [https://askubuntu.com/questions/893425/how-can-i-successfully-install-ubuntu-16-04-2-on-a-dell-inspiron-5565-which-has]("https://askubuntu.com/questions/893425/how-can-i-successfully-install-ubuntu-16-04-2-on-a-dell-inspiron-5565-which-has")here but was of no use.

Any suggestions or guides in helping me to get ubuntu installed on my new laptop is greatly appreciated.

**PS: I don't mind getting rid of windows completely and using just ubuntu if I can get everything to work. I used to use ubuntu on a daily basis about 8 ~10 years ago.**

---

### Post by deepak.s on 2017-07-19
Quick Update:
Found this link: [http://en.community.dell.com/support-forums/laptop/f/3518/t/20012390](http://en.community.dell.com/support-forums/laptop/f/3518/t/20012390).
Although I wasn't sure if it was the same error message **_[SIZE=3]I thought of giving 16.04.1 a try. Currently installation is in progress[/SIZE]_**
Seems like there is some issue with Installing Ubuntu on the above Dell laptop backed by aforementioned configuration.
Wish I was able to copy the error message.

---

### Post by oldfred on 2017-07-19
Some Dell seem to have RAID or Intel SRT on. Drives should be set to AHCI.
Make sure you have latest UEFI from Dell.

 Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889) 
      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)

---

### Post by deepak.s on 2017-07-19
Thanks for the response. As of now I could get the 16.04.1 set up. I will go through these links and will try to set up 16.04.2 and post back on the status.

---

### Post by BenginM on 2017-07-20
Salutations!

I could only suggested you try to boot with the kernel boot parameter but i can't remember the correct one! .. in the meantime try booting the 17.10 livecd/usb instead.

---

### Post by crazyaxe on 2017-10-16
You just need a very recent kernel, the last kernels have the **amdgpu** driver. You need at least the 4.13.x.

---

