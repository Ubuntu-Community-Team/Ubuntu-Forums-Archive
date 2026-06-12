---
title: "Reinstalling grub on ubuntu 10.10"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by Syl4r on 2011-11-25
Hi!
I've got an HDD with Ubuntu 10.10 on /dev/sdb1.
Later on i installed Ubuntu 11.10 on /dev/sdb5, so now my grub is the one from 11.10.
I'd like to reinstall grub on my 10.10 so i can remove 11.10.
How could i do that??
Thanks!
(sorry for my english, i'm Italian :D )

---

### Post by darkod on 2011-11-25
The grub boot menu should currently show you an option to boot the /dev/sdb1 version.

Select it and boot it once. After it has booted, open terminal and just run:

sudo grub-install /dev/sdb

Note: I assume you use grub2 on /dev/sdb. If not, change the command above to use the correct disk.

If you can't boot 10.10 there is different way you can install its grub on the MBR.

---

### Post by Syl4r on 2011-11-25
Thanks for the reply!
It worked fine!
But there's another problem: i have another small HDD in which i have installed Win7. Now the grub doesn't prompt me anymore to choose an OS because it finds just Ubuntu 10.10.
I tried running ```
sudo update-grub
``` from my 10.10 and this is what i get:
```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-31-generic
Found kernel: /boot/vmlinuz-2.6.35-30-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

### Post by ajgreeny on 2011-11-25
It looks as if you have legacy grub on the system, not grub2.  Did you update from previous versions of ubuntu and choose to keep the old grub setup with a menu.list file instead of grub.cfg as grub2 would give you?

Click on the **Boot-info-script** link in my signature to use the Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Syl4r on 2011-11-25
> **ajgreeny said:**
> It looks as if you have legacy grub on the system, not grub2.  Did you update from previous versions of ubuntu and choose to keep the old grub setup with a menu.list file instead of grub.cfg as grub2 would give you?

Click on the **Boot-info-script** link in my signature to use the Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Hi!
No, i didn't update from previous versions of ubuntu, i installed directly 10.10.
...don't know if can help, anyways in the "/boot/grub/" folder, there are both files (menu.lst and grub.cfg).

Here's the content of "result.txt":
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 80.0 GB, 80032038912 byte
255 testine, 63 settori/tracce, 9730 cilindri, totale 156312576 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   156,311,551   156,309,504   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   419,432,447   419,430,400  83 Linux
/dev/sdb2         419,432,448 1,468,008,447 1,048,576,000   7 NTFS / exFAT / HPFS
/dev/sdb3       1,468,008,448 1,471,154,175     3,145,728  82 Linux swap / Solaris
/dev/sdb4       1,471,156,222 1,705,529,343   234,373,122   5 Extended
/dev/sdb5       1,471,156,224 1,705,529,343   234,373,120  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        22BC777C7949C105                       ntfs       WINDOWS
/dev/sdb1        552aa468-1c77-4e32-b6d4-179509bd9c52   ext4       LINUX
/dev/sdb2        406221DC5A431D32                       ntfs       MAGAZZINO
/dev/sdb3        3f133201-5c30-4ff0-8f23-3a9d5faa1508   swap       
/dev/sdb5        128f6099-259d-4b16-8466-66d92e89d7a8   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/WINDOWS           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/MAGAZZINO         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

./boot_info_script.sh: riga 1888: (  / 2 ) + 16 : errore di sintassi: atteso un operando (il token di errore è "/ 2 ) + 16 ")


```

---

### Post by efflandt on 2011-11-25
Not sure how you ended up with grub legacy. But how to switch it to grub2 is explained on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Since it looks like you are booting from the **sdb** mbr, you need to make sure that grub2 ends up installed on /dev/sdb.

---

### Post by Syl4r on 2011-11-25
> **efflandt said:**
> Not sure how you ended up with grub legacy. But how to switch it to grub2 is explained on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Since it looks like you are booting from the **sdb** mbr, you need to make sure that grub2 ends up installed on /dev/sdb.

Thanks for the link! it was very useful!
I used "Boot-Repair" ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ) and my grub 1.98 is now perfectly installed and loads all my Operating systems!
Thanks again!

---

