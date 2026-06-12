---
title: "Ubuntu Dual Booting help"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by s13vin4t0r on 2008-07-18
Hey guys. Im new here and new to Ubuntu so go easy on me. :D

Heres my deal:
what i want to do is Dual boot my laptop. I have my Computer tells me that I have 3 partitions already (Local Disk (C:), OS_TOOLS (E:), and HP_RECOVERY (F:)). I also have another partition that I made, which i was going to use to install OS X but i never got it to work. (it is 'Leopard' (G:)).

I want to install Ubuntu on G: and dual boot with Windows Vista. I have EasyBCD installed, and I would like to use that.

Im not a total noob, and im pretty good with computers, but I would still like to know the easiest way to install.

Thanks! :)

---

### Post by tC_Crazy on 2008-07-18
I think the live CD still includes Gparted, the partition editor. You also will need a linux swap partition... so I suggest you go into partition editor, delete G, create an extended partition (essentially a "folder" for logical drives). Inside the extended partition, make an ext3 partition for Ubuntu and a swap partition. Search around and you'll find recommendations for size of swap, etc. It's a good idea to get to know how your hard disk is laid out.

---

### Post by s13vin4t0r on 2008-07-18
So....

you say boot the LiveCD, delete G: and make a new partition out of that empty space?

---

