---
title: "Disk Boot Failure"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by Woozie Mu on 2012-11-05
My vista has been playing up for the past several months. So I put an older HDD in and bumped the original HDD down a couple sata? spots. Ive installed both 9.10 several times and just now 12.10 (which I'm currently using w/ the try feature) onto the spare HDD.  all times it has come up "Disk Boot Failure". Ive googled it and am assuming both harddrives are plugged in as I can open the various files under both harddrives. The spare HDD shows all the Ubuntu files in it too. Ive tried various boot sequences of HDD first, to all HDD. Ive also removed my vista HDD and tried with just the spare.

Thanks for reading. Any help would be appreciated.

---

### Post by 2F4U on 2012-11-05
Is the BIOS configured to boot from the right hdd? This was my problem when I once changed the physical connection order.

---

### Post by danelwillis on 2012-11-05
It could be as simple as the new hardrive having a cache, basically the computer cant boot the HDD because of the cache because it does not know what to do with it, i had this problem but i found out the hardrive i wasa using had an 8mb cache

---

### Post by varunendra on 2012-11-07
> **danelwillis said:**
> It could be as simple as the new hardrive having a cache, basically the computer cant boot the HDD because of the cache because it does not know what to do with it, i had this problem but i found out the hardrive i wasa using had an 8mb cache
I'm not sure I understand you correctly. All HDDs have 'cache', typically ranging from 4 to 16 MB. The BIOS or the OS only 'talks' to the drive's interface, not directly to the disk or cache or anything else. All of that is handled 'internally' by the drive's logic card.

@Woozie Mu,
I second 2F4U's opinion that the boot order may be incorrect (if you are booting from a live usb, or another usb drive is plugged in while booting, some BIOS may detect it as the first boot device if USB booting is enabled). There may be a few other possibilities also -

[LIST]
[*]The MBR of the HDD is empty, i.e., no boot loader is installed on it.
[*]Some BIOS require that you have 'Boot Flag' on the boot partition. Grub doesn't need it, but some BIOS do. You can check (and set if required) this in gparted, or with **sudo fdisk -l** command.
[/LIST]
Please check and confirm these.

---

### Post by Woozie Mu on 2012-11-08
Ok ,just thought I&#8217;d update this in case anyone ever sees this with similar problems. Since the last post i've both removed and the put back in the BIOS battery and changed the new (which in this case is an older model) HDD with a newer sata one. It seems to have done the trick, working fine.

Thanks for all the input guys

---

