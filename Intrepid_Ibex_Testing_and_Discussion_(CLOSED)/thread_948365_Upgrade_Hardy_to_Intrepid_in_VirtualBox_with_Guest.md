---
title: "Upgrade Hardy to Intrepid in VirtualBox with Guest Additions installed"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by s1mon on 2008-10-15
Posting this to help others as I've just had trouble.

If you find that gnome doesn't work after upgrading Hardy Heron to Intrepid Ibex as a guest OS in virtualbox, Guest Additions may be the culprit.

Pre-requisites:
Hardy Heron as a guest OS in VirtualBox. 
Linux Guest Additions installed in Hardy.  
(In my case the host OS was XP, but I doubt that has any relevance)

Problem:
After the upgrade to intrepid, Ubuntu boots but either goes straight to console, or shows a graphic error GUI, saying that the gnome config is wrong or missing.  
There may be a mention of a vbox video driver.
Any attempts to repair the config won't work.

Solution:
In the VirtualBox menu, click devices, then Install Guest Additions.
Change to a console in Ubuntu (Ctrl-Alt-F1)
Unmount then mount the cd to make sure it is available.
```
sudo umount /media/cdrom0
sudo mount /media/cdrom0
```
Change directory to the cdrom then reinstall Guest Additions
```
cd /media/cdrom0
sudo ./VBoxLinuxAdditions-x86.run
```

Use the amd version if applicable to your version.  

After installation, reboot and the graphics should work again.

---

