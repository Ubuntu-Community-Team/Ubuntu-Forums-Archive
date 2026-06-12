---
title: "Installation Problem!!!"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by harakiri on 2006-11-06
I had only Breezy on my hdd and no other OS(**on a 15 GB partition**) for a long time and recently decided to upgrade to Dapper. I followed the instructions as given in the help site [ubuntu_help]("https://help.ubuntu.com/community/DapperUpgrades")
The upgrade failed due to a network disconnection/some error(not sure) and I couldnot even boot into my system. So I took the "easy" way out and installed Dapper from the CD(**split the 15 GB on to 10 and 5GB partitions). I installed ubuntu on the 5GB partition and left the 10GB unallocated space and other partitions intact.** Then it was wrking fine till I installed Windows XP. **(on the 10GB unallocated space)**. GRUB was overwritten and I tried the recover grub guide
> 
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
After this the initially wrking windows also dissapeared. I was back to square-one. Then I re-installed XP again**(on the same 10 GB partition as before)** and got it wrking.
Now coming to the real problem:
Initially in the first reinstall of ubuntu all partitions which already existed were being detected and mounted auto. But when I tried to re-re-install Ubuntu**(on the same 5GB partition)** after the re-install of XP, it refuses to identify any partitions during the setup partitions step. It shows my entire 80 GB as unallocated single partitions. I want ubuntu widout having to erase all the data and repartition the hdd and thus again reistall XP. Can anyone bail me out
Harakiri
p.s. Sorry for the extremely long mail(I didnot want to miss anything that wud help people help me)

---

### Post by _lynX on 2006-11-06
I'm not sure what to tell you to do at this point, because you didn't specify whether or not you installed XP over your entire HD, or if you reinstalled it into its old partition. If you only re-used the partition, Ubuntu should still be on its old partition, and you only need to fix your menu.lst file.

In order to do that, simply follow the steps that you quoted in your post, and then add thi code to /boot/grub/menu.lst after rebooting back into Ubuntu:

```

title         Windows
root          (hd0,0)
makeactive
chainloader   +1

```

You will need to edit the root part. If Windows is on the second partition on your harddrive, it would be (hd0,1).

Hope that helps!

---

### Post by harakiri on 2006-11-06
Thx, 
For the missing pieces of info:
I hav edited my previous post please look at it for further info. 
Harakiri

---

### Post by _lynX on 2006-11-06
Alright. You shouldn't need to reinstall Ubuntu from this point. You just have to fix GRUB by booting up using the live cd and running:

```

sudo grub
find /boot/grub/stage1
root (hd0,0) # If Ubuntu is on the first partition, it should be hd0,0. If Ubuntu is on the second partition, make sure it is hd0,1.
setup (hd0)
quit

```

Then, you just have to add Windows to menu.lst by placing this towards the bottom of /boot/grub/menu.lst:

```

title         Windows
root          (hd0,0)
makeactive
chainloader   +1

```

That should be all you need to do, unless I'm missing something. As for the  partition not being detected when trying to install issue, I don't know enough to address that. I hope someone else can help you out.

---

