---
title: "Help!!! How Do I Boot My Ubuntu Again?"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by lanem1234 on 2008-04-05
Dear Anyone Who Can Help,

I recently downloaded and installed Ubuntu 7.10. It was great, but I decided to install OpenGEU on another partition to see what it was like. I didn't like OpenGEU and closed from the LiveCD. Next time I booted my computer, it gave me a Grub Error 22. I fixed my MBR so that my Vista partition started up correctly. Now, however, I don't know how to be able to boot Ubuntu because Windows doesn't have a dual-boot manager. So, I though, "I'll just delete my Ubuntu partition and reinstall it." However, when I go into Windows Computer Management and try to delete the partition it says it is an extended partition and cannot be deleted if data is on it. How do I, 1) Go back to GRUB so I can dual-boot again, or 2) Delete my current Ubuntu partiton?

Thanks,
Lane

---

### Post by lanem1234 on 2008-04-05
Dear Anyone Who Can Help,

I recently downloaded and installed Ubuntu 7.10. It was great, but I decided to install OpenGEU on another partition to see what it was like. I didn't like OpenGEU and closed from the LiveCD. Next time I booted my computer, it gave me a Grub Error 22. I fixed my MBR so that my Vista partition started up correctly. Now, however, I don't know how to be able to boot Ubuntu because Windows doesn't have a dual-boot manager. So, I though, "I'll just delete my Ubuntu partition and reinstall it." However, when I go into Windows Computer Management and try to delete the partition it says it is an extended partition and cannot be deleted if data is on it. How do I, 1) Go back to GRUB so I can dual-boot again, or 2) Delete my current Ubuntu partiton?

Thanks,
Lane

---

### Post by tubasoldier on 2008-04-05
Here is a forum thread that will tell you how to re-install Grub from the installation CD.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this helps.  :)

---

### Post by warp99 on 2008-04-05
Well you just have to reinstall the Grub MBR to the drive since all of your boot-loader information is still available in your /boot/grub directory. You can use the Super Grub Disk to repair this issues:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33)

This is the fastest and easiest way to restore the Grub MBR.

---

### Post by p_quarles on 2008-04-05
Moved to Installations & Upgrades.

EDIT: And duplicate threads merged.

---

### Post by creatory on 2008-04-05
I am sorry,I am new to use ubuntu,and now I am using kubuntu7.10.The problem you met as well as I met before when I using Microsoft WindowsXP,I used to use 'fdisk /mbr' to recover the hard-disk mbr ,you can have a try.Perhaps it can solove your problem.

---

### Post by diplomat.x on 2008-04-05
To recover GRUB, do this... 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

There are various ways to get ur grub back.
Mine also got corrupted, i tried 4 methods, Only this>>> Using the Unofficial "Super Grub Disk" <<method worked for me.

I downloaded and burnt that .iso on a cd and booted from it and GRUB was back.

And to delete ubuntu partition. (YOU CRIMINAL!!! LOL) :P

Boot using ubuntu Live CD and run Gparted. Its located somewhere inside System menu. Delete ubuntu partitions....Swap, / and /boot or whatever....

---

