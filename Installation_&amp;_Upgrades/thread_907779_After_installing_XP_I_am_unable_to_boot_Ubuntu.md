---
title: "After installing XP I am unable to boot Ubuntu"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by jonio298 on 2008-09-01
Ok, so I installed ubuntu a while ago accidentally formatting my hard drive without realizing it. (I had windows XP installed. It wasn't a problem really, all my music was stored on my ipod) I loved ubuntu but decided I would like to have windows xp installed too. 

So I found my windows XP install cd, put it in and booted it from restarting my computer. It wouldn't let me install it in my largest partitioned drive (I'm guessing because ubuntu was already on there?) even though there was plenty of room. I noticed there was another drive that was already partitioned. This could be because this is actually my brothers computer and he might have partitioned that drive a while ago. The drive is only 5.78 GB and I don't know why I installed it on that one. I didn't really understand how to partition drives or anything.

I installed windows and it works great minus the fact that it's really slow and for some reason it's not detecting my video card. So I restart my computer hoping to be able to boot Ubuntu but I was wrong. In fact, I couldn't even find my other partitioned drive (Drive E:\)!!! I was really worried at this point.

I did some research and downloaded Ext2IFS_1_11.exe. I am now able to access drive E:\ (Phew!) but I still can't boot ubuntu. 

Thanks for reading, what do I do to be able to boot both windows and ubuntu. Also, I think I would like windows on a larger portion of my hard drive. 5 GB just isn't cutting it.

---

### Post by Partyboi2 on 2008-09-01
If you installed windows after you had installed ubuntu, windows would have written back to the mbr, so to fix this you can follow these steps [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub using the ubuntu live cd.

---

