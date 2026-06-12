---
title: "mount/swap"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by tei727 on 2006-10-11
i would grately appreciate some assistance with my installation. i get stuck when it's time to pick a partition to "mount" on and one to "swap". can someone please explain this to me or point me somewhere that i can learn? thanks!!

---

### Post by tei727 on 2006-10-11
anyone [IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG]

---

### Post by John.Michael.Kane on 2006-10-11
How many partitions do you have?

Is ubuntu going to be the only OS on the machine?

Normal install use two partition setup.
/=root
swap

We need more info about how you want to set this up.

---

### Post by tei727 on 2006-10-11
> **SD-Plissken said:**
> How many partitions do you have?

Is ubuntu going to be the only OS on the machine?

Normal install use two partition setup.
/=root
swap

[highlight]We need more info about how you want to set this up.[/highlight]
oops, sorry bout that. i have XP on drive C and want to install ubuntu on a seperate partition. i have partition magic if need be. what's the best way and how do i manage that "swap" mount" selection?

---

### Post by John.Michael.Kane on 2006-10-11
During the install ubuntu should offer you the option to rsize your freespace which when done should give you one swap file,and one /=root partition.

Also during the install ubuntu should find your Windows partition,and ask if you want to add it to the grub menu.

---

### Post by tei727 on 2006-10-11
> **SD-Plissken said:**
> During the install ubuntu should offer you the option to rsize your freespace which when done should give you one swap file,and one /=root partition.

Also during the install ubuntu should find your Windows partition,and ask if you want to add it to the grub menu.

when it offers to resize the free space will it then create an additional partition? will it take care of the mount/swap issue i'm having by itself?

---

### Post by John.Michael.Kane on 2006-10-11
It should create two partitions after resizing
one being root/ <---make sure this is set bootable
the other being swap

You should then be able to install ubuntu to the newly made partition.

Futher into the install you should get a popup saying it has found another OS,and do you want it added to the grub menu.

I would backup any data on the windows partition just to be safe. 

For the most part you should be fine.

---

