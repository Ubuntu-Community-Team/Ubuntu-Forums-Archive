---
title: "Cannot install alongside Windows 7"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by underage17 on 2011-03-19
I just downloaded the Netbook edition of Ubuntu 10.10, and created a bootable USB disk as per the instructions on the website.
I open the OS through my USB, click the "Install Ubuntu" button, click forward, and then comes my problem.
I don't have an option to "Install alongside other OS"

I'm running Windows 7 Home Premium on an HP Mini 210..

---

### Post by underage17 on 2011-03-19
instead of booting it up through the USB first, I just tried to run the wubi.exe file on the USB.
It has an option allowing me to install inside Windows.
Can that be done??
I mean, on another post, some guy said that you need to repartition windows or something to get some space free for ubuntu.. is that necessary?

---

### Post by mikewhatever on 2011-03-19
You may have three or more primary partitions, in which case, the automated alongside installation wouldn't work, and therefore isn't offered. You can check the existing partitions by looking at the output of **sudo fdisk -l**, or if you prefer GUI, the Disk Utility under System->Administration.
Edit: Installing inside Windows doesn't require partitioning.

---

### Post by underage17 on 2011-03-19
Hmm.. right now, my win7 is up and running, and I've got a C drive, a D drive (recovery) and an E drive (HP tools)..
so.. im guessing thats 3 partitions
does that mean I can't install ubuntu?

edit - I've installed ubuntu before (version 8.02 i think) but i did it alongside Win XP.
i didn't have to repartition anything and it didn't give any issues.
Is this problem occurring because of Windows 7?
I mean, in my XP, I had 3 partitions as well..

---

### Post by mikewhatever on 2011-03-19
With three primary partitions in place, you'll have to resort to the manual partitioning option. It has nothing to do with W7 or XP, but do verify the total number of partitions. W7 often has a boot partition which isn't shown in the file browser. Open the disk manager to see what partitions are there.

---

### Post by underage17 on 2011-03-19
didn't u say it doesn't require a partition?
well.. let me go check this sudo fdisk anyway now....

---

### Post by mikewhatever on 2011-03-19
> **underage17 said:**
> didn't u say it doesn't require a partition?
well.. let me go check this sudo fdisk anyway now....

Yes, I did. ;) Installing '**inside Windows**' doesn't require partitioning, as Ubuntu gets installed into a file in the Windows file system. Installing **alongside Windows**, on the other hand, means installing to a dedicated partition, completely independent from Windows.

---

### Post by underage17 on 2011-03-19
ooohhhhh!!! i had installed "inside" windows last time too..
i'll go ahead and do that then
by the way, if i install it inside windows, and later want to remove it, can i do it without harming my windows?

---

### Post by mikewhatever on 2011-03-19
Yeap. According to the Wubi FAQ:
> How do I uninstall it?

You uninstall it as any other applications. In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it. You can also use the uninstaller that you find in the installation folder.

[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

---

### Post by underage17 on 2011-03-19
thanks a lot :)

---

