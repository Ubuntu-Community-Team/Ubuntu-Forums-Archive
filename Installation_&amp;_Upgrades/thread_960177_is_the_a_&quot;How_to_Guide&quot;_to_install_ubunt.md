---
title: "is the a &quot;How to Guide&quot; to install ubuntu with a separate /home partition"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by PhilOHara on 2008-10-27
Hi,
Does anyone know where I can find a guide to install the following setup. 
I am currently running XP 64 bit, and want to create a dual boot system using the downloaded ubuntu 8.04 live cd. I also want to install 8.04 with a partitioned EXT3 /home partition, so I end up with a Windows XP 64 bit partion, a EXT3 /home partition, and a unbuntu ext3 partition?
regards Phil

---

### Post by Pumalite on 2008-10-27
Defrag XP several times. Turn PageFile to '0' (later to normal) Get Gparted Live CD and 'shrick' your XP partition. In the new space make 3 'New' partitions:
10 GB fo '/'
The rest minus your RAM for /home
Your RAM for /swap.
Install, go 'Manual' and use the already prepared partitions.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by francisc1701 on 2008-10-27
What do you need a guide for? It's so easy a 3-year-old could do it :)
To answer your question: yes, there are probably several. [This one]("http://www.herman.linuxmaniac.net/p24.html") should to, though.

good luck

---

### Post by PhilOHara on 2008-10-27
thaknyou will try that.....cheers Phil

---

### Post by PhilOHara on 2008-10-27
> **francisc1701 said:**
> What do you need a guide for? It's so easy a 3-year-old could do it :)
To answer your question: yes, there are probably several. [This one]("http://www.herman.linuxmaniac.net/p24.html") should to, though.

good luck
Thanks but I dont think the example in that link has the partitioned /home directory I was looking for

---

### Post by Elfy on 2008-10-27
Pumalite pinted you in the right direction - choose manual - where he said > The rest minus your RAM for /swap he meant /home - so if you now have 3 partitions formatted 2 as ext3 one as swap it is quite simple. Forget about the swap now as long as it's formatted - it will be dealt with by the installer.

So in manual - pick the partition you made for / - edit partition - pick ext3 in the use as box and / in the mountpoint, close that window. Pick the larger ext3 partition - use as ext3 and mountpoint is /home, close window - the partitions screen should now show

ext3 / 10Gb
ext3 /home larger partition

---

### Post by PhilOHara on 2008-10-27
> **forestpixie said:**
> Pumalite pinted you in the right direction - choose manual - where he said  he meant /home - so if you now have 3 partitions formatted 2 as ext3 one as swap it is quite simple. Forget about the swap now as long as it's formatted - it will be dealt with by the installer.

So in manual - pick the partition you made for / - edit partition - pick ext3 in the use as box and / in the mountpoint, close that window. Pick the larger ext3 partition - use as ext3 and mountpoint is /home, close window - the partitions screen should now show

ext3 / 10Gb
ext3 /home larger partition
thankyou forestpixie all becoming clearer....Phil

---

### Post by PhilOHara on 2008-10-27
> **Pumalite said:**
> Defrag XP several times. Turn PageFile to '0' (later to normal) Get Gpatrted Live CD and 'shrik' your XP partition. In the new space make 3 'New' partitions:
10 GB fo '/'
The rest minus your RAM for /home
Your RAM for /swap.
Install, go 'Manual' and use the already prepared partitions.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Hi Permalite
One Q in regards to the page file....I set to initial and max to 0 then reboot with gparted live CD do partitioning then reboot windows again and reset page file settings to what they were? Is that correct?....vheers Phil

---

### Post by Pumalite on 2008-10-27
You can wait to install or you can do it right after partitioning.

---

