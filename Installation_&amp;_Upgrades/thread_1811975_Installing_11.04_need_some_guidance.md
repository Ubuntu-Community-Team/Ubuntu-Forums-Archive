---
title: "Installing 11.04 need some guidance"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Spadje on 2011-07-25
Here is what I have 
Windows 7 Ultimate 64Bit
2x 150GB Raptor's Raid 0
1x 400 GB Seagate
1x 1 TB Seagate 7200.11
EasyBCD

I have tried on 3 occasions to get Ubuntu installed. Everytime it fails. I have done the customized install following a guide on here for 10.10 ( I read a post where they said the directions and pictures were close enough ) got it to install but never could get into Ubuntu would get error out of disc or the grub rescue. I then tried installing it alongside Windows 7 and that really messed me up I had to do a mbr fix and some other things just to be able to get back into Windows. 

I have since found other people who have had issues installing while their primary OS was on a raid. Is there anything you all can help me with? I would really love to be able to dual boot but so far I cannot figure it out.

Thanks,
Spadje

---

### Post by Spadje on 2011-07-26
*Bump*

---

### Post by Quackers on 2011-07-26
Is your system using so-called "fakeraid" - like Intel bios raid? Or is it hardware controlled?

---

### Post by Spadje on 2011-07-26
I guess it would be called a fake raid. It is Bios controlled I do not have a controller card in the system.

---

### Post by steve11911 on 2011-07-27
Hhmmm...Dual boot Windows 7 and Ubuntu on a Raid 0 array?...sounds a little like trying to skateboard blindfolded but...here we go:

First, I would back up all important data.(read: very possible face plant...) Then let's check a few important pages:

[http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Still on the board? Then read on:

[http://www.overclockers.com/forums/showthread.php?t=639115](http://www.overclockers.com/forums/showthread.php?t=639115)

[http://neildecapia.wordpress.com/2010/02/15/dual-booting-windows-7-and-ubuntu-karmic-9-10-on-a-raid-0-array/](http://neildecapia.wordpress.com/2010/02/15/dual-booting-windows-7-and-ubuntu-karmic-9-10-on-a-raid-0-array/)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
==
Raid 0 arrays are great if you have that need for speed but they are inherently dangerous.Please be prepared in advance to handle a disaster ...or two...
Let us know...

---

### Post by YesWeCan on 2011-07-28
You have a Windows raid and two other disks? Where are you wanting to install Ubuntu?
To avoid a skateboarding accident I would not put Ubuntu on the same raid as Windows, although I believe it is technically possible.

---

### Post by Spadje on 2011-07-28
Windows 7 is on the raid 0...not much on there but Windows and a few games that need speed for loading. I want to put Ubuntu on my 400GB drive that is blank at the moment

---

### Post by YesWeCan on 2011-07-29
Ah well, it ought to be possible.
For people who are installing Ubuntu for the first time I recommend putting it on its own disk (which is what you want to do so that's a good start) and physically disconnecting the other disks while you do it. This is not necessary but simplifies the decisions you have to make in the installation process and avoids the all too common problems caused by the installer putting the Grub boot code on the wrong disk by default. If you can easily disconnect the other disks (just pull out their power connectors) then that will make the install simpler.

Set your bios HD boot order to be 400GB disk first. Then boot Ubuntu live CD/USB. Choose "use entire disk" then install. After the install is finished, shut down and reconnect the other disks. Boot again into the new Ubuntu and run [COLOR="Navy"]sudo update-grub[/COLOR] to add the Windows OS to the Grub boot menu.

I assume that Grub 1.99 in 11.04 can boot a Windows RAID0. I'm not sure whether 1.98 in 10.10 can; it may not - but no harm in done. In the unlikely event that it doesn't, you can still boot into Windows by setting the bios to boot the RAID0 first. Then you can add Ubuntu to the Windows boot menu instead.

---

### Post by Spadje on 2011-07-29
Awesome will give that a go today.

EDIT: Unhooked all drives except the 400GB drive and when I boot I get Error: Out of Disk after the new install.

---

### Post by YesWeCan on 2011-07-30
Do you mean that you disconnect all but the 400GB disk, then installed Ubuntu to it, then rebooted (before reconnecting the other disks) and got that error?

If you only got that error after reconnecting the other disks then make sure the bios is set to boot your 400GB disk first.

If you get that error even when the 400GB is the only one connected and the bios is set to boot that disk, then something went wrong with the install. From the live CD please download and run this [FONT=Nimbus Sans L, sans-serif][SIZE=2]http://bootinfoscript.sourceforge.net/ and post the RESULTS.txt here inside code tags.
[/SIZE][/FONT]

---

### Post by Spadje on 2011-07-31
I had all the drives disconnected, installed ubuntu, rebooted, and then received the error. I will try downloading that link later today.

Thanks,

---

