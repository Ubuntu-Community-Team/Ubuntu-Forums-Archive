---
title: "an error occurred while mounting /media.. help"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by q8_legend on 2012-05-27
Hi

My computer was just working fine until I tried to install the new ubuntu(12.04) while  remaining the os's i already have.

I have Ubuntu 11.04 & win7, & they are installed on my HDD.

I have 4 HDD. my old ubuntu(11.04) is installed in a separated HDD & i have 2 other HDD for data & files(not system files). and the last HDD i had separated to partitions, & one of its partition has Win7.

the new installation of the ubuntu(12.04), i installed it in the win 7 Hdd(which have multiple partitions). 

the problem occurred now. after I have installed it, when i tried to run my computer, the boot loader won't start. I heard that i should use 'boot-repair' to fix the grub, & it did fix it but the Win7 is now not working & not shown in the boot loader. 

my problem is not here only, now when i tried to run my computer, i can't access & see one of my HDD(that have data files only), it doesn't show.

also, when the computer is running(while booting), this msg appear 'an error occurred while mounting /media/ my HDD name , press s to continue or m to manual recovery'.

Note:
the drive that shown in the booting screen(unable to mount), this is the same drive that i can't access it when the computer start.

how can i fix the problem ???

Thanks alot

---

### Post by raja.genupula on 2012-05-27
put a live cd and run fsck for that HDD .

---

### Post by q8_legend on 2012-05-28
> **raja.genupula said:**
> put a live cd and run fsck for that HDD .

ok, i will do it. and how about the win 7 that i can't see it now in the boot loader. how can i fix that problem ??

thanks alot

---

### Post by raja.genupula on 2012-05-28
open your terminal and type as 
```
sudo update-grub
```

---

### Post by q8_legend on 2012-05-28
> **raja.genupula said:**
> put a live cd and run fsck for that HDD .

unfortunately nothing is changed... what should i do now ??

thanks

---

### Post by q8_legend on 2012-05-28
I thing the problem is from the 'fstab' , since the problem that i'm facing it right now(mounting error) is for the 3 partitions. 2 of them, i have deleted them & combine them in one new partition(merging them together), & the last one i didn't touch anything with it.

but some one told them the problem is may from the 'fstab' since it may occur from the numbering of the partitions since they have changed right now, & the fstab may(for sure; from the problem that occurred) have the old list.

but i don't know if from it the problem or not..

any help ??

thanks

---

### Post by raja.genupula on 2012-05-28
```
cat /etc/fstab
```
post its output

---

### Post by q8_legend on 2012-05-28
> **raja.genupula said:**
> ```
cat /etc/fstab
```
post its output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
# /dev/sda1	/	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/sde1	/media/1_TB	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/sdd1	/media/620040GB	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf800
/dev/sdb1	/media/Ubuntu___xp_32	ntfs-3g	defaults,locale=en_US.utf8	00
/dev/sdb3	/media/Win_7	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/sdb2	/media/Xp_32_New_	ntfs-3g	defaults,locale=en_US.utf8	00
/dev/sdc5	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0



note:

the partitions that gave me errors are:
/media/1_TB
/media/Xp_32_New_	
/media/Ubuntu___xp_32

while only the '1_TB' is exist(which hold the data), while the other are not available right now since i'v delete them & merge them together to a new one partition.

---

### Post by raja.genupula on 2012-05-28
add an entry in the format like this with 
```
sudo gedit /etc/fstab
``` but before doing any edit ,take a back up 
as ```
sudo cp /etc/fstab /etc/fstab.old
```

```
UUID=847CFB207CFB0BA4	/media/<put your drive > ntfs-3g		user,fmask=0111,dmask=0000   0   0
```

you can get UUID by blkid and put there your new drive label name.

---

### Post by q8_legend on 2012-05-28
> **raja.genupula said:**
> add an entry in the format like this with 
```
sudo gedit /etc/fstab
``` but before doing any edit ,take a back up 
as ```
sudo cp /etc/fstab /etc/fstab.old
```

```
UUID=847CFB207CFB0BA4	/media/<put your drive > ntfs-3g		user,fmask=0111,dmask=0000   0   0
```

you can get UUID by blkid and put there your new drive label name.

i'v used 'sudo blkid'

and this is the output:

/dev/sda1: LABEL="930GB" UUID="8428888B28887E44" TYPE="ntfs" 
/dev/sdb1: UUID="8a095a6b-a1bb-452a-a32c-b1bc0d8790a8" TYPE="ext4" 
/dev/sdb3: LABEL="Win 7" UUID="9672D87372D85A17" TYPE="ntfs" 
/dev/sdc1: UUID="fe758b02-bff5-4890-8467-7c0467665752" TYPE="ext4" 
/dev/sdc5: UUID="a196778d-3e42-4381-ae12-534ad4048f8e" TYPE="swap" 
/dev/sdd1: LABEL="620 GB" UUID="20B4641EB463F4A6" TYPE="ntfs"


my hard drive isn't available here (/dev/sde1). so, can i use you UUID ?? and where should i add it ?? is it to the last line in the file  ??

thanks

---

### Post by raja.genupula on 2012-05-28
do one thing put a live cd and run live session . check is that harddisk mounting there or not . i think it have some errors .

---

### Post by q8_legend on 2012-05-28
> **raja.genupula said:**
> do one thing put a live cd and run live session . check is that harddisk mounting there or not . i think it have some errors .

the same . it doesn't show at all.

---

### Post by raja.genupula on 2012-05-28
The HDD you merged is visible in other Operating systems you got ?

---

### Post by q8_legend on 2012-05-29
> **raja.genupula said:**
> The HDD you merged is visible in other Operating systems you got ?

How can i Know !! ? Since, the Win is not working right know after installing the new ubuntu.
but its shown here in ubuntu right now.

---

### Post by q8_legend on 2012-05-29
I'v solved my problem. it seems that my HDD drive that won't boot have an issue an it seems that its damaged. so, iv used 'testdisk' to retrieve my data from it. and it works great as it should be... you can check this video for how you can do it... Thanks alot again... [http://www.youtube.com/watch?v=pnNefxLydV8](http://www.youtube.com/watch?v=pnNefxLydV8)

---

