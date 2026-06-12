---
title: "What to do next?"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by steven21 on 2006-07-17
In my intsllation of Ubutu i have reached here
[http://img272.imageshack.us/img272/9632/042ne2.jpg](http://img272.imageshack.us/img272/9632/042ne2.jpg)

and [http://img512.imageshack.us/img512/6196/044dg4.jpg](http://img512.imageshack.us/img512/6196/044dg4.jpg)

as far as i understand media/hda1 contains my win XP
and media/hda5 contains files sitting on my second win partition (d: )

Now when i click next why does it warn me that it will destroy data on my removed partitons as well when i have specifically selected only the new partitions for reformat & installation of UBuntu?

see this [http://img512.imageshack.us/img512/1828/043ck8.jpg](http://img512.imageshack.us/img512/1828/043ck8.jpg)

If i go ahead will it leave my win xp and data on d: alone ?

Can somebody advise me if wat i am doing is correct and i can go ahead and install ubuntu without damaging my win xp or other data?

---

### Post by cotcot on 2006-07-17
You will keep your windows partitions. The only partition that will be reformatted is the swap, that is normal. The installer does that by default. Obviously you have created the root partition before with the correct mount (/).
The warning about losing data applies to the partitions mentioned below this text which is the swap.

Maybe, optionally, consider to have a separate /home. For instance 5 GB for / and 4 GB for /home. Google on "separate home partition" for more info. You can make one later also.

---

### Post by steven21 on 2006-07-17
Ok thanks, cotcot

Ubuntu is up and running, all data intact

---

