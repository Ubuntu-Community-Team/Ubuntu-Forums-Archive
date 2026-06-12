---
title: "Lost my home partition after reinstalling Ubuntu in the systempartition"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by gopada on 2012-03-26
Hi -- I am bit new to linux/ubuntu so bear with me :-)

I thought I did a smart initially - having a clean hp box to install Oneiric on. So I proceeded to make 2 partitions with ext 4 formatting plus a swap. One was of course the system part. containing Ubuntu 12 GB and  the other would function as my HOME drive with all the files etc. 

However - as I wasn't able to run:  sudo apt-get dist-upgrade 
to get a newer kernel - and solve a hanging splash screen on shutdown
I went ahead an first reinstalled U on the first drive on top of the existing U and then the home drive was no where to be seen after the first boot.
At the time of installing i was asked to make a swap part. once again - that I did.

OK - since the problem with installing a new kernel persisted I went radical and reinstalled U completely on the first drive. The new home drive is on the firste drive now. 

What does this mean ? Do I have to mount the old HOME drive - the partition is still there I believe:
  	 	 	 	 	 	  Disk /dev/sda: 80.0 GB, 80026361856 bytes
 255 hoveder, 63 sektorer/spor, 9729 cylindre, i alt 156301488 sektorer
 Enheder = sektorer af 1 * 512 = 512 byte
 Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte
 I/O-størrelse (minimum/optimal): 512 byte / 512 byte
 Diskidentifikation: 0x0008195c
 

     Enhed Opstart   Start         ****     Blokke   Id  System
 /dev/sda1   *        2048    23437311    11717632   83  Linux
 /dev/sda2        23439358   156301311    66430977    5  Udvidet
 /dev/sda5        23439360   144531455    60546048   83  Linux
 /dev/sda6       144533504   156301311     5883904   82  Linux swap / Solaris
 

 Disk /dev/mapper/cryptswap1: 6025 MB, 6025117696 byte
 255 hoveder, 63 sektorer/spor, 732 cylindre, i alt 11767808 sektorer
 Enheder = sektorer af 1 * 512 = 512 byte
 Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte
 I/O-størrelse (minimum/optimal): 512 byte / 512 byte
 Diskidentifikation: 0x92172845
 

 Disk /dev/mapper/cryptswap1 indeholder ikke en gyldig partitionstabel
 

 Disk /dev/sdb: 8382 MB, 8382316544 byte
 64 hoveder, 32 sektorer/spor, 7994 cylindre, i alt 16371712 sektorer
 Enheder = sektorer af 1 * 512 = 512 byte
 Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte
 I/O-størrelse (minimum/optimal): 512 byte / 512 byte
 Diskidentifikation: 0x69737369
 

 Dette ligner ikke en partitionstabel.
 Du har nok valgt den forkerte enhed.
 

     Enhed Opstart   Start         ****     Blokke   Id  System
 /dev/sdb1   ?  1869771365  2038460886    84344761   69  Ukendt
 /dev/sdb2   ?  1701519481  3571400945   934940732+  73  Ukendt
 /dev/sdb3   ?        2573        2573           0   74  Ukendt
 /dev/sdb4      2885681152  2885733566       26207+   0  Tom
 


But U cannot see it. So how do I make the new installation be able to read it??
Sorry about the language.          :confused:

---

### Post by oldfred on 2012-03-26
When you have a separate /home partition, you have to include it in the install. You tell it to use the partition as /home but DO NOT format it.

If you do not want to reinstall, you should only need to edit fstab with the /home entry. 

You only need to see the last couple of commands on mounting /home and the examples of fstab entries for your /home from the normal moving /home to a new partition.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by darkod on 2012-03-26
During the latest install, did you tell it to use the existing /home partition or not? It can't assume what you want to use, so when you have a separate /home partition you need to use the manual install method and select to use that partition as /home WITHOUT formatting it.

---

### Post by gopada on 2012-03-27
Thanks both.

[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") I made a new install on the systempartition - this time I remembered to point to the old /home partition without formatting it. The only little twist was to remember which type of formatting I used when I did the very first installation - I believe that this could have caused some trouble in case I had made the wrong choice.

After that all was easy - I could find the old /home with all my files EUREKA!!!!
and the new kernel : sudo atp-get dist-upgrade
went well. So all in all it worked very well. 
Thanks again.

Thanks for the boot info script - I will definitely try this out as well as the other commands like rsync. I am just getting my feet wet.

:-)

---

### Post by gopada on 2012-03-27
:-)

---

