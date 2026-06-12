---
title: "Karmic Install boots straight to Vista"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2010-01-24
Hey everyone,
I currently have Windows Vista Home Premium installed on my c drive, (ide).
I installed  Ubuntu 9.10 32 bit,onto a new drive 500gb (sata).  I chose the "erase and use entire drive" option at install. Install goes great but,no matter what I do, every reboot goes straight to windows. No grub menu at all. I have changed the boot order of the drives in my bios a few times. Nothing helps.  I HAVE successfully had Ubuntu installed on this machine before, however, I had to reinstall because I got a grub error after an update and could not figure the problem out. But every install has failed since. I have tried 32 bit and 64 bit, as my machine is 64 bit. It is so frustrating. Any help is greatly appreciated. Thanks in advance,
P.S. 
I have reformatted the 500 gig drive back to ntfs, and will wait for a definative answer before installing Ubuntu again.
Smitty

---

### Post by Sef on 2010-01-24
I would have instead of installing or running the live cd, gone to the bottom of the list to fix disk for erros (or something similar.)    Then i would have reinstalled grub.

---

### Post by bigsmitty64 on 2010-01-24
> **Sef said:**
> I would have instead of installing or running the live cd, gone to the bottom of the list to fix disk for erros (or something similar.)    Then i would have reinstalled grub.

Thanks, but since I didn't do that, can you tell me how to proceed from here?

---

### Post by presence1960 on 2010-01-25
> **bigsmitty64 said:**
> Hey everyone,
I currently have Windows Vista Home Premium installed on my c drive, (ide).
I installed  Ubuntu 9.10 32 bit,onto a new drive 500gb (sata).  I chose the "erase and use entire drive" option at install. Install goes great but,no matter what I do, every reboot goes straight to windows. No grub menu at all. I have changed the boot order of the drives in my bios a few times. Nothing helps.  I HAVE successfully had Ubuntu installed on this machine before, however, I had to reinstall because I got a grub error after an update and could not figure the problem out. But every install has failed since. I have tried 32 bit and 64 bit, as my machine is 64 bit. It is so frustrating. Any help is greatly appreciated. Thanks in advance,
P.S. 
I have reformatted the 500 gig drive back to ntfs, and will wait for a definative answer before installing Ubuntu again.
Smitty

Now that you formatted the SATA disk there is no way to see what may have been the issue. Install Ubuntu again and if there is a problem we can troubleshoot from there.

---

### Post by presence1960 on 2010-01-25
> **bigsmitty64 said:**
> Hey everyone,
I currently have Windows Vista Home Premium installed on my c drive, (ide).
I installed  Ubuntu 9.10 32 bit,onto a new drive 500gb (sata).  I chose the "erase and use entire drive" option at install. Install goes great but,no matter what I do, every reboot goes straight to windows. No grub menu at all. I have changed the boot order of the drives in my bios a few times. Nothing helps.  I HAVE successfully had Ubuntu installed on this machine before, however, I had to reinstall because I got a grub error after an update and could not figure the problem out. But every install has failed since. I have tried 32 bit and 64 bit, as my machine is 64 bit. It is so frustrating. Any help is greatly appreciated. Thanks in advance,
P.S. 
I have reformatted the 500 gig drive back to ntfs, and will wait for a definative answer before installing Ubuntu again. 
Smitty

Now that you formatted the SATA disk there is no way to see what may have been the issue. Install Ubuntu again and if there is a problem we can troubleshoot from there. At the Ready to install window click the Advanced button and choose /dev/sdx  where x = your SATA disk (i.e. sdb) This will put GRUB on the MBR of your SATA disk. When the install is complete and you reboot go into BIOS and set the SATA disk to boot before the IDE disk in the hard disk boot order. This will bring up GRUB when you boot.

---

### Post by bigsmitty64 on 2010-01-25
> **presence1960 said:**
>  At the Ready to install window click the Advanced button and choose /dev/sdx  where x = your SATA disk (i.e. sdb) This will put GRUB on the MBR of your SATA disk.

Thank you so much. It worked like a dream!

---

