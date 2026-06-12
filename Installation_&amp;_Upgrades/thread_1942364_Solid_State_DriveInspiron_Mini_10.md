---
title: "Solid State Drive/Inspiron Mini 10"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by Bias on 2012-03-17
Hi,

Just wondering if someone can point me in the right direction. I recently installed Ubuntu 11.10 from here [http://www.ubuntu.com/certification/hardware/201010-6646](http://www.ubuntu.com/certification/hardware/201010-6646) onto my Dell Inspiron mini 10 completely overwriting windows, this worked with no issues what so ever.

A couple of days ago, I decided to try this again on the same machine but with the HDD swapped for a SSD.

The install procedure I went through was as far as I can tell identical it was still on the USB I had used previously. The install finished, the machine rebooted and I was at the logon screen very quickly :), I logged in sorted wireless etc. then restarted.

This time I got:-

error: unknown filesystem.
grub rescue>

I searched and found this [https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode) , following the procedure I could get as far as "insmod normal" in the "Rescue Mode (''grub rescue>'') Booting" section before it failed.

I have tried rebuilding again and the same thing happened (this time I did not tweak any settings after the build but just rebooted immediately).

I am fairly lost as to how to progress this. If anyone has any ideas please let me know.

Thanks,

Nick.

---

### Post by darkod on 2012-03-17
Is the Sata mode set to AHCI or IDE in BIOS? (if you have the options)

For a SSD it's better to be used as ahci. For a HDD and if it came with XP it might be left at ide.

Although that should not stop the ssd working, it will only be slower.

Also, you can try booting into live mode, running the boot info script from the link in my signature and post the results as explained there. That will show much more details.

---

### Post by Bias on 2012-03-17
Hi Darko,

Thank you for your speedy reply :).

I have checked the BIOS, it is fairly rudimentary and does not have the option you mention.

I have run the script you suggest and am attaching the results, I am trying to make some sense of them but it's somewhat overwhelming :).

Thank you,

Nick.

---

### Post by darkod on 2012-03-17
From what ever reason, it can't read the linux partitions any more. But I can't see any reason.

fdisk reports them correctly it seems, with correct type, etc. But mounting fails, and also blkid doesn't read them.

You can try first deleting all partition with Gparted in live mode, also writing a new msdos partition table, and then try to install again. But I can't promise that would work since I can't see any reason for your problem.

---

### Post by Bias on 2012-03-18
Hi Darko,

Thank you for looking and for your advice. I too am not optimistic that this would provide a solution however I decided to try it, on entering GParted it showed some contradictory results, so I thought I would post them here in case they shed more light on the issue.

The boot partition /dev/sda1 shows as an unknown file system, there is an ! in a red circle this gives possible reasons why the file system could not be detected, these are:-
-The file system is damaged
-The file system is unknown to GParted
-There is no file system available (unformatted)
-The device entry /dev/sda1 is missing

The swap partition /dev/sda2 shows as extended.

Within the swap partition there is a further partition /dev/sda5, this shows as being an unknown file system and also has an ! in a red circle, giving the same reasons as with /dev/sda1 above.

GParted does not seem to offer the ability to 'edit' these details, I do not actually know if this is possible but if anyone does know of a utility that would let me configure this manually please let me know.

Having written down all the information I will now try the procedure.

Thank you for your help.

Nick.

---

### Post by darkod on 2012-03-18
If you have no data to save from that disk, you can try in Gparted to go into the Device menu and select Create Partition Table... That will create by default a new blank msdos table with no partitions.

Then save the changes in Gparted. After that you can try a new install. Something went wrong if it's not recognizing the filesystems.

---

### Post by Bias on 2012-03-18
Thanks Darko,

I have tried that and on this install only the boot partition is not recognised by GParted, it now sees the Linuk-swap on /dev/sda5 A definite improvement :). I will try it again.

Nick.

---

### Post by Bias on 2012-03-18
Same thing but this time while trying stuff at the grub rescue prompt I got a free magic is broken error. Think I should try this in another machine!

---

