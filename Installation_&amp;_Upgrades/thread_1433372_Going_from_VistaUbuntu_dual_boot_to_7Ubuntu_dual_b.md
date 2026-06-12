---
title: "Going from Vista/Ubuntu dual boot to 7/Ubuntu dual boot"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by BA_UO on 2010-03-18
Hello all, 

As you can tell from the thread title I am currently dual booting Vista/Ubuntu, and I have just received a free Windows 7 License through my school, and would like to now dual boot Windows 7/Ubuntu, and get rid of vista for good.

Is there any general instructions/guidance that someone with more experience give me?  

Tips/Do's/Dont's would be greatly appreciated.

Thanks in advance, 

BA

---

### Post by Mark Phelps on 2010-03-19
Your easiest solution, in which you would lose the least, and have to do the least work, would be an in-place upgrade from Vista to Win7.  But, since MS has really tightened up the in-place upgrade requirements for Win7, you can only go from like version to like version. For example Vista Home to Win7 Home, Vista Business to Win7 Pro, Vista Ultimate to Win7 Ultimate. All other installs/upgrades are fresh install.

Regardless of the kind up upgrade, you'll still have to reinstall GRUB afterwards because Win7 will rewrite the MBR.

---

### Post by BA_UO on 2010-03-19
Sooo, If I burn the ISO image of the windows 7 installer to disc, and restart the computer with the disc in, I will esentially have just windows 7, then have to re-install ubuntu after that?

Sorry if that's what you said, I just need it re-stated in noob-terms please ;)

Thanks, 

BA

---

### Post by Ozymandias_117 on 2010-03-19
> **BA_UO said:**
> Sooo, If I burn the ISO image of the windows 7 installer to disc, and restart the computer with the disc in, I will esentially have just windows 7, then have to re-install ubuntu after that?

Sorry if that's what you said, I just need it re-stated in noob-terms please ;)

Thanks, 

BA

Um. No. :P Basically, he is asking what version of vista you have (basic, home premium, ultimate) and what version of 7 you're trying to install.

Depending on that, it will be easier or harder.

---

### Post by oldfred on 2010-03-19
[LEFT]Reinstalling grub is just the boot loader in the MBR that starts the computer. Windows will automatically overwrite that and take over booting. Windows will not see the linux partitions so you Ubuntu install should be just fine. Of course any hardware changes may cause problems so you should have good backups.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[/LEFT]

---

### Post by BA_UO on 2010-03-19
Thanks for the info!

I am attempting to go from a Vista Home Premium to Windows 7 Professional...

---

### Post by Ozymandias_117 on 2010-03-19
> **BA_UO said:**
> Thanks for the info!

I am attempting to go from a Vista Home Premium to Windows 7 Professional...

Then when you're installing, you should be able to select your Vista partition and overwrite it. Then you will have to reinstall grub using a liveCD. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by BA_UO on 2010-03-21
Hello again, 

Well, my Windows 7 installation went well, but I am having troubles installing grub(2) so that I can run my ubuntu.

I folled the instructions here:

> Then when you're installing, you should be able to select your Vista partition and overwrite it. Then you will have to reinstall grub using a liveCD. [https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)

And I got this error:
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/2fe6947a-c977-4447-9654-b73eb1f0b7c0 /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly


Am I doing something really stupid for this not to work?

Any help is much appreciated.

Thanks in advance...

BA

---

### Post by BA_UO on 2010-03-21
Hello again, 

I got grub2 re-installed, but ended up using this link:
> [http://www.ohbuntu.blogspot.com/2009/11/repair-grub2-after-install-windows-7.html](http://www.ohbuntu.blogspot.com/2009/11/repair-grub2-after-install-windows-7.html)

I understand that I probably made a mistake when using the other set of instructions, but I found this link must easier to follow.

Hope it helps someone else out there!

Have a good one, 

BA

---

