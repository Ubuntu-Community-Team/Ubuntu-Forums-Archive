---
title: "Reinstalling XP with 9.10 dual-boot..."
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by RonPDX on 2009-12-08
Hello everyone, 

Currently I am running an XP/9.10 dual-boot. While I primarily use Ubuntu for almost everything, there are some work related tasks that require Windows. I also have to use XP for watching anything in flash, since flash does not work properly in Ubuntu. 

The only concern I have is the boot-loader once I do a fresh install on the Windows partition.

Once I restore My Documents and Settings folder, will the boot-loader be restored? or do I have the reinstall Ubuntu as well? 

If I do have reinstall Ubuntu, what is one of the better backup/restore utilities for an external HDD?

Thanks, 

Ron

---

### Post by starcraft.man on 2009-12-08
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Grsync is nice for synchronizing files to a external storage.

I don't know about flash, it works reasonably well, though I agree that it does just seem to work "better" on windows overall. I'm hoping for the 64 bit version.

As to booting, you don't need to reinstall Ubuntu, just reinstall GRUB to the mbr, which will be overwritten by windows bootloader. See [grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") page.

---

### Post by RonPDX on 2009-12-08
Thanks Starcraft.man, your help is appreciated.

---

### Post by darkod on 2009-12-08
Reinstalling XP will write the windows bootloader to the MBR of your disk. After you check that XP is booting fine and working fine, you'll have to restore just the grub2 on the MBR. If you did a clean install of 9.10 and not an upgrade of 9.04 you would use grub2 then.
Restoring grub2 is very simple, you just boot with the 9.10 cd, select Try Ubuntu and in terminal do:
sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have single disk the above works perfect. In the first command you have to replace /dev/sdaX with your root partition, for example /dev/sda2, /dev/sda5 depending where your root is.
Note: if you have separate /boot partition you also need to mount it.

---

### Post by RonPDX on 2009-12-08
> **darkod said:**
> Reinstalling XP will write the windows bootloader to the MBR of your disk. After you check that XP is booting fine and working fine, you'll have to restore just the grub2 on the MBR. If you did a clean install of 9.10 and not an upgrade of 9.04 you would use grub2 then.
Restoring grub2 is very simple, you just boot with the 9.10 cd, select Try Ubuntu and in terminal do:
sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have single disk the above works perfect. In the first command you have to replace /dev/sdaX with your root partition, for example /dev/sda2, /dev/sda5 depending where your root is.
Note: if you have separate /boot partition you also need to mount it.

Thanks Darkrod, 

I did not do a fresh install from 9.04 to 9.10, I did the upgrade to avoid reinstalling all of the drivers for mythtv and alike. I know I was lazy and should have done a fresh install. 

Since I did the upgrade, will Grub2 work? or will I have to use Grub?

---

### Post by starcraft.man on 2009-12-08
> **RonPDX said:**
> Thanks Darkrod, 

I did not do a fresh install from 9.04 to 9.10, I did the upgrade to avoid reinstalling all of the drivers for mythtv and alike. I know I was lazy and should have done a fresh install. 

Since I did the upgrade, will Grub2 work? or will I have to use Grub?

Oh, good question. If you upgraded, then you still have grub. See here for original grub > [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB).

So to clarify. If you install a clean version of Karmic, you get GRUB2. If you upgrade to karmic, you keep GRUB. Use the right instructions per your situation, they are very different.

---

### Post by darkod on 2009-12-08
> **RonPDX said:**
> Thanks Darkrod, 

I did not do a fresh install from 9.04 to 9.10, I did the upgrade to avoid reinstalling all of the drivers for mythtv and alike. I know I was lazy and should have done a fresh install. 

Since I did the upgrade, will Grub2 work? or will I have to use Grub?

In terminal do:
sudo grub-install -v

That will show you your version which is probably grub1 (0.97 for grub1, 1.97 for grub2). No big deal, restoring grub1 is also easy. You can read here if you want to be prepared in advance:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by phillw on 2009-12-08
Recovering MBR's (Win and Grub) for the various flavours of Win & both grubs is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

As pointed out, if you upgraded from 9.04 --> 9.10 you're still on Grub Legacy.

Regards,

Phill.

---

### Post by RonPDX on 2009-12-08
Thanks everyone...I think I have everything that I need.

---

### Post by RonPDX on 2009-12-08
Thanks everyone for your help. Everything with restoring the bootloader went well and just as you said.

---

### Post by darkod on 2009-12-08
No problem. Glad you got it going.

---

