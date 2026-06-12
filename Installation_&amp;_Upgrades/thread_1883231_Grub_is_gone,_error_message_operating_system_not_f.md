---
title: "Grub is gone, error message: operating system not found"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by nosirrah111 on 2011-11-18
Okay guys here is where I sit. I have an alienware m11x laptop that I recently installed Ubuntu 11.04 onto, but after a week or so of use it seems that GRUB has disappeared. I get an error message on start up (before any os loads) saying "no module name found. Aborted. Press any key to exit. Operating System not found". I had a dual boot of 7 and ubuntu. Ive tried installing super grub 2 and also running from a live CD but neither work. (mind you i have to use an external optical drive if this makes any difference). I cant seem to get any bootloaders to work at all. Anyone have a clue as to whats causing this? Could it be a hardware problem?

---

### Post by darkod on 2011-11-18
I wouldn't use super grub or any other tool apart from the ubuntu cd. At least not until it's confirmed there is no way to repair with ubuntu.

Boot again in live mode with the cd and follow the link in my signature to run the boot info script. Post the results as explained there. That should show more details about the system.

---

### Post by dolphin194 on 2011-11-18
> **nosirrah111 said:**
> Okay guys here is where I sit. I have an alienware m11x laptop that I recently installed Ubuntu 11.04 onto, but after a week or so of use it seems that GRUB has disappeared. I get an error message on start up (before any os loads) saying "no module name found. Aborted. Press any key to exit. Operating System not found". I had a dual boot of 7 and ubuntu. Ive tried installing super grub 2 and also running from a live CD but neither work. (mind you i have to use an external optical drive if this makes any difference). I cant seem to get any bootloaders to work at all. Anyone have a clue as to whats causing this? Could it be a hardware problem?

I have found a guide on recovering the GRUB bootloader at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). Even though it may say "After Windows," it's an easy way to recover your GRUB bootloader.

> **Using the Ubuntu CD (Recommended)**

 
[LIST]
[*]Insert your Ubuntu CD, reboot your computer and boot into a live session.
[*]Install and run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), select 'First Repair' and apply.
[*]Reboot without the CD. GRUB menu will appear and will propose both Ubuntu and Windows.
[/LIST]
**[SIZE=3]*Here's* how it goes![/SIZE]**
Simply run these commands to install it
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```After installing Boot Repair, launch it and click the "Recommended repair" button.
[IMG]https://sites.google.com/site/finnyphinelia/finny-files/bootrepair.png[/IMG]
-Dolphin

---

### Post by nosirrah111 on 2011-12-03
Thanks a lot guys! I finally found time to get around to this. Boot-repair worked and everything is running smooth.

---

### Post by Bucky Ball on 2011-12-03
Good work. Boot-repair is a gem and solves a lot of these issues. Please mark thread as solved so you might help others. :)

---

### Post by dotsdan on 2013-03-24
Is it likely in the future Boot-Repair will be bundled with Ubuntu live cd/usb in the future? Thanks, Boot-Repair has fixed alot of grub problems for me.

---

### Post by Bucky Ball on 2013-03-25
Welcome to the forums.

That is doubtful. You can install Boot Repair when trying Ubuntu from a Live CD so this isn't really necessary.

***Thread Closed***

***Reason***: Necromancy. 

Please do not resurrect threads that have had no activity for over a year. Better to post a new thread.

---

