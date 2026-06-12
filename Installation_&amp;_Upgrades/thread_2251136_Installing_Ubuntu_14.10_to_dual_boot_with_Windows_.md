---
title: "Installing Ubuntu 14.10 to dual boot with Windows 7."
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by mjalberts13 on 2014-11-02
Hello

This morning I tried to install Ubuntu on another partition as the one my windows+data is on and after it installed and my PC restarted I got this message "error: symbol 'grub_term_highlight_color' not found". I decided to just do a clean install of windows so what I am wondering is if the USB with Ubuntu 14.10 on it is faulty or was it something I did wrong in the installation?

---

### Post by Mark Phelps on 2014-11-02
You mention installing on "another partition". What filesystem did you use to format that partition? If it was an existing Windows partition -- that's where you did "something wrong".  You can only install to a Windows partition using WUBI -- and that isn't supported anymore.  It was dropped from support due to problems with preformatted Windows 8 PCs.

I would personally hold off installing 14.10 as there are lots of problems being reported with it, especially during the installation.  I would give it at least a month for the developers to fix the major bugs and update the release code.

---

### Post by mjalberts13 on 2014-11-02
Your profile picture is quite intimidating! ;)

I simply used Windows Disk Management to shrink the volume of my main partition so that there was about 50 GB of unallocated space. I then tried installing Ubuntu on that unallocated part. 

I guess the file system is NTFS.

---

### Post by oldfred on 2014-11-02
There was the same error message with upgrades to 14.04 and that was due to grub version differences. Some part of update did not correctly re-install grub to MBR or internally. Post 109 explains.
       Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

So did you have an older version of grub installed somewhere and are booting that from MBR and it then does not boot new version correctly?

And how did you make installer. There is/was a bug on syslinux using Ubuntu's creator but unetbootin should work.

---

### Post by mjalberts13 on 2014-11-02
The partition had a really old version of Linux Mint on it. Cinnamon 14.1 I believe it was.

I made the installer with pendrivelinux.

---

### Post by oldfred on 2014-11-02
It sounds like then it may be using the old Mint grub to boot Ubuntu now and versions are different.

Does live installer boot ok? If so run this:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mjalberts13 on 2014-11-02
I installed Windows and formatted all the partitions. 

I just want to know how I can prevent the grub error with future Ubuntu installations?

If I pick "Something else" and select the partition I want to install Ubuntu on what do I need to type into the "Mount point:" field?

---

### Post by oldfred on 2014-11-02
The mount point is the / (root) partition and then /home if you have that.
But you install grub to the drive that you are installing Ubuntu into.

The combo box to chose install location is below the partitioning part of the screen. Choose drive not partitions.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

