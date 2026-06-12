---
title: "Problem installing Ubuntu 12.04 on Win XP Pro that had 13.04 previously installed"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by Burto Kidd on 2013-05-13
Asks for restart, but when it gets to the dual boot page, seems to loose what it was trying to install, and stops the installation process..
 
 How does one remove the Dual Boot Screen?  


Entire problem began when I updated from 12 to 13, and the install could not locate the Radon 7500 video driver.   Would rather run the 13, but the 12 actually functioned when installed on this machine.  

Must use the Wubi dual boot software as this machine has no USB boot or DVD player.  Have to install using the Internet version.

Dell Latitude c640, 2 gigs DRAM, ATI Radeon 7500 Video driver,

---

### Post by bcbc on 2013-05-14
Uninstall Wubi from the control panel - look for and double click the "Ubuntu" entry.

Use nomodeset to boot: [http://askubuntu.com/a/257917/14916](http://askubuntu.com/a/257917/14916)

---

### Post by Burto Kidd on 2013-05-14
Removed all Ubuntu, Wubi files using Control Panel.   Dual Boot still exists when Ubuntu installer asks to restart the system.  Then the install stops.

---

### Post by Burto Kidd on 2013-05-14
First time I installed Ubuntu, it installed with zero problems, and operated flawlessly.   Marketing encouraged me to upgrade to the 13,04.  Arrrrrgggg!

---

### Post by bcbc on 2013-05-14
> **Burto Kidd said:**
> First time I installed Ubuntu, it installed with zero problems, and operated flawlessly.   Marketing encouraged me to upgrade to the 13,04.  Arrrrrgggg! That's always a trap. I'd advise sticking with the LTS unless you have a compelling reason to upgrade or don't mind some breakage.

> **Burto Kidd said:**
> Removed all Ubuntu, Wubi files using Control Panel.   Dual Boot still exists when Ubuntu installer asks to restart the system.  Then the install stops.
I don't understand. You uninstalled but there is still an option to boot into Ubuntu  when you start? It may just be a leftover in the windows boot manager and this can be removed: [http://askubuntu.com/q/145444/14916](http://askubuntu.com/q/145444/14916)

---

### Post by Burto Kidd on 2013-05-14
Removed the Ubuntu File using Control Panel.  Removed the Wubi files.   Restarted and Windows opened with no Dual Boot option screen.   Re-installed Wubi, and attempted to install Ubuntu again, and got to the Reboot Screen.  Rebooted and the Dual OS Screen opened.   Choose Ubuntu and complains there is something missing.  Booted in Windows and nothing continues on the install.   Repeated the removal of all Ubuntu files and Wubi again.  Checked the Hard Drive for a Partition, only one.   Repeated the Installation process again, and it still fails on the Reboot process?   I have a logon set for XP Pro for Administrator, which is the same password as for Ubuntu.

Will continue attempting to install,  wish this machine would allow boot from USB, or had a DVD reader installed.  BIOS does not allow boot from USB.   

Confused why i was able to install the original Ubuntu prior to this, it installed with no problem.

---

### Post by bcbc on 2013-05-14
So... you chose Ubuntu.

It complained something is missing: wubildr? That's not a problem. Unless it complained about wubildr.mbr being missing or corrupt. That is a problem.

What happened after that? It should have tried to boot up Ubuntu. Did you see a bunch of weird lines on the screen, a black screen, a purple screen. That's where you would have needed nomodeset.

The 13.04 wubi is different to the 12.04 wubi because the 12.04 uses a 'diskimage' and the 13.04 uses an ISO. Whether that is causing the difference isn't clear.

---

### Post by Burto Kidd on 2013-05-14
Complained prefix was not set.  Now it reboots directly into Windows again, with no option for dual boot.   Will attempt to follow the process once again to install Ubuntu.

---

### Post by bcbc on 2013-05-14
What is pace?

---

### Post by Burto Kidd on 2013-05-14
Using Google Chrome browser to install, I will try Mozilla Firefox.

---

### Post by bcbc on 2013-05-14
Why would that make a difference?

---

### Post by Burto Kidd on 2013-05-14
It read Prefix is not Set, not Pace.

---

### Post by Burto Kidd on 2013-05-14
Found one problem, the download of ubuntu-12.04.2-desktop-1386iso had a download error.  Re-downloading for the 6th time.

---

### Post by Burto Kidd on 2013-05-14
About to learn all of this, thanks for your help.

---

### Post by Burto Kidd on 2013-05-14
Here is the error messege when choosing Ubuntu start up.  Try (hd0 ,0) : NTFS5: error: "prefix is not set"

---

### Post by Burto Kidd on 2013-05-14
Pressed esc and it is now  opening Ubuntu.   You are a genuis!   Thanks so much!!!

---

### Post by bcbc on 2013-05-14
> **Burto Kidd said:**
> Here is the error messege when choosing Ubuntu start up.  Try (hd0 ,0) : NTFS5: error: "prefix is not set"Wubi always has some output about "Try (hd0,0)". It's diagnostic output from grub4dos and can be ignored (unless it hangs on that or says grldr not found).
The one about "prefix not set" is always present on Wubi installs from release 11.04 up to 12.04, but fixed in 12.10 or 13.04 (one of the two). It can also be ignored.

> **Burto Kidd said:**
> Pressed esc and it is now  opening Ubuntu.   You are a genuis!   Thanks so much!!!
Great.

Remember with Wubi, it's designed to try out Ubuntu. If you like it, consider a real dual boot. If you want to keep Wubi, either keep important personal data stored on the Windows /host (outside of the Wubi virtual disk), on a separate partition, or sync'd to the cloud.

---

### Post by Burto Kidd on 2013-05-14
I use Google Drive because I travel a l lot.  Own a Chromebook and like keeping files on a cloud storage at this point as I travel. It syncs with my two handsets, Chromebook, Desktops, and five Laptops.

---

### Post by Burto Kidd on 2013-05-14
How can I do a full install, avoiding Wubi, without a DVD player, or USB Boot in BIOS?

---

### Post by bcbc on 2013-05-14
On XP it's tough because I don't believe you can partition it from within Windows (while the drive is mounted) and you can't do it from Ubuntu either. But on Windows 7 you can shrink the main C: partition even while running Windows, and then [migrate the Wubi install]("https://help.ubuntu.com/community/MigrateWubi") to new partitions you create in that free space.

The only other way I could think of would be to pull out the hard drive and do it from another computer.

Personally, I wouldn't advise dual booting if you can't boot a rescue disk though. Stuff happens and then a simple thing (e.g. reinstalling Grub or running chkdsk for a Windows repair) is no longer possible.

---

### Post by Burto Kidd on 2013-05-14
Ooops spoke too soon.  Gets about 3/4 of the way copying files, then the mouse locks up and wheel stops spinning.

---

### Post by Burto Kidd on 2013-05-14
It will reboot and start up again in Ubuntu and attempt another Install but hangs at the same place. ??

---

### Post by Burto Kidd on 2013-05-14
Working again.   Directions need to inform installers these screens may take up to 4 minutes to refresh.

---

### Post by Burto Kidd on 2013-05-14
Makes me appreciate my out of the box operating Google Chromebook more each day.  :)

---

### Post by Burto Kidd on 2013-05-14
As I recall it took around 6 hours to install the first time.  I have a fast Cable Internet connection, can't imagine what a slow DSL would be like.

---

### Post by bcbc on 2013-05-14
If it locks up, press CTRL+ALT+F1, and take the logs:

```
sudo zip -r /host/ubuntu/install-logs.zip /var/log
```

Then go back to the graphics to check if it continues CTRL+ALT+F7
If it doesn't, drop back to CTRL+ALT+F1 and sudo reboot.

Then you can attach the logs from C:\ubuntu\install-logs.zip after rebooting in Windows.

---

