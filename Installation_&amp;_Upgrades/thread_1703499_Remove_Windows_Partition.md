---
title: "Remove Windows Partition"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by seanksg on 2011-03-09
Hi all,

I have recently decided to switch to linux as my primary OS.  I currently have Windows XP installed on the larger partition on my machine.  Is there a way that I can delete the XP partition, or at least re-allocate the majority of my space over to the Ubuntu side without reinstalling? 

Thanks.

-Sean

---

### Post by mörgæs on 2011-03-09
Yes, using Gparted you just delete the Windoze partition, and after that you can increase the Ubuntu partition to use the free space. 

I have never had problems with Gparted, but still it is a good idea to back up your most important files.

---

### Post by seanksg on 2011-03-09
Thanks for the help!

---

### Post by seanksg on 2011-03-09
Sorry, thought that would have done it.  But I'm having trouble resizing the Ubuntu partition.  I'm running from the live CD right now in order to be able to edit it, but it won't let me allocate more space to the Ubuntu partition than it already has (about 30Gb).  Any ideas?

Thanks.

-Sean

---

### Post by seanksg on 2011-03-09
I tried copying the partition to the unallocated space, but now I can't delete the original.  It gives me the error "Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5.

Currently, my partitions are as follows:
copy of /dev/sda5   ext4              26.84 GiB
unallocated         unallocated       178.01 GiB
/dev/sda2           extended          28.04 GiB
/dev/sda5           ext4              26.84 GiB
/dev/sda6           linux-swap        1.20 GiB

*Note that sda5 and sda6 are both subsidiary to sda2 (according to GParted)

I tried using the unmount command from the terminal on sda2, sda5, and sda6, but each time I got the message "umount: /dev/sdaX: not mounted"

The command I used was: "sudo umount /dev/sdaX" where x was either 2, 5, or 6.

Thanks for any help in advance.

-Sean

---

### Post by seanksg on 2011-03-09
Sorry again, just realized that the "not mounted" message I got meant that the disk had been unmounted.  Thanks for all the help.

-Sean

---

### Post by Hedgehog1 on 2011-03-10
```
[COLOR="Red"]copy of /dev/sda5   ext4              26.84 GiB
unallocated         unallocated       178.01 GiB[/COLOR]
/dev/sda2           extended          28.04 GiB
/dev/sda5           ext4              26.84 GiB
/dev/sda6           linux-swap        1.20 GiB

```

Sean,

Please don't copy partitions.  What you want is to end up like this:

```
/dev/sda2           extended          230.04 GiB
/dev/sda5           ext4              228.84 GiB
/dev/sda6           linux-swap        1.20 GiB

```

To do this, boot off of the LiveCD, select try and run gparted.

1) Delete the copied partition.
2) Highlight the 'swap' partition, right click and select 'swapoff' if it is showing.
3) Then, move/extend **sda2** from the to fill all the disk space at the begining of the disk.
4) Then, move/extend **sda5** to fill the space in **sda2**
5) Highlight the 'swap' partition, right click and select 'swapon' if it is showing.

Your done.

---

### Post by seanksg on 2011-03-13
Thanks for the help hedgehog!

---

