---
title: "Ubuntu, Win 7 Dual Boot problem"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by brhokla on 2009-12-02
I'm using Ubuntu right now to write this and my win 7 is working fine also. Only problem is that when I boot up I have Ubuntu on my F drive and Win 7 on my C drive.  Apparently my computer is not automatically going to F when i tell it on the dual boot screen to use Ubuntu.  I have to get into Bios and select it to manually start F: every time.  Is there a way to get this to let me select Win 7 or Ubuntu and the computer automatically go to the correct drive that it is installed on?

Thanks

---

### Post by Megafag on 2009-12-02
> **brhokla said:**
> I'm using Ubuntu right now to write this and my win 7 is working fine also. Only problem is that when I boot up I have Ubuntu on my F drive and Win 7 on my C drive.  Apparently my computer is not automatically going to F when i tell it on the dual boot screen to use Ubuntu.  I have to get into Bios and select it to manually start F: every time.  Is there a way to get this to let me select Win 7 or Ubuntu and the computer automatically go to the correct drive that it is installed on?

Thanks

how did you install all this?
do you have a GRUB screen?

---

### Post by darkod on 2009-12-02
OK, first of all, assigning letters C, D, E etc is what windows does, not linux. And windows can't see the ubuntu partitions to assign them letters, not without special procedure.
Unless you have actually wubi which is different than standard ubuntu.
What is your F drive? What do you mean by that? Is Ubuntu on one hard drive and windows on another separate hard drive?

---

### Post by brhokla on 2009-12-02
> **darkod said:**
> OK, first of all, assigning letters C, D, E etc is what windows does, not linux. And windows can't see the ubuntu partitions to assign them letters, not without special procedure.
Unless you have actually wubi which is different than standard ubuntu.
What is your F drive? What do you mean by that? Is Ubuntu on one hard drive and windows on another separate hard drive?


Yes,  Two different drives.

---

### Post by darkod on 2009-12-02
Well this situation can happen if you had your windows drive disconnected when installing ubuntu. It could not see the windows installation to add it.
Set BIOS to boot from ubuntu drive. That will allow you to boot ubuntu. Then open terminal and do:
sudo update-grub

Reboot and see if windows is in the grub menu and whether it's booting fine.

---

### Post by presence1960 on 2009-12-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rideonXX on 2009-12-02
Please help----I have just loaded Ubuntu 9.10 as the second operating system on this computer.  The other system is Win7 RC.   The grub loader shows Win7 as an option but keeps looping back up to the Ubuntu option.  Thus, I have not been able to get to the Win7 loader.  Both programs are loaded on the same drive in different partitions.

What should I have used for the where to mount choice when Ubuntu partitioner asked that question.  I used '/'.

Any assistance will be greatly appreciated.

Thank you, kel

By the way, the drive position for win7 is the primary partition on sda1---so vol 1?  The Ubuntu location is sda1/vol8---------thanks

---

### Post by oldfred on 2009-12-03
rideonXX, please start a new thread with your problem and try to explain it as much as possible including Presence's recommendation on the script. It is too difficult to keep track of which person we are responding to when different posters as asking different questions. (Even though they may be similar issues).

---

### Post by rideonXX on 2009-12-03
> **oldfred said:**
> rideonXX, please start a new thread with your problem and try to explain it as much as possible including Presence's recommendation on the script. It is too difficult to keep track of which person we are responding to when different posters as asking different questions. (Even though they may be similar issues).


Will do, thanks

---

