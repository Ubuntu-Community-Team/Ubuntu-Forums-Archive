---
title: "no grldr problem"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by river226 on 2010-06-07
Background: So i am running ubuntu 10.04 on a amd computer, and this is the second time i have run into this problem. last time i was playing around with os's, trying to get around some annoyances, and i did a reinstall and it worked just fine, but since i have my computer the way i want it and i really don't want to go through the hassle of a reinstall.

problem: when i boot up my computer i get a no grldr. exact print out:[INDENT]Try (hd0,0) Fat16: No GRLDR
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd1,0): EXT2: _
[/INDENT]I have already tried once to reinstall grub, but i rebooted without unmounting the hd, though i don't think thats the problem, but since that first attempt, i have been unable to boot into live CD mode... please help :(

---

### Post by darkod on 2010-06-07
Were you using Super Grub Disk or something similar? grldr is not a standard grub/grub2 from ubuntu file, as far as I know. It shouldn't need it at all.

To get more details about your setup, please run the boot info script (from live mode for example), and post the content of the results file as explained:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You should be able to boot in live mode any time you want. What ever you did to your hdd has no relation to booting from cd. If the cd is a bootable ubuntu cd and you are booting from cd-rom first, it should work.

---

### Post by river226 on 2010-06-07
No, i have been using standard ubuntu disks downloaded from the main site.

As for the live disks, makes sense, just wasn't sure

---

### Post by tinybit on 2010-06-07
Try (hd0,0) Fat16: No GRLDR <------ this is the first partition on the first drive. It looks like a dell utility partition. You may place grldr in this partition.

Try (hd1,0): EXT2: _  <-------- This is the first partition on the second drive. It should be a ext2/ext3 partition. And your boot record should update using the bootlace.com command. It failed because you were using a very old grldr boot record. Any way, a grldr on ext4 partition cannot be found at this stage. You should use ext2/ext3, or FAT/NTFS.

---

### Post by river226 on 2010-06-07
okay, checked my disks doesn't look like i have one good one... that explains that problem.
as for the grldr problem, now it's a problem with grub... i'm thinking that means i need to reinstall grub.

---

### Post by darkod on 2010-06-07
> **river226 said:**
> okay, checked my disks doesn't look like i have one good one... that explains that problem.
as for the grldr problem, now it's a problem with grub... i'm thinking that means i need to reinstall grub.

You need to burn a good ubuntu cd, so you can run live mode and the boot info script. Without more detailed info it's not good to start throwing commands at your computer. Besides, you need the ubuntu cd to reinstall grub anyway.

I still think grldr is not part of grub1 or grub2 from ubuntu. At least I haven't seen it around.

---

### Post by river226 on 2010-06-07
I think you are right about grldr as everything i find seems to indicate problems with xp or vista for the most part. And I'm gonna go with a live USB

---

