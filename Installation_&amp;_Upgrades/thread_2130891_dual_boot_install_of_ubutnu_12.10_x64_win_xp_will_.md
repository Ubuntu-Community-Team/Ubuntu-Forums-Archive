---
title: "dual boot install of ubutnu 12.10 x64 win xp will not boot into ubuntu"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2013-03-30
I just installed 12.10 on a drive that already has an xp installation. When I boot the computer, I get the grub menu and select Ubuntu. The screen just goes black and I have my mouse pointer, but it just stays that way. I can boot into xp with no problem.

I choose custom partitioning and added a 4GB swap partition right after the xp partition. Then I added a 20GB ext4 partition for the install and selected / as the mount point. For the location of the boot loader, I selected the drive that the OS is on. This part of the installer is very cryptic. You would think that by now someone would have figured out a simple and straight forward way of setting up the partition and grub options, maybe the next version will be better. As far as I could understand what I was selecting, I installed the bootloader to the MBR of the driver where Ubuntu and windows are installed (sda). I'm not sure what the grub install location would have to do with a boot issue, especially since grub loaded and works for windows, but that was the part of the installer that was the least clear. Looking at the partitions from inside windows, both the swap and root partitions are there and have been formatted.

The install seemed to go smoothly and there were no errors indicated. When the rig restarted after the install, I was not able to boot into Ubuntu. Should I try super grub or boot repair disk, or should I install again?

Any suggestions?

**[COLOR="#000080"]LMHmedchem[/COLOR]**

---

### Post by oldfred on 2013-03-31
Sounds like a video issue. Do you have nVidia? I have to use nomodeset on first boot after install until I get nVidia driver installed. Use e on grub menu and change quiet splash to nomodeset.
With 12.10 you have to install headers first to get nVidia (or some other drivers) to install correctly.

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)


        Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by LMHmedchem on 2013-03-31
Thanks for the links, I will look at installing the nvidia drivers since I have an evga card. For some reason, when I started up today, I choose the second ubuntu option and that took me to a screen where I could select normal or safe mode. I selected normal and it booted right up. It seems to be fine now, at least as far as booting goes.

As far as the rest of the OS, you can register another vote for those who despise the Unity desktop. Talk about replacing functionality with useless flash. This desktop does nothing, but at least it looks nice doing it, so I guess that makes up the difference.

As a programmer, I really need actual tools, like a package manager, and the ability to actually configure the environment, not just watch pretty graphics effects (ok, I do that too when it gets really late). I have heard that you can revert to a more reasonable desktop and regain the necessary functionality, so I would really appreciate a link to some instructions. I think that for an OS that has always been the choice of users who want to configure there system the way they like it, some of these options would have been in the installer in the first place.

**[COLOR="#000080"]LMHmedchem[/COLOR]**

---

### Post by oldfred on 2013-03-31
gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

Others will have different suggestions. Some of them.

 Unity alternatives/info Hedgehog1
[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

If you do not like Unity, use K/L/X ubuntu or the DE/ WM of your choice. 
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

---

### Post by leslo911 on 2013-04-01
I use Windows 8 with a 30 Gbs partition accomplished through Ubuntu itself by way of the Wubi installer. The same problems with dual boot have been going on in 12.04 ans 12.10. These boot problems were going on Windows 7 too.

Have Linux 12.04 as my exclusive operating system on a netbook. There are no problems starting up that system. My dual boot with Vista and 12.04 works every time without fail. all systems are 64 bit native.

The issue with not loading Ubuntu in Windows 8 maybe the way you click on the Ubuntu system. I could be that you need to restart the computer redundantly for the system to recognize the boot loading sequence. In any event, Ubuntu, the best of the Linux distros is a stone age operating system with tons of foibles.

I make cash donations to Ubuntu on occasion. They have to come out of the era of cave paintings and stone implements to compete with Windows. But do they really want to be competitive?

I have always found the Wubi installer the best path to a dual boot.  Have used Linux ditros for a real long time.

If they would improve their hardware to include Blu-Ray, 3D, fingerprint and facial recognition they would have a solid operating for sale.

Wubi the mess. Delete your Linux partition and Wubi a partition. Man, how easy is that.

Don't start cold with Linux. Open Windows then restart. Choose Linux after the restart. it may be enter instead of clicking.

---

