---
title: "Clean install to replace one side of an Ubuntu-Ubuntu dual boot"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by col48 on 2013-03-05
I have a dual boot with Lucid Lynx 10.04 32bit on one side and Hardy Heron 8.04 32bit on the other.  Unlike many dual-boot systems there is no Windows system.

The Hardy is never used now and I want to replace it with Precise Pangolin 12.04 _64bit_ without affecting the Lucid partition so that I can make sure I am happy with the Precise settings as I gradually migrate to it and have no functional down time for Lucid.  I've got a liveDVD to start from.  

There must be some instructions around somewhere, but all I can find assumes a clean install to wipe the whole hard drive, which I do not want to do and should be unnecessary.

Can someone point me in the right direction, please?

---

### Post by oldfred on 2013-03-05
As long as you know which partition it is, just reinstall to that partition. You have to use Something Else or manual install, choose partition, select it as / (root) and format as ext4. If you have a separate /home you can add that also, if previous /home you can not format it to preserve data otherwise formatting will erase everything. If you have swap it will auto find it.
Also select to install grub2's boot loader to the MBR of the same drive and then choose to boot that drive from BIOS.

       Install to external drive. Also any second drive. Shows the manual install screens.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by col48 on 2013-05-06
oldfred: Thanks for your encouragement - I almost missed the instruction about changing BIOS; hence initial puzzle that restart did not offer 12.04 as an option - reason was that 10.04 is on sda3 and 12.04 on sdb1.

Now for the task of getting used to 12.04 and getting everything I want up and running..... I hate change, which is why it took 2 months to get up the courage!

---

### Post by oldfred on 2013-05-06
I also have 13.04 in another partition, but primarily boot 12.04. Previously I had 10.10, but it expired.
I stayed with 10.10 as I was not a fan of Unity. Unity has been improved a lot but I still like the old menus and my monitor is the old 4:3 and menu on left uses important screen space where top & bottom panels do not. 
So I reverted to the gnome-panel mode.

 gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by col48 on 2013-05-06
I'm very much with you on the subject of Unity.  I've gone for the Classic look as well.  And changed the colours - white on black is not very user-friendly for this user!  I like to see the gaps between icons etc.

I also had to change the screen from 1600x1050 (which put some of the screen off limits - including the 'cog-wheel' icon!) to 1600x1000.  I note that 1600x1200 functioned OK but the proportions were wrong.

---

