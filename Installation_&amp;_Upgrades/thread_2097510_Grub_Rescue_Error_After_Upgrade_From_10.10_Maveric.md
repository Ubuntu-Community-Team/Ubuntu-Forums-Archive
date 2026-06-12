---
title: "Grub Rescue Error After Upgrade From 10.10 Maverick To 12.04.1.."
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2012-12-23
Hello Ubuntu Collective,

     After completing an update of 10.10 Maverick on a Dell Latitude E6510 laptop that has Windows 7 Professional and on a partition and Ubuntu 10.10 on another partition to 12.04.1 the computer rebooted after I updated from DVD and now I am receiving an error:

error: invalid arch independent ELF magic.
grub rescue>

     The installation was pretty straightforward, I booted from Disc and after choosing to install Ubuntu 12.04.1, I chose to upgrade after receiving the prompt that Windows 7 Professional and Ubuntu 10.10 had been detected so I chose to upgrade.  However, now I am no longer able to see Grub at start up, which I know was updated during the upgrade.  Any help would be more than appreciated.  I'm pretty sure this has to do with updating Grub.

     Thank you so much in advance and Happy Holidays!!

---

### Post by dino99 on 2012-12-23
i does not really understand what have been done , as maverick is not a LTS, so should not be able to dist-upgrade to 12.04.1

by the way maverick use grub1 (grub-legacy with its menu.lst) but recent release use grub2 (grub-pc) and dont like grub1+dependencies.

you still can try chrooted but i think you will go faster to do a fresh install and get less trouble due to oldisd settings left behind.

---

### Post by freesparks on 2012-12-23
Thank you so much for the reply Dino99, all i did was upgrade my system which had Windows 7 professional on one partition and Ubuntu 10.10 maverick 2.6.35-32 generic pae on another partition.  Before doing the upgrade I was able to see grub list my linux partition first and then my Windows 7 professional partition last.

  I am no longer able to see that after the system rebooting after the upgrade to 12.04.1 completed.  Is there a way to restore or fix the Grub so that it sees both my Windows 7 partition and the new 12.04.1 ubuntu partition.

Best Regards,

freesparks

---

### Post by freesparks on 2012-12-23
Hello  Ubuntu Collective,

     Please help, I now booted from a DVD that is ubuntu 12.04.1 LTS I386 the other one that I booted from originally was Ubuntu 12.04.1 AMD64, but now I am being given a prompt that this computer currently has Windows 7 and ubuntu 12.04 LTS on it.  What would you like to do?  The options that it gives is to:

Erase Ubuntu 12.04.1 LTS and reinstall, however this will delete all my Ubuntu 12.04.1 LTS files, photo, etc. , which I dont want to do because this is the upgrade that I did from ubuntu maverick 10.10 that i mentioned in the previous post.

Also, among the options are Erase everything and reinstall:

    I dont want to do this because it says it will delete everything and on the Windows 7 Professional partition as well.

The third option is Something Else:

     This is what I am sort of familiar with in respects to creating my own boot partitions, grub etc. whenever I would dual boot the machine in the past.

     Any help on this would be greatly appreciated.  Luckily, the install is still detecting the Windows partition.  I just want to fix the original error I was receiving after I upgraded with Ubuntu 12.04.1 LTS AMD 64 which gave me the error:

error: invalid arch independent ELF magic.
grub rescue>

         after the system rebooted after upgrading from Maverick 10.10 to ubuntu 12.04.1.

Thanks again everyone!!

---

### Post by grahammechanical on 2012-12-23
First, make backups of everything that you do not want to loose. For you are going to loose what is on the Ubuntu partition. I see no other way.

Does your machine have a 32bit CPU? Ubuntu 32bit will work on both 32bit CPUs and 64bit CPUs but UBuntu 64bit will not work on a 32bit CPU.

This 

> error: invalid arch independent ELF magic.

could mean that you have an operating system that does not run on the architecture of your machine. So, you may have no choice but to choose the Do Something Else option and over-write the Ubuntu 12.04 already in the partition.

Regards.

---

### Post by freesparks on 2012-12-23
Thank you for the reply grahammechanical,

     Yes you're right and this was my hunch, and this is why I put the 32 bit disc instead.  But, surely there's gotta be a way to install 32 bit 12.04.1 Ubuntu losing all those files.  I have chosen to delete the newly non-functioning 64bit 12.04.1 LTS and am installing the 32 bit version 12.04.1 LTS version instead and hoping this will fix the grub.  However, if this does work, and it should, how do i go about reinstating the grub so that it sees both my Windows 7 professional and the newly created 32 bit 12.04.1 ubuntu partition?

     Thanks again for the help and suggestion.

---

### Post by freesparks on 2012-12-23
In addition, I'm confident, and I maybe wrong that this is a result of a broken Grub/boot.  If it is, what command do I use to list my current partition scheme?  I'm pretty sure it's:

sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt /dev/sda

     However, in my case I want to be sure I am mounting the correct partition that contains my Grub, which is why I need to know what command and how to go about retrieving my current partition scheme.

Thanks in advance!!

---

