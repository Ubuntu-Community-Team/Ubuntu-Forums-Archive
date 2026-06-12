---
title: "installing windows on an ubuntu machine"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by DrewB on 2008-01-02
Hello, I am running Ubuntu 7.10 on a Gateway AMD64 MX6440 laptop with 100GB HD.
I need to install Windows XP alongside it so I can dual-boot.
I have the following configuration:

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3307    26563446   83  Linux
/dev/hda2           11812       12161     2811375    5  Extended
/dev/hda3            3308       11811    68308380   83  Linux
/dev/hda5           11812       12161     2811343+  82  Linux swap / Solaris

/ is mounted on hda1 (25GB) and /home on hda3 (65GB) and the swap is in the extended partition (hda2 & hda5)

So I want to resize hda3 (/home) and make a new partition of 30GB and install Win XP there.

I've seen that I will need to restore GRUB to the MBR.

Does anyone know if this will work? Will I be able to dual-boot into Win-XP or Ubuntu after I'm done?

Thanks a lot for any help anyone can give.

---

### Post by lizzard on 2008-01-02
After Windows installation you need to boot up with a Linux Live-CD to restore the boot manager (GRUB). [  Here ](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub) you'll find an instruction how to do that.

---

### Post by DrewB on 2008-01-03
Thanks for the reply lizzard, however I did know that. From my original posting:
> I've seen that I will need to restore GRUB to the MBR.
I really wanted to know if I would be able to dual-boot with Windows with the configuration I will have, as described above.
Thanks

---

