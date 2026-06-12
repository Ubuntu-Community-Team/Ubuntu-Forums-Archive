---
title: "How do I convert an ext3 file system to an ext4? Safely please."
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-10-17
I have/home on a separate hard drive and it is formatted to ext3.

A Karmic i386 new install (with ext4 format) has been successful except that I have lost some sound control and get some garbled reports from lshw.

Can I change the /home drive to ext4 whilst preserving the data? 

I have backed it up on an external drive so would be prepared to take a 'normally ok' risk.

---

### Post by falconindy on 2009-10-17
Simple enough...
```
tune2fs -j /dev/DEV
tune2fs -O extents,uninit_bg,dir_index /dev/DEV
e2fsck -fpDC0 /dev/DEV
```
The first line ensures that you have journaling enabled on the drive (you should already). The 2nd line does the dirty work of the actual conversion. The last line is necessary to clean up some structures that were modified during the conversion.

edit: In case you're curious, I've done this myself before. Didn't take much longer than it would have if I were just formatting a partition fresh as ext4, and all my data was preserved. Hmmm, reminds me I still need to convert my root drive...

---

### Post by psyke83 on 2009-10-17
Why didn't you just link to the full instructions [here]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")?

I previously read that converting a filesystem from ext3 -> ext4 may result in sub-optimal performance, but perhaps that's not an issue any longer?

---

### Post by FuturePilot on 2009-10-17
> **psyke83 said:**
> Why didn't you just link to the full instructions [here]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")?

I previously read that converting a filesystem from ext3 -> ext4 may result in sub-optimal performance, but perhaps that's not an issue any longer?

That's still an issue and will be an issue until the defragging tool is available so you can move all the files over to extents.

---

### Post by bwallum on 2009-10-17
Thanks all, I had found the [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4) link but though it was not offering a 'full' conversion hence my question.

I bit the bullet, copied the /home directory to an external drive and changed format to ext4 using gparted. [COLOR="Red"]IT COMPLETELY ELIMINATES ALL DATA[/COLOR] I should add for anybody following in a rush. Backup is essential. I then copied the externally backed up /home folder on to the newly formatted ext4 drive and all was well.  Just for the record the backup file structure was fat32.

---

