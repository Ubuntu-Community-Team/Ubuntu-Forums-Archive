---
title: "Boot issues"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by taeza on 2019-04-19
Hi,

I was trying to install docker on my ubuntu 16 machine. It finished installing and I was able run a sample container however I noticed some issues with my ui (e.g.  missing  icons on my firefox brower) I then rebooted and I couldn't get in anymore. I only see the emergency mode come up.

Boot-repair didn't fix my issue.
Here's my pastebin:
[https://paste.ubuntu.com/p/WDCgsvYqXM/](https://paste.ubuntu.com/p/WDCgsvYqXM/)

Thanks in advance.

---

### Post by oldfred on 2019-04-19
You show old XP boot files in your NTFS partition? XP does not work at all with UEFI systems.

You show a lot of unknown entries in UEFI NVRAM entries. That is Acer & setting "trust". But since you have an entry with "ubuntu", I assume you know about trust & Acer systems. You can delete all the duplicate entries in UEFI. You can also delete most of the grub menu items in 25_custom that was created by Boot-Repair. It sees additional .efi boot files, & adds entry just in case you want or need those. 

But I do not think either of those are your issue. What video card chip?
Do you get to grub menu?

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) 

      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

      
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also. also can turn off execute on 25_custom if none wanted
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by taeza on 2019-04-19
Thanks for the quick response. I have windows 10 on my other partition. Thats still working well. I get to the grub but get emercency mode w the ff when I choose ubuntu: 

Failed to start lsb: apparmor initialization

---

### Post by oldfred on 2019-04-19
Can you boot to recovery mode, second or third menu item in grub?
But not sure exactly what repairs you may need.

---

### Post by taeza on 2019-04-19
Recovy mode comes up but I can't make the arrows point to any of the items. When I type something it comes up on the background. 
I think I'll just hve to reinstall the os. This time I'll try 18.

---

