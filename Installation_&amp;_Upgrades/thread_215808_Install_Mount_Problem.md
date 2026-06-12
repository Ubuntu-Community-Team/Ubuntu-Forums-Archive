---
title: "Install Mount Problem"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by steven21 on 2006-07-14
Newbie here.

I have one 80 GB harddisk partitioned in two FAT 32 partitions named c: and d: (37 GB each). Windows XP is installed on c: and i want to install Ubuntu on d: 

Using partiton magic i have made an "ext3" partition on my D: drive of size 10 GB and i want to install linux specifically into this without touching other partitions as i want to save My win XP installation and data on both c: and d: I am trying to use the manual partition option while installing ubuntu but cant make head or tail of options that ubuntu throws at me. 

I am attaching screenshots (camera shots rather) of the situation .Can somebody tell what i need to fill in those blanks and wat excatly is mount and why does Ubuntu need so many partitions? It refuses to go into the single 10 GB partiton that i have created if i select the same Partition for Swap, root etc.

[http://img311.imageshack.us/img311/4905/pic0390dd.jpg](http://img311.imageshack.us/img311/4905/pic0390dd.jpg)
[http://img311.imageshack.us/img311/9655/pic0408bx.jpg](http://img311.imageshack.us/img311/9655/pic0408bx.jpg)

(The screenshot shows partion size as 7 GB but i have now increased it to 10 GB)

Please dont guide me to psychocats.net as i have read that tut. & it finishes where my Problem starts.

---

### Post by Sonofmoog on 2006-07-14
You're almost there.  You'll need to create one more partition for swap, and it should be 2 x RAM.  

Media/hda1 is /dev/hda1 - Your windows partition
Your root partition (line 2 is fine)

Just create another partition, format it as swap, and change line 3 to point to it .. 

HTH

---

### Post by steven21 on 2006-07-16
Ok so iam here now 
[http://img272.imageshack.us/img272/9632/042ne2.jpg](http://img272.imageshack.us/img272/9632/042ne2.jpg)

and [http://img512.imageshack.us/img512/6196/044dg4.jpg](http://img512.imageshack.us/img512/6196/044dg4.jpg)

as far as i understand media/hda1 contains my win XP 
and media/hda5 contains files sitting on my second win partition (d: )

Now when i click next why does it warn me that it will destroy data on my removed partitons as well when i have specifically selected only the new partitions for reformat & installation of UBuntu?

see this [http://img512.imageshack.us/img512/1828/043ck8.jpg](http://img512.imageshack.us/img512/1828/043ck8.jpg)

If i go ahead will it leave my win xp and data on d: alone ?

---

