---
title: "re-instal to partition failed with Ghost.  Need help."
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by tomaasj on 2007-07-16
Definetely need help,


My Dell Inspiron was set up with dual boot:  partitions for Vista, Ubuntu, Data.  It Works (-ed).
Had to re-install Ubuntu backup from image which was created with Ghost on a mini Boot CD.  The Image backup resides on an external hardrive (NTFS filesystem).  I used Ghost again to put the image on the partition (ext3 filesystem) to restore Ubuntu.  I noticed that Ghost tries to create an ext2 filesystem on the partition.  On reboot of my laptop, Ubuntu initially starts, but boot fails.  Something like corrupted filesystem etc.

Is it possible with other tools (similar to Ghost) on a boot CD to reformat the partition on the hardrive of my laptop which initally held Ubuntu, re-create the ext3 filesystem (which is now most probably corrupted by Ghost, when trying to re-install the Image Backup) and restore with the Image, which was originally created with Ghost ? And keeping the other partitions intact in the process, so dual boot remains etc.

I am a complete beginner so, please, communicate with me as such.  It would be great to recreate my laptop as was.  I now have to work with Vista (which BTW boots normally from the same laptop at the moment).

Help would be appreciated with this distressing situation...

Tomaasj

---

### Post by Pumalite on 2007-07-16
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by tomaasj on 2007-07-17
Hi,

thanks for responding.

I am completely new to these things.  If I download the LiveCD as described on the link, will it allow me to not only restore the partition file system back to an ext3 filestructure but  restore the Ubuntu backup Image file, originally created with Ghost, from the external hardrive as well ?  In the meantime I will go ahead and try to figure it out,

gr. Tomaasj

---

### Post by Pumalite on 2007-07-17
As long as it works; it's great!

---

### Post by tomaasj on 2007-07-17
Hi,

another question:

On the FAQ of [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I found the following:


"5 : Why are some menuitems disabled?
  
2. At startup gparted decides which operations on which filesystems are supported. 
For instance, to create an ext3 filesystem gparted needs mkfs.ext3. 
If this cannot be found on your system, the creation of an ext3 filesystem is not possible
 and therefore disabled in gparted. The same goes for copy, resize etc.. "

Will I run into this problem ?

If I understand correctly, I boot from the LiveCD ?  Can I then still reformat the partition and give it the ext3filestructure, and restore the Backup Image onto it ?

gr. Tomaasj

---

### Post by Pumalite on 2007-07-17
Don't worry. The most worrying thing at this point is that you are running Vista. I don't know how you partition originally, but if you have to partition again, you have to do it from WITHIN Vista. As for Gparted, if you cannot format ext3, you could choose ext2 or reiserfs . After you partition with Vista, you could use Gparted to check that there is a partition. Formatting is not necessary. The installer can do it.

---

### Post by tomaasj on 2007-07-17
OK, the moment I have the LiveCD I'll go ahead.  Keep you informed...

---

