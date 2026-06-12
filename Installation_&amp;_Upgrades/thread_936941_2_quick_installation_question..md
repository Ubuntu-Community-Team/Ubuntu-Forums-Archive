---
title: "2 quick installation question."
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by Douten on 2008-10-03
Hi! I'm new to Ubuntu and I have a few installation questions : )

1.) If I run liveCD will I have an option to pick to install on an external HDD? If I install it like that can I take that hdd and put it back inside the pc(so it becomes internal HDD) and Ubuntu will boot up fine?

2.) If I install it regularly into an internal HDD can I take that HDD out when it's done and put it into another pc will Ubuntu boot up fine?

I'm asking because my friend pc is a zombie and his cd drive doesn't work so I have to install Ubuntu on his HDD then put it back in. 

Thanks : )

---

### Post by Idefix82 on 2008-10-03
You can install it on an external hard drive but you need to make sure that the BIOS checks the USB devices first so that it boots from this HD and not from the internal one.

---

### Post by Douten on 2008-10-03
If I install it on an external HDD can I boot it up normally if I put that harddrive back into the pc like a regular internal harddrive? I'm only interested in installing Ubuntu in this HDD and then snap it back into the old pc that the cd drive doesn't work.

Thanks : )

---

### Post by Idefix82 on 2008-10-03
You should have no problems as long as that will be the only internal bootable hd.

---

### Post by iponeverything on 2008-10-03
you just have to do a simple step before you move it the other machine.

make sure that you install grub in the mbr of the drive that your moving
not the mbr of drive in your machine.

After its in the other machine reconfigure X if its needed.

sudo pkg-reconfigure xserver-xorg

---

### Post by Douten on 2008-10-03
How do I install grub in the mbr of my external drive? Is it automatically installed with Ubuntu?

Also another question. I've tried to format the hdd externally through gparted to ext3 and when it's finished and I unmount/remount it says I do not have permission to view folder, create folder, etc. How can I fix it?

---

