---
title: "Update U11.4 on USB"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by rgd130 on 2011-08-16
Installed U11.4 on an 8Gb Sandisk USB formatted FAT32 using "Universal USB Installer" with 4GB persistance.  Using "Try Ubuntu" I ran "Update Manager".  Some updates failed.  Upon restart, USB option was absent from boot menu.  Erased and reinstalled U11.4 on USB and everything works fine without update.  Should I be able to update a USB ?  Curious

---

### Post by rgd130 on 2011-08-26
> **rgd130 said:**
> Installed U11.4 on an 8Gb Sandisk USB formatted FAT32 using "Universal USB Installer" with 4GB persistance.  Using "Try Ubuntu" I ran "Update Manager".  Some updates failed.  Upon restart, USB option was absent from boot menu.  Erased and reinstalled U11.4 on USB and everything works fine without update.  Should I be able to update a USB ?  Curious

Success.  I am including my notes to myself FYI.  ( I am sure there must be a cleaner way to do this but this was my solution)

Notes:
 Objective:  Make a bootable Ubuntu 11.4 USB stick that could be updated.
   
  Approach:  1) Use an 8GB USB stick,  2) Download a Ubuntu 11.4 ISO,  3) Install onto USB,  4) Install the latest updates.
   
  Attempt 1:  Went to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and downloaed a 32 bit version of 11.4 to my Windows PC.  (Did not install Linix on the Windows machine.)  Used Unetbootin to create the bootable USB from the downloaded ISO.  Couldn’t figure out how to create a persistence file with Unetbootin so I didn’t think I would be able to update with the latest revs.
   
  Attempt 2:  Used Universal USB installer from Pendrivelinx.com to create the bootable USB from the downloaded ISO, setting the persistence file size to maximum.  Booted up the PC from the USB and used the <Try-Ubuntu> button.  Used the Updater application to get the latest U11.4 updates.  Too many errors reported to list.  Don’t think any updates were made.  The USB didn’t boot following the update attempt.
   
  Attempt 3:  Created a bootable CD using U11.4 ISO following the instructions on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) after clicking the <CD> radio button and the <Show-Me-How> button.  Booted the PC with the CD.  Inserted a FAT32 formatted 8GB USB.  Selected <Install-Ubuntu> button.  Followed CS Cameron’s recipe found at the Ubuntu Forum.  (Search for “**[B]full ubuntu installation on usb hdd” item 7.)  After selecting the **[/B]**[B]USB**[/B]**[B] stick and proceeding, I got an error which I failed to document.**[/B]
  **[B] **[/B]
  **[B]Attempt 4:  Went to [https://wiki.ubuntu.com/Unity/InstallUSBKey](https://wiki.ubuntu.com/Unity/InstallUSBKey).  Booted PC with CD from attempt 3.  Selected <Try-Ubuntu> button.  **[/B]Inserted a FAT32 formatted 8GB USB. **[B] Launched Make-Startup-Disk application.  Selected **[/B]**[B]USB**[/B]**[B] as Disk-to-use.  Clicked <Erase Disk> button.  Selected <Stored in reserved extra space> radio button and moved slider to far right.  Clicked <Make-Startup-Disk> button.  Rebooted from the **[/B]**[B]USB**[/B]**[B] stick.  Launched the Terminal application.  Typed “sudo apt-get update” at the prompt.  At the next prompt typed “sudo apt-get upgrade”.  All but 7 upgrades were installed.  (?)  (Also installed ClamTK, launched the terminal, and typed “sudo freshclam” to get the latest virus defs.)  I think I now have a bootble, updateable, Linix stick with antivirus application.  Call it SUCCESS !**[/B]

---

### Post by rgd130 on 2012-02-16
Note: References to U11.4 above should be U11.04.

 **[B]Attempt 5:  Decided to upgrade my **[/B]**[B]USB**[/B]**[B] stick to 11.1.  Booted from the 8GB stick.  Launched the terminal and typed “sudo apt-get update” at the prompt.  At the next prompt typed “sudo apt-get upgrade”.  Error message indicated there wasn’t enough room on the stick.  Guessed that making a 4GB persistence area on an 8GB stick didn’t leave room for the upgrades.**[/B]
  **[B] **[/B]
  **[B]Decided to use 11.1 to try to create an updateable 11.1 stick.  **[/B]Went to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and downloaed a 32 bit version of 11.1 to my Windows PC.  Created a bootable CD following the instructions on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) after clicking the <CD> radio button and the <Show-Me-How> button.  Used Infra Recorder method to create the bootable CD from the ISO.  Booted the PC with the CD.  **[B]Selected <Try-Ubuntu> button.  **[/B]Inserted a FAT32 formatted 8GB USB. **[B] Launched Startup-Disk-Creator application.  Selected **[/B]**[B]USB**[/B]**[B] as Disk-to-use.  Clicked <Erase Disk> button.  Selected <Stored in reserved extra space> radio button and moved slider to get a 3GB persistence file.  Clicked <Make-Startup-Disk> button.  Rebooted from the **[/B]**[B]USB**[/B]**[B] stick.  Launched the Terminal application.  Typed “sudo apt-get update” at the prompt.  At the next prompt typed “sudo apt-get upgrade”.  All upgrades were installed.  Installed ClamTK, launched the terminal, and typed “sudo freshclam” to get the latest virus defs.  I now have a bootble, updateable, U11.1 Linix 8GB stick with antivirus application.**[/B]

---

