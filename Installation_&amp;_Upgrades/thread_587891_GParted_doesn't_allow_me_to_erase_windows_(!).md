---
title: "GParted doesn't allow me to erase windows (?!)"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by gandalfito on 2007-10-23
Hello,

I was using both Windows XP and Ubuntu, but finally I decided to delete Windows FOR EVER (yes!!!). 
So I thought it would be very good to delete this NTFS partition and make instead an Ext3, where I was thinking to put my /home (now it is all in the same partition)

My problem is that in GParted, I cannot use any of the 'available' options. All the buttons appear on grey. I thought maybe unmounting windows partition would enable me to modify it, but I come this error

> The partition could not be unmounted from the following mountpoints:

/media/sda1

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

Since I am not an expert, I am not sure of how to do it manually.

Here I send the description of my hard drive

> /dev/sda1 --> Windows NTFS partition --> Mountpoint /media/sda1
/dev/sda2 --> Linux/ Ext3 --> Mountpoint /
/dev/sda3 --> Linux-Swap
/dev/sda4 --> Fat32 partition where I store my music, photos, .... --> Mountpoint /media/sda4

Any help is welcomed

Thank you very much in advance

---

### Post by sisco311 on 2007-10-23
you can unmount the partition manually from the terminal:
```
sudo umount /media/sda1
```

---

### Post by Juffo-Wup on 2007-10-23
Open up a terminal (Applications->Accessories->Terminal) and type:```
sudo umount /dev/sda1
``` to 'detach' the Windows partition from the rest of your filesystem. You should now be free to cleanse your hard drive of unholy NTFS partitions.

PS: I think you could also do it from Nautilus, going to the 'Computer' entry on the 'Places' menu, and from them 'expelling' (I don't know what is the word in the English version of that menu) the partition like you would with a flash drive or a CD.

---

### Post by gandalfito on 2007-10-23
Thank you, unmounting it manually was enough to re-partiotionate

And now, direct to full enjoy Ubuntu

than U !!!!

---

