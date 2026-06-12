---
title: "upgrade reinstall"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by soni1770 on 2009-11-22
ok, i'm running 9.10 32 bit with just one partition, (9.10 and home are together)

i'm going to install 9.10 64 bit

if i do a manual install and make 2 seperate partitions
 1 for home, 1 for 9.10

does this mean when i do a fresh install to 10.04 i can just keep my home directory with things like wallpaper, screen layout remaining

i think all the extra programs will disapear , true?

i like to do fresh install as this makes for less problems i think.

so, if i change from 32 to 64 bit how big should each partition be?

i have a 250gb hdd.

how much space does ubuntu need, if i add extra programs do they all go on ubuntu partition?

well, thanks for anyones who can help, 

thanks,

regards 
soni1770

---

### Post by Diabolis on 2009-11-22
Yes, you are right.

If you install new software, it will go to the root, Ubuntu, partition.
Having a separate partition for your home folder will allow you to keep all your settings through different installations.

I suggest:
5-7GB for root
5-7GB for home
And the rest for a storage partition which should be formated as **EXT3**. It has been discovered that **EXT4** will corrupt files larger than 512mb, so movies and .iso files are at risk and they are likely to be stored in a "storage" partition.

---

### Post by soni1770 on 2009-11-22
hi Diabolis,

ok, 
so it's prob a good idea to have seperate partitions as i can keep my layout, background and so forth. 

but can i ask,

do i need a home and a storage partiton, would just a home work the same,

now i have a lot of files greater than 512mb, both on my internal hdd and also a 1tb external hdd, 

both of these hdd are ext4 and i have not had any major problems, no corrupt files at all and i have 100's of large files,

there all backed up on a 1tb ntfs external hdd as well, just in case,

so i guess my question is

will just 2 partions work,

1 home
1 root/buntu.

cheers

---

### Post by Diabolis on 2009-11-22
Sure, 2 partitions will work fine. Its a matter of what works best for you. What I suggested is how I installed it. I rather have a storage partition that is always clean of configuration files etc.

Even when a separate home partition is made to be able to keep settings through different installations, sometimes I wipe it out because I mess too much with the config files. Also I might have many distros installed at once, so I can access the storage partition from different Linuxes with different users.

---

### Post by soni1770 on 2009-11-22
cool cool,

cheers for your help,

i'll have a think about what to do,
 going to go to 64 bit tomorrow.

thanks

---

