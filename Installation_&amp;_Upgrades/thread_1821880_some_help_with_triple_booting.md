---
title: "some help with triple booting"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Matryx on 2011-08-09
I'm trying to setup a triple boot and I've followed many guides and keep running into the same problems. I've spent three days already reinstalling ubuntu and making new partitions but I can't seem to make that last partition for OPENELEC.

I want to triple boot Windows7, Ubuntu, and Openelec.

When I install Ubuntu I make the /boot, / , /home, and swap partitions and after Ubuntu is installed I download GParted and TRY to make another partition and get these messages. 

Also I've also tried to put the boot loader in /dev/sda5 and I keep getting grub rescue errors. Only if I leave it at the default (/dev/sda) does it work. 

[[IMG]http://i.imgur.com/Q5gtP.png[/IMG]]("http://imgur.com/Q5gtP")

[[IMG]http://i.imgur.com/92ilA.png[/IMG]]("http://imgur.com/92ilA")

---

### Post by garvinrick4 on 2011-08-09
take a screenshot of gparted screen and then hit the paperclip icon in upper of Message
box and upload it in the box that opens. That way we can see it, looks like to many primary partitions. Screenshot is under applications/accessories to screenshot.
Never mind I see it now.

---

### Post by Matryx on 2011-08-09
Should I be making all the partitions when I'm setting up the partitions during the install? For some reason after I install Ubuntu it doesn't let me make anymore logical partitions but before installing Ubuntu I could make as many partitions as I want. I guess I answer my own question but I'm still unsure where to put the device boot loader. I want to use GRUB but all the guides I've been reading is telling me to install it in the /boot partition. Only problem is I keep getting an error after the install and can't boot in anything.

---

### Post by garvinrick4 on 2011-08-09
#Delete all partitions sda4 and up and make the sda3 extended larger.
#Then make logical partitions inside the extended partition for your
/ and /home and swap if you are short on RAM. 
#The extended partition is just a house for the logical partitions which
Linux can survive in. Extended counts as a primary.
#Only allowed 4 primary sda1 thru sda4 which Windows likes to live in.
Do not make a /boot partition. Leave sda1 and sda2 alone.
#Put grub in sda not sda5 or sda1 but sda
#I would just make the rest of your drive extended so as to use whenever you
want as more logical partitions for more installs.

---

### Post by garvinrick4 on 2011-08-09
After you install and boot into Ubuntu you will have to open
a terminal.( ctrl/alt/t ) and type or copy and paste this in:
```
sudo update-grub
```
This will put Windows in your grub2 that Ubuntu uses as a menu entry
so you can boot either Ubuntu or Windows.

---

### Post by Matryx on 2011-08-09
ok thanks. I'll try it and see if it works

---

### Post by Matryx on 2011-08-10
how exactly do you create an extended partition? the sda3 in my screenshots were created when I made the /home and / partitions.

---

### Post by oldfred on 2011-08-10
You can use gparted. But if you still have your sda3 extended you cannot create another extended, only one allowed. So just extend sda3 to include all of the unallocated.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

