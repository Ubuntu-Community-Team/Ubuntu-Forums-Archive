---
title: "Cant install due to corrputed hdd"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Honz@ on 2011-05-02
i tried installing ubuntu 11.04 on my external hard drive (i already had ubuntu lucid lynx on it and it worked), but the installation crashed. I reported it on launchpad, but they told me that my logs say my hdd is corrupted (here they are btw)
```
May  1 17:55:56 ubuntu kernel: [  585.397622] sd 5:0:0:0: [sdc] Unhandled error code
May  1 17:55:56 ubuntu kernel: [  585.397627] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
May  1 17:55:56 ubuntu kernel: [  585.397632] sd 5:0:0:0: [sdc] CDB: Write(10): 2a 00 00 00 08 00 00 00 08 00
May  1 17:55:56 ubuntu kernel: [  585.397645] end_request: I/O error, dev sdc, sector 2048
May  1 17:55:56 ubuntu kernel: [  585.397650] quiet_error: 20 callbacks suppressed
May  1 17:55:56 ubuntu kernel: [  585.397654] Buffer I/O error on device sdc1, logical block 0
May  1 17:55:56 ubuntu kernel: [  585.397657] lost page write due to I/O error on sdc1
May  1 17:55:56 ubuntu kernel: [  585.397668] EXT4-fs error (device sdc1): ext4_journal_start_sb:260: Detected aborted journal
May  1 17:55:56 ubuntu kernel: [  585.397675] EXT4-fs (sdc1): Remounting filesystem read-only
May  1 17:55:56 ubuntu kernel: [  585.397679] EXT4-fs (sdc1): previous I/O error to superblock detected
May  1 17:55:56 ubuntu kernel: [  585.400621] sd 5:0:0:0: [sdc] Unhandled error code
May  1 17:55:56 ubuntu kernel: [  585.400625] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
May  1 17:55:56 ubuntu kernel: [  585.400630] sd 5:0:0:0: [sdc] CDB: Write(10): 2a 00 00 00 08 00 00 00 08 00
May  1 17:55:56 ubuntu kernel: [  585.400643] end_request: I/O error, dev sdc, sector 2048
May  1 17:55:56 ubuntu kernel: [  585.400647] Buffer I/O error on device sdc1, logical block 0
May  1 17:55:56 ubuntu kernel: [  585.400650] lost page write due to I/O error on sdc1
```

so, how could i fix it? Already tried fsck, it repaired it so i tried to install again, same happened.

---

### Post by dino99 on 2011-05-02
open gparted to see if some blocks are not aligned or else. Better to format it again (after some backup if your data is on too) or only / and swap then reinstall a fresh release

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Dutch70 on 2011-05-02
If you can get it to show up in Disk Utility, try checking the SMART data. 
If not, try going to the manufacturers website to see if they have some tests you can run on it.

---

### Post by Honz@ on 2011-05-02
tried to reformat /, but error occured,
this is the error

GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    **Create Primary Partition #1 (ext4, 18.63 GiB) on /dev/sdc**  00:00:02    ( ERROR )             create empty partition  00:00:02    ( ERROR )       libparted messages    ( INFO )             *Input/output error during write on /dev/sdc*       *Error fsyncing/closing /dev/sdc: Input/output error*          ========================================

---

### Post by Honz@ on 2011-05-04
ok, so i ran ESWIN SMART utility diagnostic and it didnt find any errors. But if hard drive is ok, why cant I install ubuntu?

---

### Post by jmore9 on 2011-05-04
You could try booting into gparted live cd and check the file system and also format partitons if desired.  It also doe Windows partitions also.

---

### Post by Dutch70 on 2011-05-04
There are a lot of bug reports regarding libparted 2.3 & Gparted with external devices. You may want to try to use a different partitioning tool to reformat. I've heard of, but never used [[COLOR="Red"]Parted Magic[/COLOR]]("http://partedmagic.com/doku.php?id=downloads") 
There are others too.

---

### Post by Honz@ on 2011-05-07
so i tried
parted magic - didnt work
using unetbootin instead of universal USB installer - nope
intsalling 10.10 - freezes after choosing timezone
installing 10.04 (wich i installed succefully once on this computer) - same as 10.10
using 11.04 alternate with CD instead of USB (lowest possible burning speed) - freezes after i getting time from some server or something

---

### Post by Not unique on 2011-05-07
Under Windows I would of formatted with a free low level formatter is there one for Ubuntu and would it help in this case?

---

### Post by jmore9 on 2011-05-07
Gparted Live CD.  If you can download a copy, burn to cd, then boot into it. It has linux file system support included as well as Windows.

---

### Post by Not unique on 2011-05-07
Gparted wont do low level formatting though. or will it? I'm sue it doesn't.

---

### Post by Honz@ on 2011-05-14
So I tried to use manufacturers tool (Eswin samsund SMART utility) to zero-fill my external hd, and the program gave me error right after it started. It doesnt say what kind of error, it just says error.

---

### Post by Dutch70 on 2011-05-14
I would be checking on the warranty. They should have the info you need on their website.

---

### Post by Honz@ on 2011-05-25
ok, so I zerofilled my hard drive, the same error occured. So its definetaly not the hard drive.

---

