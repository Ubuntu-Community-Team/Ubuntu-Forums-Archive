---
title: "Trying to recover partition table with testdisk"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by ksatta1 on 2012-05-12
I accidentally deleted my partition table. I used dd ... bs=512 instead of bs=440 while trying to remove grub.. doh :D

Anyway I thought it would be easy for testdisk to find the partitions, but it looks like it only found 2 partitions which weren't actually partitions, I think they were some backup files I created with dd/fsarchiver/etc.. I tried deep search too.

Then it suggested to change the heads per cylinders to 8. Trying that now but it looks like it's not finding any partitions.

At the time I accidentally deleted the partition table it was something like this:
<unpartitioned space>
<ext4 partition>
<NTFS partition>
<extended>
  <...>

I'm wondering if the unpartitioned space in the beginning is throwing testdisk off. Maybe if I find where the first ext4 partition starts then I could create some partition from position 0 - beginning of ext4 partition.

I'm thinking of creating a bash script to search for ext4 magic bytes, but if anyone else has more knowledge or something else I could try first :)

Also is there any chance that gpart would work better? (haven't tried it yet, each try takes a couple of hours, the drive is 1TB).

---

### Post by darkod on 2012-05-12
testdisk should scan the disk, that's why it takes so long. So, having unpartitioned space in front shouldn't matter.

I wonder if not having any partition table at all (zeroed out) is throwing it off. It's a bit risky, but what if you create new partition table, and then deep search for the lost partitions?

---

### Post by ksatta1 on 2012-05-12
> **darkod said:**
> testdisk should scan the disk, that's why it takes so long. So, having unpartitioned space in front shouldn't matter.

Yeah, especially the deep search since it probably scans each byte.

> I wonder if not having any partition table at all (zeroed out) is throwing it off. It's a bit risky, but what if you create new partition table, and then deep search for the lost partitions?Now that you mentioned it, it always says that partition table doesn't end at foo or something :D I thought it's "normal" because I don't have a partition table. But that's a good suggestion. It might start searching for partitions from beginning of MBR or something.

thanks, I'll report back.. I might let the current scan finish first and try that tomorrow.

---

### Post by ksatta1 on 2012-05-12
I think I solved it... I chose "Intel" partition type in testdisk before... but ofcourse the partition table wasn't there anymore (which I knew), so I had to select "unpartitioned media".. now it found atleast one correct partition. I'll mark this solved if all goes well.

Thanks Darko :)

---

### Post by ksatta1 on 2012-05-12
I got it fixed (Actually took just a few minutes to scan like this):
- run testdisk
- choose "non partitioned media"
- copy resulting list

- in parted:
mktable msdos
unit chs
rescue [C],[H],[S] [C],[H],[S] (use values from list earlier)

Then it should find the old partition and if the info is correct, answer yes.. Then the partition automounted right away on my Xubuntu :D

Well, now Grub is gone and I didn't lose any data. All this took about 12+ hours LOL

---

