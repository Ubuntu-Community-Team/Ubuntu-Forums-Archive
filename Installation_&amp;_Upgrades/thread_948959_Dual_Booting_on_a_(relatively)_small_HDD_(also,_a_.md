---
title: "Dual Booting on a (relatively) small HDD (also, a side question)"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by kcirbmab on 2008-10-15
Hi, I'm planning on dual booting Ubuntu with Vista on a 60gb HDD. I have 31GB free out of a total of 51GB on NTFS.

How compatible is Ubuntu with NTFS? I'm trying to decide between making a 5-10GB Ubuntu partition and using my other partition to store everything else or just splitting it down the line 25gb/25gb.

How difficult would it be to resize my partitions at a later time? (ie - changing from 10gb/40gb to 25gb/25gb assuming I have enough space)

Thanks


side question: I remember seeing a site listing the features of the Thinkpad x-series tablet and how compatible they are with Ubuntu. Does anyone know what I'm referring to? I can't seem to find it.

---

### Post by Partyboi2 on 2008-10-15
Ubuntu can read/write to ntfs, , so you will be able to read/write to your vista partition while using ubuntu. Before you make the partitions for ubuntu you will need to shrink down the vista partiton with the vista resize tool.
It is possible to increase or decrease partition sizes later down the track if you decided too.

---

### Post by kcirbmab on 2008-10-15
> **Partyboi2 said:**
> you will need to shrink down the vista partiton with the vista resize tool.

I just finished defragging and I can only shrink my partition from 51gb to 47gb. Any Ideas?

---

### Post by Partyboi2 on 2008-10-15
If you are unable to shrink down your vista partition to provide enough space for ubuntu you could install ubuntu inside vista using [[COLOR=Blue]wubi installer[/COLOR]]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by kcirbmab on 2008-10-15
Thanks, trying it right now.

---

### Post by kcirbmab on 2008-10-16
I hit a snag. My trackpoint's speed isn't affected by the preferences > mouse menu and it's current speed is driving me nuts.

I read that you need to do the following in the terminal:

# echo -n 120 > /sys/devices/platform/i8042/serio0/serio2/speed 
# echo -n 250 > /sys/devices/platform/i8042/serio0/serio2/sensitivity

But the problem is that the serio2 folder doesn't exist for me. Does anyone have any ideas? It's an x60 tablet if that helps at all.

---

