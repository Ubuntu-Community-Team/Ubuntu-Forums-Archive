---
title: "Trying to install Ubuntu 14.04, Nvidia Geforce 6200"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by goonybird on 2014-05-30
Hello everyone.

I love Ubuntu, it's my all-time favourite OS. But I get extremely frustrated that it won't run on a desktop. I have 12.04 running on three laptops with absolutely no problem whatsoever. I've even had Puppy working on an ancient laptop. But desktops.....

I managed to get 10.04 running when it came out but after that nothing. Tried Lubuntu, Kubuntu, Edubuntu, Mint etc but nothing worked properly till Ubuntu 13.04. That worked great!!! 

Now I am trying to upgrade to 14.04LTS. I tried an upgrade but that failed so I wiped the disc with Paragon, formatted it, and went for a clean install from a downloaded iso. 

The installation seems to go OK untill the final reboot. The machine boots, checks for bootable media in the CD drives then goes to boot from hard drive. That's it. It just stops there. I have tried changing the boot order in BIOS but it still stops when it gets to booting from hard drive. 

I just don't understand why I can get Ubuntu working on a laptop but not on a desktop.

---

### Post by LastDino on 2014-05-30
What is this desktops config?

---

### Post by goonybird on 2014-05-30
Mobo; Gigabyte 7vt600p-rz
CPU; Amd athlon 2.6
Ram; 3Gb
Graphics; Agp, Geforce 6200, 512mb
HDD; one 300gb sata used for storage. two x ide - one 60gb used for storage, one 40gb [maxtor] used as system disc

---

### Post by LastDino on 2014-05-30
And which disk are you using for Ubuntu? Are you disconnecting others during installation or not? Is there any other OS on those other Disks? 

I'm not well aware of AMD CPU terminology, but I'm working under assumption that your processor is good enough here.  

Have you tried pressing F6 and booting from nomodest?

---

### Post by ubfan1 on 2014-05-30
To emphasize the above comment:  Not every Athlon is 64 bit, so the 32 bit ones would take the i386 iso, NOT the amd iso (which is 64 bit).  Your symptom is that of trying to run a 64 bit installer on a 32 bit machine.

---

### Post by goonybird on 2014-05-31
PS. I also tried running it live off the dvd and it seemed to be fine.

---

### Post by mörgæs on 2014-05-31
> **ubfan1 said:**
> Your symptom is that of trying to run a 64 bit installer on a 32 bit machine.

No, it would have failed from the beginning.

Goonybird, you should try something lighter like X/Lubuntu. Please see the link in my signature for more information.

Also the nomodeset boot option is worth trying.

---

### Post by ubfan1 on 2014-05-31
The installer may be able to install to any disk, but can the motherboard boot from any disk?  Try moving the disk cables around so the system disk is a Primary/Master

---

### Post by mörgæs on 2014-05-31
Ubfan1, your suggestions are a bit too imaginative. We know that the hardware worked for 10.04 so cable mismatch is not likely.

Please let the thread rest until original poster returns.

---

### Post by oldfred on 2014-05-31
Classic nVidia black screen issue. Exactly the way my system with nVidia does not boot.
But full Ubuntu will not work either. Lubuntu probably or maybe Xubuntu.

And OP does not get grub menu as it is only install, so it just boots but needs nomodeset and does not have it.

You have to hold shift key from BIOS until grub menu appears. 
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Yours also is an older nVidia card so you will need one of the legacy drivers. Looks like the 304.xx is your version:
      
 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by grahammechanical on 2014-05-31
Ubuntu 14.04 installs the latest proprietary video drivers. I have heard that Nvidia are in the habit of droping support for what they call obsolute graphic cards. You could try installing without ticking "Install third party software." Then the installer will not install an Nvidia driver but use the open source driver Nouveau. That might be suitable but if you find that you need an Nvidia driver, then the software centre has nvidia 173 and that is said to support Nvidia cards from GeForce series 5 to Geforce series 9. 

After installation you can use the software centre to install Ubuntu Restricted Extras to get the video and audio codecs that you did not get during the install.

Regards.

---

### Post by mörgæs on 2014-06-02
Just so people don't get scared:

Correct, Nvidia support their old cards back to the 5 series (and maybe longer), which means hardware from 2003. I think we should be satisfied with that. If people want to use even older cards there are open source drivers available.

The problem with short support is mainly AMD, not Nvidia.

---

### Post by goonybird on 2014-06-03
Hi folks! Sorry to be away so long. 

It looks like one of my replies didn't post. Sorry.

Anyway, I was trying to install to the 40gb drive as the only OS, giving it the whole drive. That was always the master. I did try disconnecting the other drives but that made no difference.

Your comments all give food for thought. Both my desktop PCs are similar - Gigabyte boards with AMD socket A chips and the same graphics card. 

However the other machine is running windows 7 alright.

Although I had Ubuntu 13.04 running OK on this one I don't seem to be able to update. As you say, it could be outdated equipment. I tried going backwards to 12.04 LTS but that didn't work either.

I've now tried Lubuntu 14.04 as suggested and that's working, but no flash. That's evidently an issue as you say, although flash works on the Windows 7 machine.

---

### Post by LastDino on 2014-06-03
Adobe Flash?  It is available in Ubuntu software center. It's not a bug or problem, it's just not installed by default as it is not open source. Also, install ''restricted extras'' if you haven't already from software center.

---

### Post by mörgæs on 2014-06-03
No recent Flash is going to work on a socket A.

I guess most people would disagree that it's neither a bug nor a problem, but anyway it's a fact. 

A workaround is installing an old Flash version but I don't recommend it.

---

### Post by goonybird on 2014-06-19
Hi.

I now have Lubuntu running on both Socket A machines. This one is dual-booted with Windows 7, but I have had to buy a bigger hard drive to give them both enough room. At least I know it works.

Still can't play BBC news video though. There are several flash plugins installed in Firefox but nothing plays. Tried disabling some in case of conflict but to no avail so left 'em all on. Same on both Lubuntu intallations. Oddly enough, the content will play through Firefox on Windows 7. Ah, well.

Guess as Socket A is so old gonna have to think about upgrading hardware at some point. Still it's usable enough at the moment so Lubuntu will extend the life of the machines a bit longer. 

The boys like playing Minecraft and it works fine as long as the graphic options aren't too high. They can LAN the game a lot better/easier with 'Buntu than Windows so they are happy.

---

### Post by goonybird on 2014-06-19
PS...

I also meant to add - Thankyou all very much for your thoughts and suggestions. It is much appreciated.

---

