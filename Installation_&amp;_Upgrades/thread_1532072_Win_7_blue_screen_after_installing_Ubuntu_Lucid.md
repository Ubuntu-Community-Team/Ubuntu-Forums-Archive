---
title: "Win 7 blue screen after installing Ubuntu Lucid"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Marcelo Ruiz on 2010-07-15
Hi all,

I've been a happy user of Ubuntu for years, but today I faced a mayor problem after installing Ubuntu.

I have a Toshiba Laptop with 2 hard drives:

+ sda
  -sda1 (System Partition)
  -sda2 (Windows 7)
  -sda3 (HD Recovery)
+ sdb
  -sdb1 NTFS (empty)

I wanted a dual boot with Windows 7 and Ubuntu Lucid, so I erased sdb1 and created using ext4:

+ sdb
  -sdb1 /boot
  -sdb2 /
  -sdb3 /home
  -sdb4 swap

After that I installed Lucid. So far, so good.

When I reboot, I see the Grub2 menu and I can load Ubuntu with no problems, but when trying to load Windows 7 it starts loading showing the animated icon and fails with an infamous blue screen of death.

Toshiba doesn't ship the computer with the original Win 7 DVD, the only choice users have is to create an image of a working installation, so using Win 7 DVD to fix Windows installation is not an option for me.

I checked the Win 7 partition for errors and everything seems to be fine. 

Unfortunately I had to return my new brand computer cause the charger was not working, so I cannot explore this further until I get a replacement... 

I am wondering if I did something wrong when I installed Lucid. Did anyone faced the same problem? 

I want to install Ubuntu Lucid in my girlfriend's laptop (another model of Toshiba with the same restrictions mine had)... but I am not sure if I will be able to deal with the consequences of a failure!!! :lolflag:

Please share your suggestions with this soon-to-be kamikaze boyfriend...

Thanks!!!

---

### Post by Marcelo Ruiz on 2010-07-16
Hi,

Well, if any of you ever face this problem (having an OEM Win 7 install with not repair disks), you can use the following links (info taken from [http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)) to download the windows 7 repair disk ISO and use them to fix the problem:

Win 7 32b -> [http://www.mediafire.com/?xjyozmnttnn]("http://www.mediafire.com/?xjyozmnttnn")
Win 7 64b -> [http://www.mediafire.com/?vmmyjwoihnl]("http://www.mediafire.com/?vmmyjwoihnl")

I hope this helps!

---

### Post by YesWeCan on 2010-07-16
To avoid certain death, next time physically disconnect the windows disk while installing Ubuntu. Once Ubuntu is booting ok, reconnect Windows disk and tell bios to boot Ubuntu disk first. Then in Ubuntu terminal type 'update-grub' to add Win to grub boot menu.

---

### Post by robpennington84 on 2011-05-22
I am having exactly the same problem. BSOD when trying to boot Windows 7 after installing Ubuntu 10.04. I have downloaded and created the Windows 7 (64-bit) recovery disk, and it comes up fine when I boot to it. But, none of the repairs work. Startup Repair does not work. Also, I do not have the original Windows 7 DVD (bought the laptop from HP, they didn't give me a disk). Also, I was dumb and did NOT create a system image file to restore to. Also, when I use a command prompt to run diskpart, it only lists Disk 0, which it says is invalid....

I know this post is old, but Google really SUCKS and I could not find anything similar to my problem except for this thread in this forum... Someone please help!

---

