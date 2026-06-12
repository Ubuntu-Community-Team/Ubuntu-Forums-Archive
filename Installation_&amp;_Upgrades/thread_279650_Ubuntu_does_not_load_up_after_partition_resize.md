---
title: "Ubuntu does not load up after partition resize"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by Aramis on 2006-10-18
Dear all,

Recently I have run out of space on my root partition. Since I had planned to install 2 Operating Systems on my laptop PC, I still had a fair amount of free space. Using gParted I copied the content of my home drive to a new partition (the previously free space), and resize the root partition accordingly.

I all went well until I wanted to access the operating system once again. The computer boots no problem, and I can even see the Ubuntu splash screen . However, 1/3 of the way in the boot process stops with the following error:

```

fsck.ext3 : no such file or directory while trying to open /dev/hda5
/dev/hda5
The super block could not be read or does not describe a correct
ext2 filessystem. If the device is valid and it really contains
an ext2 file system (and no swap or ufs or something else), then
the supperblock is corrupt, and you minght try running e2fsck 
with and alternate superblock:

   e2fsck -b 8193 <device>

* File system check failed. Please repair manually

```

I haven't the first clue about what to do, where to start, the tools I need and so on. It is true that I could simply re-install my system, but I have read some many times that Partition Magic can do the operations described above no problem, that I am convinced that the Open Source Community can emulate it :mrgreen: .

Cheers,

krzAr@mi$
System :
OS : Ubuntu Dapper Drake
Proc : AMD Duron 1.1Ghz
Mem : 256 MB
HDD : Maxtor 20GB
root partition in ext3
home partition in ext3
Manufacturer : SAMSUNG

---

### Post by Kateikyoushi on 2006-10-18
Let's see how does your new partition layout looks like.

```
sudo fdisk -l
```

Then post your fstab.

```
cat /etc/fstab
```

---

### Post by Aramis on 2006-10-18
Hello there!

here is the ouput of "fdisk -l" :
```

/dev/hda1 1     1189 9550611   83 linux
/dev/hda2 1190  1304  923737+  82 Linux Swap / Solaris
/dev/hda3 1305  2432 9060660   83 Linux

```


Then, "fstab":
```

/dev/hda1 /      ext3   defaults, errors=remount -ro, noatime, data=writeback 0 1
/dev/hda5 /home  ext3   defaults, 0 2
/dev/hda6 none   swap   sw        0 0
/dev/hdd  /media/cdrom0 udf, iso9660 user, noauto 0 0
/dev/fd0  /media/floppy auto,  rw, user, noauto 0 0

```

I performed these commands from the prompt I have access too when the boot process fails. I forgot to mentions that if I type "startx" from that prompt the OS loads up... except that there is no data in the HOME folder/drive.

Thanks for such a speedy response.

Ar@mi$

---

### Post by Aramis on 2006-10-18
Solved!

I matched the content of FSTAB with the information output'd by fdisk -l . The computer now boots up no problem, the OS is just as I left it and so is my data :mrgreen: I am one happy chap.

Before I close this thread, I would like to know if there is anything extra I should take care of? Special measure or else.

Just let me know!

Big thanks to Kateikyoushi

Ar@mi$

---

### Post by Kateikyoushi on 2006-10-18
Sorry for the late reply, I am glad you managed to solve it.
I think there is nothing you should take care of concerning this, it is normal that linux can't boot if the partition layout changes.
Before any hard drive related changes creating a backup is recommended.

---

### Post by Aramis on 2006-10-19
Hi there,

I would not have understood the problem between the current partition layout and the one described in FSTAB, if it wasn't for your intervention; so it is 50 50 each ;) .

I did back up my data before proceeding with the gParted. Indeed, my research lead me to believe that the OS might be broken (e.g no operating system at all) after re-partitioning. However, I did not expect a half an Operting System. In all the tutorials I read on partitioning disks with Linux none of them mention the difficulties that might arise once the job is done. I guess it would simple enough for authors to suggest double checking the information included in FSTAB.

Have a nice day,

Ar@mi$

---

