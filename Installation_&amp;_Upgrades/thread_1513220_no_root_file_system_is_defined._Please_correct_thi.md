---
title: "no root file system is defined. Please correct this list from the partition menu"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by eeg710 on 2010-06-19
Hi.

I'm generally new to ubuntu so please forgive me if this is an error that has already been solved, but I am running Windows 7, and when I finish installing Wubi in Windows, it asks me to reboot.  I select Ubuntu and it gives me the error: "No root file system is defined. Please correct this list from the partition menu."  I can't get past this error.  Any help would be greatly appreciated.

Thanks!

---

### Post by Chame_Wizard on 2010-06-19
You have to choose */* as the partition.

---

### Post by eeg710 on 2010-06-20
I can't boot into Ubuntu past this error (which I get on boot) and there's no option to choose the partition in Windows.  Where do I set this?

---

### Post by darkod on 2010-06-20
I saw this in another thread and it might be the same. In that case the person was also getting this error in wubi. But he also tried a full install on its own partition and realized the hdd si not shown in the installer.

That usually happens if the hdd has been used in raid and has metadata on it.

If you ARE using raid, I'm not sure how to install wubi inside windows.

If you are NOT using raid, make an ubuntu cd (if you already don't have it), boot it in live mode and in terminal execute:

sudo dmraid -r -E /dev/sda (or if your disk has different name, use that instead of /dev/sda)

If that asks you to remove raid metadata, do it.

After that try booting wubi. I'm not sure if reinstalling it will be needed.

Have in mind that wubi is not a full install and it's not recommended for longer use.

---

### Post by pearce007 on 2011-05-05
I have just had the same problem with Ubuntu 11, I tried installing by using Wubi straight from Windows 7 and it says "No root file system is defined", so I uninstalled it and tried installing dual boot from CD and it keeps crashing on the first hurdle of installation, any help on installing would be great! :confused:

---

### Post by bcbc on 2011-05-05
You should generally create a new thread - this one is nearly 1 year old. Why don't you review this thread [http://ubuntuforums.org/showthread.php?t=1743189](http://ubuntuforums.org/showthread.php?t=1743189) and then create your own thread, and post your bootinfoscript results.

---

