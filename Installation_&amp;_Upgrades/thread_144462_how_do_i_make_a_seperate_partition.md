---
title: "how do i make a seperate partition?"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by halvdansk on 2006-03-14
i would like to make **my own partition** because i dont like all the stuff that is generated in my home/ partition. how can i do that and how do i mount etc? step by step please :) 

i know you can make seperate partition for 
_var/ _
_home/ _
_etc/_ and so on

but i what my own.. :-k 
i.e _john's/_

thx

---

### Post by aysiu on 2006-03-14
Your first step would be resizing an existing partition.

You should do this with a live CD, as the resizing process requires that the partition being resized is unmounted.

If you have the Ubuntu Live CD, you can install (through Synaptic or apt-get) GParted and then use GParted from there to resize and create a new partition.

Applications > Accessories > Terminal ```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
```

Other options are QTParted with Knoppix or DiskDrake with PCLinuxOS. I prefer the latter, but if GParted works for you, there's no need to download an entire other .ISO.

Whatever partitioning program you use, make note of the new partition's location (for this example, let's just say it /dev/hda5).

Once the partition is created and formatted as Ext3, just boot up to Ubuntu again and ```
sudo mkdir /john
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Add this line in ```
/dev/hda5 /john ext3 defaults 0 0
``` Then save and exit ```
sudo mount -a
sudo chown -R john:john /john
sudo chmod -R 755 /john
```

---

### Post by StefanoCole on 2006-03-15
> If you have the Ubuntu Live CD, you can install (through Synaptic or apt-get) GParted 

If you have the Breezy live CD you don't need to install GParted since it is already available between the applications ;) 

Stefano

---

### Post by aysiu on 2006-03-15
[QUOTE=StefanoCole]If you have the Breezy live CD you don't need to install GParted since it is already available between the applications ;) 

Stefano[/QUOTE] How do you know this? Is there a list of packages available on the live CD? I seem to remember having to install GParted... maybe I was using the Hoary live...

---

