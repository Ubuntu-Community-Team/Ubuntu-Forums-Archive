---
title: "grub rescue on a dual boot system"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by seth elohim on 2010-03-24
So here is my problem. A good friend of mine wanted me to install Ubuntu on their computer to surf the web without fear of viruses/malware/ect. they had windows7 installed to run certain apps they couldnt live without. I used a 9.10 cd that I have used several times for various installs and everything seemed to go well. However when I went to reboot I got a grub rescue prompt and nothing else. I searched the forum and found "How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)" I then followed the instructions to the letter but when I rebooted it went back to grub rescue. I can use the terminal and paste any output here if you gurus can walk me through the rescue. As a side note, her copy of windows seven has a loader of its own, and I am not sure if that has anything to do with it, but I really hope that i dont wind up screwing her computer up and souring her on Linux after all the great stuff I have told her about it.

---

### Post by 666f6f on 2010-03-24
Probably for some reason a messed up /boot/grub/grub.cfg was generated. It happened to me many times when I had Ubuntu installed on a USB External Disk (which, by the way, is not a good idea because of crappy USB controllers or faulty USB cables, at least to my mind).

Can you boot the Karmic LiveCD, run *sudo fdisk -l* and then paste the output here?

---

### Post by seth elohim on 2010-03-24
Sorry, I already went atomic and reloaded windows7 from boot disc. I think her problem involved it being a patched copy of windows with a hacked loader. (not my work btw) I will tackle the problem with grub after I get her a legit copy of windows. Thank you for taking the time to respond none the less :) For the record, anyone using a hacked loader will probably run into similar problems with grub.

---

### Post by 666f6f on 2010-03-24
Quite gentle response, thanks for reporting back!

---

### Post by Jeff May on 2010-03-24
Very glad you solved the issue.  I do want to provide an "enhanced" response for the sake of those who may find this thread via a search.  Currently upgrading a Karmic 9.10 dual-boot system to Lucid 10.04 beta seems to be problematic in some instances, and causes Grub2 to be written to the Windows partition.  As a result trying to select your Windows partition from the Grub2 menu just brings you back to the Grub2 menu.

Here's the fix . . . and it pretty much applies to a number of similar situations when after installing Ubuntu you can no longer access your Windows 7 (or Vista) partition because the Windows bootloader was overwritten . . .  

1.  Restore the Windows 7 bootloader.

   - Boot the machine from the Windows 7 CD
   - Select "Repair Windows"
   - After the installer finishes searching for Windows systems, select the installation you wish to restore.
   - Select the "Boot to command prompt" option.
   - At the command prompt, issue the following commands

[B]bootrec  /fixmbr
bootrec  /fixboot[/B]

   - After issuing each command you should receive "The command was completed successfully" 

When you restart your computer you should boot directly into your Windows 7 installation.

  2.  Restore the Grub loader and Dual-Boot Functionality
    - Boot the machine from Ubuntu Live CD
    - Open a terminal session
    - Create a mount point for your Ubuntu partition
     (example:  if your Ubuntu installation is in sda5 . . . )

**         sudo  mkdir  /media/sda5**
         
     - Mount your Ubuntu partition to the mount point

      **    sudo mount /dev/sda5   /media/sda5**

     - Finally, install Grub on your Ubuntu partition and point the boot loader to it.

          **sudo   grub-install   --root-directory=/media/sda5  /dev/sda**

      
Reboot the machine, and you should be good to go.

---

