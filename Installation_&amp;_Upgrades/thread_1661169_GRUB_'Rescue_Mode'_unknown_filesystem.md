---
title: "GRUB 'Rescue Mode': unknown filesystem"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by s.diamond on 2011-01-06
Hi,

I have installed Ubuntu on an old computer which was running Windows XP, installing Ubuntu alongside XP.

After the installation and restarting, I get the error that C/H/S values cannot be retrieved, and I'm given a grub rescue prompt. I've followed the instructions here [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

However, after I type ls, I get (hd0) and (fd0).

After tying ls (hd0), I'm given the error

error: unknown filesystem

The same happens when I try ls (hd0)/

I have not got a Windows XP installation CD for this machine as it was purchased second-hand without the reinstall disk. Is there anything I can do at the rescue prompt or will I have to follow Problem #1, Solution #2 here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I don't have any CDs or USB sticks lying around so will have to buy one if that's the case.

Cheers,

---

### Post by presence1960 on 2011-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by s.diamond on 2011-01-08
Hi Presence,

I've finally got this issue sorted now.

I found a spare CD lying around and put Linux Mint 10 onto it. Then, I put the CD in and booted from the CD, backed up my important files and went into the D drive where WUBI was installed and deleted the 'ubuntu' folder. I also deleted two other files I found in the D drive relating to WUBI, and went into the C drive, opened boot.ini, and deleted the Ubuntu entry from there. After that I installed Linux Mint and all is working now.

I run Windows XP on this machine also and when it starts I'm given the option to choose either Mint or XP. However, I've got a new problem which I hope someone can help with.

At first the Wireless worked fine on Mint and XP (using Belkin wireless adapter). However now today I used the PC and Windows XP would connect to my network fine, though Linux Mint doesn't.

I had the box selected to try connecting automatically but it wouldn't connect. Therefore I deleted the option and tried again, using WPA security, putting in the password etc and it just will not connect. However the network does display in the options as to which one to connect to.

Have you got any ideas what might be going on? Is this a driver issue? It connects to my network without issue using XP.

Regards

Scott


> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by presence1960 on 2011-01-08
> **s.diamond said:**
> Hi Presence,

I've finally got this issue sorted now.

I found a spare CD lying around and put Linux Mint 10 onto it. Then, I put the CD in and booted from the CD, backed up my important files and went into the D drive where WUBI was installed and deleted the 'ubuntu' folder. I also deleted two other files I found in the D drive relating to WUBI, and went into the C drive, opened boot.ini, and deleted the Ubuntu entry from there. After that I installed Linux Mint and all is working now.

I run Windows XP on this machine also and when it starts I'm given the option to choose either Mint or XP. However, I've got a new problem which I hope someone can help with.

At first the Wireless worked fine on Mint and XP (using Belkin wireless adapter). However now today I used the PC and Windows XP would connect to my network fine, though Linux Mint doesn't.

I had the box selected to try connecting automatically but it wouldn't connect. Therefore I deleted the option and tried again, using WPA security, putting in the password etc and it just will not connect. However the network does display in the options as to which one to connect to.

Have you got any ideas what might be going on? Is this a driver issue? It connects to my network without issue using XP.

Regards

Scott

I have never used wireless with linux. It does sound like a driver issue. There are a number of wireless chips that are not comaptible with linux or that require some tweaking to get them to work. I would suggest you start a thread in the networking & wireless category of the forum and get some help from someone with experience in this matter. Good luck!

---

### Post by s.diamond on 2011-01-08
Thank you very much, the support offered on here is terrific!

---

