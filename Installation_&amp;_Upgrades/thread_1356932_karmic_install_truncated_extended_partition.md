---
title: "karmic install truncated extended partition"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by graemev on 2009-12-16
I've installed karmic on 3 other computers.

I just built a new machine. 1.5Tb sata drive. on that drive I created:

3 primary partitions of 20Gb (sda1-3)
1 extended partition (rest of drive) (sda4)

In the extended partition I created several secondary partitions and copied all my old systems data into it.


I installed karmic (boot from DVD) and used the manual partition setup to make sda1 mount as root (ext4)
and create a 8gb sawp in sda8 .

Once karmic is installed I see all the partitions I created but now the extended partition ends right at the point of my swap (sda8) ... so I can't use the rest of the disk ... I already have an extended partition  ... so I can't add one and the extended partition now appears full , because it's truncated to end of the last secondary partition (I've installed karmic on 3 other computers.

I just built a new machine. 1.5Tb sata drive. on that drive I created:

3 primary partitions of 20Gb (sda1-3)
1 extended partition (rest of drive) (sda4)

In the extended partition I created several secondary partitions and copied all my old systems data into it.


I installed karmic (boot from DVD) and used the manual partition setup to make sda1 mount as root (ext4)
and create a 8gb sawp in sda8 .

Once karmic is installed I see all the partitions I created but now the extended partition ends right at the point of my swap (sda8) ... so I can't use the rest of the disk ... I already have an extended partition  ... so I can't add one and the extended partition now appears full , because it's truncated to end of the last secondary partition (488649104 )... dooh why did it do this .... anybody know a way to re-extend the extended partition ... overwise I have a lot of copying to sort this out.
... dooh why did it do this .... anybody know a way to re-extend the extended partition ... otherwise I have a lot of copying to sort this out.


$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cda1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41945714    20972826   83  Linux
/dev/sda2        41945715    83891429    20972857+  83  Linux
/dev/sda3        83891430   125837144    20972857+  83  Linux
/dev/sda4       125837145   488649104   181405980    5  Extended
/dev/sda5       125837208   335549654   104856223+  83  Linux
/dev/sda6       335549718   367004924    15727603+  83  Linux
/dev/sda7       367004988   471861179    52428096   83  Linux
/dev/sda8       471861243   488649104     8393931   82  Linux swap / Solaris

---

### Post by darkod on 2009-12-16
I don't understand. sda5, 6, 7 and 8 are all following each other and are all within sda4, as it should be. What exactly is the problem?

---

### Post by graemev on 2009-12-16
well sda8 ends at   488649104 same as sda4 ... so sda8 is right at the end of the extended partition.

However the extended partition is no longer at the end of the disk  2930277168


   488649104   == approx 233Gb
  2930277168 == approx 1397 Gb

So most of my disk is now beyond the extended partition. Since I have 3 primary and 1 extended partitions I can't create any more primary and since the extended is now 'full' I can't create any secondary.
and aside from taking my word that the extended part used to occupy the remainder of the disk  ... note that sda8 ends at the same point as sda4 ... it would have been very slick indeed for me to arrange that ...no sda4 shrunk.

---

### Post by darkod on 2009-12-16
I figured that's what you meant, it's just difficult to follow the numbers like that. :oops:

From within ubuntu, if only sda8 (swap) is mounted, you could try this:
Open Gparted (install it if it's not in System-Administration).
Use swapoff to unmount swap
Unmount any other sda5-sda8 if mounted
That should remove the padlock (keys) symbol from them and sda4 as whole.
Expand sda4.
Not sure how you want to organize inside sda4 if the expand is successful, I'm leaving that to you. :)

---

### Post by graemev on 2009-12-16
Well I'll be  .... (a monkey's Uncle .... I case the English reference is obscure ... I'm impressed)

That did it:

Disk /dev/sda: 1500 GB, 1500299297280 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272065 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63    41945714    20972826   83  Linux
/dev/sda2        41945715    83891429    20964825   83  Linux
/dev/sda3        83891430   125837144    20964825   83  Linux
/dev/sda4       125837145  2930272064  1402209427    5  Extended
/dev/sda5       125837208   335549654   104848222   83  Linux
Warning: Partition 5 does not end on cylinder boundary.                   
/dev/sda6       335549718   367004924    15719602   83  Linux
Warning: Partition 6 does not end on cylinder boundary.                   
/dev/sda7       367004988   471861179    52420095   83  Linux
Warning: Partition 7 does not end on cylinder boundary.                   
/dev/sda8       471861243   488649104     8385930   82  Linux swap
Warning: Partition 8 does not end on cylinder boundary.  


(you'll note I've changed the version of fdisk... one of may desperate measures :-)

...just as well I didn't hack the fdisk tbale I was out by one of course (zero base not 1)

total 2930272065 sectors
dev/sda4       125837145  2930272064  1402209427    5  Extended

I guess gparted is just using a general rules about 'in use' partitions ... it would have been safe to edit this while running ...it's not a filesystem.

So once again many thanks. 

I guess I should do the decent thing and post this as a karmic installer bug ... lots of folks are going to be losing bits of their disk  ... might make drive manufactures happy I guess :-)

Any idea where I should raise the bug report?

---

### Post by darkod on 2009-12-17
The only place I know is [https://bugs.launchpad.net](https://bugs.launchpad.net). However, before reporting it I would go once again trough the install process and try to figure out what exactly you told the installer to do.
Not that I'm pointing a finger at you. :) But in some situations we just think we did it right and then we're surprised from the outcome and blame the poor computer which can only do as told. :)
Anyway, you're free to report it and maybe someone there will have an answer.

---

### Post by graemev on 2009-12-22
I think you have this rather "back to front" ...

I have have a fix, my system is working (thanks to your help)

My reporting it is not for my benefit but to help others.

I'm pretty sure about the sequence of events, since the swap partition got added there's pretty good proof that the partition was was shrunk AFTER I created the swap.

---

