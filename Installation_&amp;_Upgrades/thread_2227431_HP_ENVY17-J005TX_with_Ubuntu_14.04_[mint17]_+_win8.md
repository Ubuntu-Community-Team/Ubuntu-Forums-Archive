---
title: "HP ENVY17-J005TX with Ubuntu 14.04 [mint17] + win8 on separate drives"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by Col-1023 on 2014-06-02
I haven't bought a new computer in ages, so have no experience with this whole secure boot mess.

I've done alot of reading and it seems like a real horror show, so I'm looking for a fairly easy solution.

The notebooks I'm thinking of getting are HP ENVY17-J005TX [Australia} with the following specs

i7 4700MQ
16GB RAM
2 X 1TB HDD
Nvidia GT740m 2GB
17.3" screen
Win 8 or win8.1 pre-installed.

I'm not that interested in windows, but don't want to brick the new notebooks, so am wary of deleting windows straight away, especially with this whole uefi-secure boot thing.

I assume win8 will be installed on the 1st hdd, ie sda1, so I was hoping to use all the disk 2 for wither ubuntu 14.04 or mint 17.

1 - Has anyone installed ubuntu 14.04 on this type of machine, and how well did it go?

2 - Assuming I don't boot into win8, If I just go into the bios, disable secure boot, will the liveusb installation work fine by recognising that there is a free 2nd hdd and choose that to install on, or will I have to pick this manually and pick partitions on this drive manually?

3 - It seems with hp envy line has problems with the bootloader picking the ubuntu drive over the windows, that is if you select to boot from the 2nd hdd in bios, the bootloader will still boot from the first, did this still hppen with a liveusb install of ubuntu 14.04.

I'm hoping that ubuntu 14.04 has made it easier to dual boot on separate drives with the hp envy 17, since most of what I've read applies to ubuntu 13.10, 13.04 or 12.04lts, or mint 16.

Sorry for the long post, any help appreciated.

---

### Post by Col-1023 on 2014-06-02
I've done some more searching and it seems that you can't boot from the drive in the 2nd bay, that is the 2nd hard drive.

The suggestion is to physically swap the drives, so that the 2nd drive can be booted as sda.

Is this still the case for this model?

How easy is it for a total hardware noob, an absolute beginner to do without damaging the notebook?

Otherwise the only options is to install ubuntu 14.04 on the 1st hard drive alongside windows, if someone has done this with this or similar model and ubuntu 14.04 or mint 17 rc or mint 17, I would be interest to know how it went.

TIA.

---

