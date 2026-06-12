---
title: "Installing in background"
date: 2017-12-17
forum: Installation &amp; Upgrades
---

### Post by James Wilde on 2017-12-17
On the theory that there are no stupid questions, I'd like to ask this one.
I have a computer which is happily running Ubuntu-Mate, 16.04 and which is my normal working laptop.  I'd like to install Ubuntu-Mate on another disk.  I wonder whether I can connect the relevant disk to my computer and find some way to install Ubuntu-Mate on it in the background, that is whilst I am doing something else on the computer?

Why would I want to do that?  Well, the disk in my working computer is an old 160 GB disk.  The new one is 1 TB.  Eventually I'd like to transfer everything I have on the little disk to the larger one, and then switch them so that I have a 1 TB drive in my computer instead of one hardly more than one tenth of the size.

I realise I could just dd my 160 GB disk over, but I've had so much trouble with copying disks that I thought it might be better to try this method.

---

### Post by yancek on 2017-12-17
>   I wonder whether I can connect the relevant disk to my computer and  find some way to install Ubuntu-Mate on it in the background, that is  whilst I am doing something else on the computer?

I doubt that will work the way you want because you are wanting the installer to do a non-standard install automatically.  These installers aren't mind readers so they don't know what you want and you can easily do that with the manual "Something Else" option.  You can download the Ubuntu iso if you don't already have it and boot the iso directly from Grub on your installed system and then use the installed system while it is installing your second Ubuntu.  You will need to make some decisions/selections during the install.  You should run the command:  sudo parted -l before installing with both disks attached so you know which is which and you don't accidentally overwrite the original.  

Probably simpler if you are not experienced with installers to use a DVD or flash drive to install but you will still need to identify the correct device to install to.  Should be easy enough as your drives are different in size and parted will tell you which is which.

I'm not sure I read you correctly about installing the second system while using the first.  If you just want two installs, you need to identify which drive is which by size so as not to overwrite the original.  I've always used the manual install option so I'm not really sure how it would work if you selected the second disk initially and then used the Erase Disk command to install to that drive.  Lot safer to use the Something Else command.  You might wait for someone more familiar with the Erase Disk and/or Install Alongside options.

Do you have an EFI install?  That might complicate things for you.

---

### Post by James Wilde on 2017-12-17
Thanks for your input, Jancek.  I suppose I have to bite the bullet and try dd one more time.  I have my little disk divided in two partitions, 20 GB for / and the rest for /home, and I would want to format the larger disk in pretty much the same way, perhaps 50 GB for the system and the rest for /home (plus swap, of course).  I happen to have a day with some free time tomorrow, that is time when I cannot work on my computer.  Maybe I can dd the system partition, switch the disks, mount the smaller /home as /home and do a dd of the smaller /home at a later time.

---

