---
title: "Partition table"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by wabi on 2005-09-04
Salutes,

I have looked but I haven't found a topic on it.  :roll: 

Can anyone share with me what their partition table looks like for dual booting XP/ubuntu?

Thanks

---

### Post by odin on 2005-09-05
I cannot tell you because I only have ubuntu installed in my PC but I can tell you what you need if it helps.

I was about telling you what you should do but I'm thinking that it will be easier if you post how your hard drive is partioned so I can tell you what to do.

---

### Post by dohko_xar on 2005-09-05
Hi, im posting here because I think i destroyed my partition table. I installed Ubuntu on one of my partitions on my hdd. After finishing installing Ubuntu, i logged into it and use it for a while. I wished to return to windows, so i reboot the pc and gubu or guru, cant remember the name, came up. I choosed Windows XP and my screen of the Windows XP boot screen came up. After choosing the boot screen, a black screen with white letters came up telling me that it couldnt find a requiered .dll file found in windows dir/system32/. I quickly got my Partition Magic rescue disk, as partition magic for DOS boot up, it told me i had a Partition Table Error #114, and it couldnt display my partitions. Scared as hell, i ran to get my windows xp rescue disk and did "fixmbr" on my boot record. It cleaned my boot and guru got ereased. Now I still get the same problem and I cant get onto XP.

Please forgive my spelling and grammar  =/
If anyone can help me, thanks

---

### Post by cbudden on 2005-09-05
[QUOTE=dohko_xar]Hi, im posting here because I think i destroyed my partition table. I installed Ubuntu on one of my partitions on my hdd. After finishing installing Ubuntu, i logged into it and use it for a while. I wished to return to windows, so i reboot the pc and gubu or guru, cant remember the name, came up. I choosed Windows XP and my screen of the Windows XP boot screen came up. After choosing the boot screen, a black screen with white letters came up telling me that it couldnt find a requiered .dll file found in windows dir/system32/. I quickly got my Partition Magic rescue disk, as partition magic for DOS boot up, it told me i had a Partition Table Error #114, and it couldnt display my partitions. Scared as hell, i ran to get my windows xp rescue disk and did "fixmbr" on my boot record. It cleaned my boot and guru got ereased. Now I still get the same problem and I cant get onto XP.

Please forgive my spelling and grammar  =/
If anyone can help me, thanks[/QUOTE]
 Looks like you windows install is messed up.  The boot loader is called GRUB.  You should look in you windows drive when using ubuntu and see whats there.
If you cannot see how to access you windows partition, here is how to do it.
```
 sudo mkdir /media/windows 
```

This makes a folder to mount the drive into.

```
 sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 
```

This assumes that windows is on the first partition on the disk and it is formatted with NTFS

If you then go to look in the /media/windows/ folder, you should see the contents of the C: drive.

I got this from the unofficial ubuntu guide [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by wabi on 2005-09-05
Ok, I went through the installation. I have seen the partition table is suggested by setup

Thanks

---

