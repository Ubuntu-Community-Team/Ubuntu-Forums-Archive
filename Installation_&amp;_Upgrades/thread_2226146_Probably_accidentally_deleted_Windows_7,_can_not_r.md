---
title: "Probably accidentally deleted Windows 7, can not run Ubuntu"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by j_circuit_z on 2014-05-25
EDIT: TYPO in thread title, I CAN NOT run Ubuntu

I posted this in the Other OS's section as well ([http://ubuntuforums.org/showthread.php?t=2226140](http://ubuntuforums.org/showthread.php?t=2226140)), I wasn't sure exactly where to put it? I suppose perhaps more here because the problem originates from trying to use Ubuntu.

So I was interested in trying out Ubuntu. I downloaded the .iso and put it on a USB and went about using it without installing it. I was switching between Windows 7 and Ubuntu and everything was fine until I decided to try and install it and then partition my harddrive.

 Admittedly, I didn't know very much of what was going on, the guide I was using said it was easy and straight forward, so I figured I couldn't mess anything up too bad, and honestly, it didn't let me do anything (as far as I know). I was attempting to partition my hdd and it was telling me, if I remember correctly, that I hadn't chosen a drive to partition. So I was like whatever, restarted my laptop and booted up in Windows to try to figure out what was wrong online. I decide to go back to Ubuntu and then this go around I accidentally click on the wrong option regarding how to install it and chose to completely wipe my hdd. The first screen to show after selecting that option asked for my location on the map geographically. I didn't choose anything, I didn't continue on, I just shut down the laptop after that and then tried booting back into Ubuntu.

 Trying to reinstall Ubuntu leads me to the Ubuntu startup screen (4 circles) that never progresses. If I try to boot it without installing, I get the startup screen that within 4 seconds goes to a blank black screen.

 So I try booting Windows 7 and I get a black screen with a blinking "_".

 I try doing a system restore of my harddrive, which leads me to a screen asking me if I really do want to do a system restore, yes or no. I enter no and nothing happens, I can continue moving the cursor left or right between the two options, but if I enter yes then the screen locks up and you can't move the cursor and stays on the same gui.

So I start up boot repair ([[COLOR=#dd4814]http://sourceforge.net/p/boot-repair-cd/home/Home/[/COLOR]]("http://sourceforge.net/p/boot-repair-cd/home/Home/") to be clear), select the recommended repair, and I get a boot repair dialog saying

 "Please enable a repository containing the [Linux] packages int he software sources of Ubuntu 14.04 LTS(sda1). Then try again."

 then it generates a sources.list file with:

 "deb [[COLOR=#dd4814]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") trusty main restricted
 deb [[COLOR=#dd4814]http://security.ubuntu.com/ubuntu/[/COLOR]]("http://security.ubuntu.com/ubuntu/") trusty-security main restricted
 deb [[COLOR=#dd4814]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") trusty-updates main restricted"

I pressed OK on the first dialog box and now I got a new one:

 "Please enable a repository containing the [grub]2 packages int he software sources of Ubuntu 14.04 LTS(sda1). Then try again."

 And then that's all of it. I'm then left with the initial boot repair dialog where I can choose to do the recommended repair again.

 I suppose it tells me what to do from here but, I'm not sure how I'm supposed to go about "enabling a repository"

I then tried using the boot-repair-disk to restore my MBR, which doesn't seem like it was the right decision now in hindsight. Now when I try to boot Windows 7 I just get a window saying "Missing Operating system" as well as some other info. Lol, well, perhaps, we can at least get Ubuntu running

Yet, the problems are still the exact same when trying to run Ubuntu.

 Any help would be greatly appreciated. Thank you very much in advance.

---

### Post by oldfred on 2014-05-26
STOP using system.

If it is saying Ubuntu is in sda1, then you have erased drive and at least partially installed Ubuntu to the entire drive.
Boot Ubuntu live installer and add testdisk to it. 

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

    
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If testdisk shows old partitions, you may be able to get them back, but probably not as bootable as parts of drive were overwritten with install.

---

### Post by j_circuit_z on 2014-05-26
I'm unable to boot into anything, though. I try the live installer and I get stuck in the loading screen.

---

### Post by oldfred on 2014-05-26
What system and video card?
Did you need boot parameters when you booted installer before. Or perhaps the installer installed its boot loader to the flash drive in effect corrupting it?
You have to have a working repairCD or flash drive to be able to make any repairs. 
Or remove hard drive and install into another working system.

---

