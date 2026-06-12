---
title: "Serious issues - Ubuntu broke down, re-installing it doesn't work! HELP!"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by moljac024 on 2007-05-24
I am begging for somebody to respond and help me, i have a serious problem...PLEASE! 
I will try to write everything i did during the course of the last few days, so forgive me if the post is a little long but i desperately need help.

A few days ago i thought i'd give Linux a try and i downloaded Ubuntu 7.04. I then installed it for the first time and everything went smoothly - it detected my internet connection without any trouble, downloaded updates, recognized every piece of hardware (didn't even need any graphic card drivers for my ATI x550). I installed everything through synaptic package manager since i am new to linux. I re-installed the whole OS several times and every time the install process went flawlessly.

 I have a 160 GB S-ATA MAXTOR hard disk and a 120 GB NTFS partition on it where i keep all my data.
Naturally i installed Ubuntu on the remaining 40 GB (i allocated 3 GB of that to swap, the rest was root partition).

I then learned that i couldn't write to ntfs and a little googling presented me a solution - ntfs-3g and the configuration utility based on it. So i installed that through synaptic, enabled write support on ntfs and it all worked nice.

Then i installed beryl and it would cause frequent system hang ups and my only choice in those situations would be a hard reset (Beryl was set to fall back to metacity in case of a crash but i don't know why it didn't do that).

So, today i am reorganizing my NTFS partition (moving and deleting folders) and beryl freezes my system in the middle of a files moving operation. I did a hard reset and found the files weren't moved (they remained in their original location), but when i tried creating folders on that partition i would get a I/O ERROR and COULD NOT CREATE FOLDERS! I tried using the ntfs-config tool to disable and then enable write support, i tried restarting ubuntu and nothing could fix it.

I then re-installed Ubuntu from scratch and for the first time it wouldn't  download language packages and i would have to skip that part of the install. The rest of the install finishes and when i boot into Ubuntu it informs me that there are 5 updates available (when i know there are more) and i get all sorts of errors from update manager while trying to update and synaptic won't search for packages online.... i've tried re-installing ubuntu three times!

Please help!  Is there a way to check what could be causing this ? Did something screw up my hard drive ?

---

### Post by shad0w_walker on 2007-05-24
It sounds lke NTFS3g is putting your system into read only mode because the drive wasnt unmounted properly. Iv had this problem a couple of times before, the easiest way to fix it should be to restart into windows, it will run the file system check when you boot up. That should sort things out for you and you can reboot into ubuntu and get normal access again.

There are a couple of ways of fixing this from ubuntu but i havent looked into them in detail, this should solve the problem anyway.

P.S. I think your beryl problems are caused by your ATI card. I used to run a Radeon 9600XT in my system and everytime the drivers got poked in the wrong way it would hardlock. Might be an idea to disable it if your doing important things.

---

### Post by moljac024 on 2007-05-24
Ok thanks, i've tried unmounting the volume and it says : Can't unmount volume (under details -  volume disagrees with fstab)

Hmm,I really wouldn't want to load into windows ever again :-), is there an alternative solution ?
But how can this be related to update repositories ? 

Also i've installed Ubuntu and beryl on my girlfriend's computer without graphic card drivers (She has an ATI 9200SE), but beryl reverts to metacity when it crashes on it. Why doesn't mine do that ?

EDIT : I've tried creating a folder in my home directory and it created it....so it doesn't look as the system is in read only mode, don't see why updates won't work...

---

### Post by moljac024 on 2007-05-24
Anyone ? Help ?

How about if i burn all my data to DVDs and then try installing ubuntu again, only this time formating the whole drive as ext3 ?

(Sorry for double posting, i really need help here, didn't sleep all night....)

---

### Post by mozetti on 2007-05-24
> **moljac024 said:**
> Anyone ? Help ?

How about if i burn all my data to DVDs and then try installing ubuntu again, only this time formating the whole drive as ext3 ?

(Sorry for double posting, i really need help here, didn't sleep all night....)

You could do that, or format it as FAT32 and that way both Windows and Ubuntu can read it natively. FYI, if you're not planning to use Windows much anymore, then don't use a file-system that is difficult at best for Linux to handle.

Remember, the simplest solution is usually the best:

-Linux-only system? - Use linux-native filesystems (ext2/3, reiser, etc).
-Windows-only system? - Use windows-native filesystems (NTFS)
-Linux+Windows system? - Use a filesystem both can use well (FAT32)

---

### Post by moljac024 on 2007-05-24
Yes, i am now backing up my data, destroying that awful windows partition and reinstalling ubuntu !
Keep your fingers crossed for me :)

I only used ntfs because i had too much data on it (aprox 100 GB) that i needed and i lacked the DVDs to burn it all.....

---

### Post by Soybean on 2007-05-24
Regarding beryl not falling back to metacity... beryl can recover from a "crash," by switching to metacity, but you're experiencing a "freeze." It's driver-related, and it's actually locking up your kernel, so there's no way to recover from it. If it happens a lot (after you get back up and running), you might want to disable some of the effects or drop beryl altogether.

On the other hand, my laptop at home freezes under beryl every couple of days, but I find it's worth it as long as I'm not doing anything important. ;) Especially since Firefox got that session recovery feature.

---

### Post by moljac024 on 2007-05-24
Okay, it seems that the ntfs partition was causing trouble....it's no more !
I feel so good now, without anything MS related on my computer.... :-)

I would gladly disable some beryl features if i knew which ones cause trouble ( i've tried various combinations). And also, is it possible that beryl would be more stable with proprietary ATI drivers ? I've read more than one web site claiming that the open-source ones were more stable, and i don't want more instability....

I've noticed,however, that the 90% of the time when freezing happens it's after i close a window with the burn animation, although it happened at other times too....

---

### Post by shad0w_walker on 2007-05-24
I speak from personal experience on this matter:

Do NOT under any circumstances bother with the official ATI drivers.

I had them, they sucked, it was painful to have to use them for so long. You can try them but i would recommend a full backup of your OS files, because the uninstall doesnt work and tends to leave a few dozen files spread across your drive.

---

### Post by moljac024 on 2007-05-24
Ok, thanks for the heads-up!

Just one question : are the open-source ati drivers good for games ?
I don't plan gaming a lot, just asking...

---

### Post by shad0w_walker on 2007-05-24
In some things they are ok (Tolerable) UT2003/4 seem to be ok, but try not to stress it too much. It tends to vary alot from card to card so you might get lucky with it, might not.

---

