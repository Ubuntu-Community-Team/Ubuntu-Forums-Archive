---
title: "Dual boot Ubuntu 11.04 with  intel raid 1+0: gparted &amp; ubiquity differ"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by mikebridge on 2011-07-04
I'm attempting to install Ubuntu 11.04 alongside my Windows Vista 64 system and I'm not seeing the same thing in Ubiquity as I'm seeing in gparted.  I have four 1TB disks set up as Intel 1+0.

To get to this point I:

1) shrunk my windows partition
2) booted to the Ubuntu live CD
3) installed kpartx
4) ran gparted and set up an extended partition with ext4 and swap in it
5) ran ubiquity.  Since it thinks there are no installed OSes, I chose "something else" over formatting the whole drive.

The problem is that gparted displays the partitions (correctly) as this:

/dev/mapper/isq_idhddichd_ARRAY1 fat16 DellUtility ...
/dev/mapper/isq_idhddichd_ARRAY2 ntfs RECOVERY ...
/dev/mapper/isq_idhddichd_ARRAY3 ntfs OS ...
/dev/mapper/isq_idhddichd_ARRAY4 extended ...
   /dev/mapper/isq_idhddichd_ARRAY5 ext4 ...
   /dev/mapper/isq_idhddichd_ARRAY67 linux-swap ...

But ubiquity sees my drive like this under "Allocate drive space":

/dev/mapper/isq_idhddichd_ARRAY-0
/dev/mapper/isq_idhddichd_ARRAY-1

And it shows no information (i.e. type, mount point, format?, size and used are all blank) for either of these.  The drop-down box for the boot loader shows that ubiquity sees these as 1TB each, making me think it's seeing two RAID-0 arrays instead of one RAID 1+0 array.  And it's not showing the EXT4 partition at all.

Does anyone have any idea what to do at this point?

Thanks,

-Mike

---

### Post by Quackers on 2011-07-04
Is fakeRAID 1 + 0 supported? Not sure about that.

---

### Post by grendel905 on 2011-07-06
FakeRaid 0+1 is supported in dmraid. What I found from hours of searching, is that if I install kpartx in the live environment, GParted will now see the array properly and I can create my partitioning scheme. Ubiquity sees the partitions as well. The installer seems to complete, but my problem happens at the grub installer. It was very late last night while I was doing it, but I am going to give installing Grub manually a go later today.

---

### Post by Quackers on 2011-07-06
Are you trying to install grub to /dev/sda or to the /dev/mapper "drive"? It should be the latter.

---

### Post by grendel905 on 2011-07-06
> **Quackers said:**
> Are you trying to install grub to /dev/sda or to the /dev/mapper "drive"? It should be the latter.

The /dev/mapper drive. But, that does bring up a question. I created a /boot partition to hold grub and selected that in the dropdown which looked like /dev/mapper/xxxxxxxGrendel4p6, being the fourth partition in my array (Extended) and the second logical, or sixth overall. I am assuming that is ok, but still didn't work for me.

---

### Post by ronparent on 2011-07-06
Just to clarify - grub is installed to /dev/mapper/xxxxxxxGrendel4p6. However if the dropdown you are refering to is the location for the bootloader that should be written to, for instance,  /dev/mapper/xxxxxxxGrendel4. The boot loader should not be written to any partition except for special circumstances.

You should be able to fix any time using this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

In your case you would use a live cd session to mount /dev/mapper/xxxxxxxGrendel4p6 and in the second step install grub to /mnt/ and the boot loader to /dev/mapper/xxxxxxxGrendel4. Unless you are unlucky and have to use one of the other grub reinstall methods what I suggested should work like a charm every time. Good luck.

---

### Post by grendel905 on 2011-07-06
Thanks ronparent. I was a little confused about that. I wasn't sure if it was asking me where I wanted grub to be located or which disk was the boot disk. I guess I should have select the boot disk instead of the /boot partition. I will give it a try tonight.

---

