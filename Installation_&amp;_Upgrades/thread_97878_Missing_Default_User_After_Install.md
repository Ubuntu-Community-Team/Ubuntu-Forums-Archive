---
title: "Missing Default User After Install"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by MRCuadra on 2005-12-01
Okay, look out, complete Linux newbie here, so be nice... ;) 

I've seen other posts about this problem, and there doesn't seem to be a direct solution, so I'm posting to (*hopefully*) get a more direct answer.

First, I've got a P2 Dell (Dimension) with a 8GB drive ([FONT="Courier New"]C:[/FONT]) that has Win2KPro installed [NTFS partition], and a 13GB drive ([FONT="Courier New"]D:[/FONT]) that (was) unformatted.

After lots of research in the forums, I decided to install Ubuntu on the 13GB drive with the following partitions:

    5GB  /         [reiser(?) file sys]
    8GB  /home  [FAT32]
    (rest) swap

I chose [FONT="Courier New"]FAT32[/FONT] for [FONT="Courier New"]/home[/FONT] because I'd like to have access to it from Windows.

Now the problem comes when I get to setting-up the user account. I input my name, input my default user name, set and confirm my password, but then it goes right back to inputing my name again. :-s The only way out of this loop is to [FONT="Courier New"]<Go Back>[/FONT]. Then I have to finish the rest of the install manually.

I did this, and everything seemed to work out okay; but when I re-booted and started Ubuntu (to finish the install), it got so far then put me at a command prompt to login, not the Ubuntu screen, but like I was in DOS (*-sorry, did I mention I was a complete Linux newbie?*  :smile: )

So I try to login as the default user; says user doesn't exist. I try to login as root; that works but now what? Well, I'm adventurous and have gleened enough tidbits from the forums, so I try to [FONT="Courier New"]mkuser[/FONT] and that doesn't work... I go 'round and 'round and get nowhere. :confused: 

Back online for more research... *(to make this post not too much longer...)* I found one thread that showed the exact same problem, but the solution suggested was to not make a FAT32 partition. That person made an EXT3 partition instead and no longer had the "loop" or "missing user" problem.

Well, if that solves my problem, so be it, but now here's my question: Can I access an EXT3 partition from Windows? For that matter, is there another format option I should choose from to get the same result? *(not being familiar with any of the options except FAT and NTFS)*

Any insights to the install problem would be appreciated as well.

MRCuadra
A Space In Time
----
"Any sufficiently advanced technology is indistinguishable from magic."  — Arthur C. Clark

---

### Post by bwog on 2005-12-02
You can access ext3 from windows with explore2fs, a recent version is 1.07.

The fat32 problem is described here: [http://www.ubuntuforums.org/showthread.php?t=89992&highlight=login](http://www.ubuntuforums.org/showthread.php?t=89992&highlight=login)
The bug is that installation can be continued even when no login name can be implemented. This is already reported, and solved for Dapper.

When you use explore2fs you probably do not need a fat32 partition. However, in case you really want it you can leave some space unpartitioned during install and make a fat32 partition after installation.

---

### Post by MRCuadra on 2005-12-02
bwog:

> You can access ext3 from windows with explore2fs, a recent version is 1.07.

Thanks! That looks like something I'll use, specially since I have other machines on my lan running Windows.

> The fat32 problem is described here: [http://www.ubuntuforums.org/showthre...ighlight=login](http://www.ubuntuforums.org/showthre...ighlight=login)

Yeah, that was my main source of info. and why I asked about the other file systems (EXT2/3). I guess it's just a matter of asking the right question. :)

> However, in case you really want it you can leave some space unpartitioned during install and make a fat32 partition after installation.

I'll probably just go with the EXT3 so I can specify where to put /home, but if I did go that route, do you know if *fdisk* or Win2K would be able to recognize the free space as formattable? *(...is that a word?)* Alternatively, could I do it within Ubuntu (assuming I get it running)?

Thanks again for the response!

---

### Post by bwog on 2005-12-02
I suppose windows would recognize the free space and could format it in ntfs, however ubuntu has gparted which is really good . Gparted is on the live CD or can be installed via synaptic on your ubuntu installation.

When you use gparted as an installed app (not the live CD), it cannot change partitions that are mounted (this would present no problem with the free space ofcourse).

(I mentioned the fat32 link as a reference for others, your question was quite clear.) 

good luck.

---

### Post by MRCuadra on 2005-12-02
Alright, looks like I've got some options. I'll try to get setup and post any good results (...or bad, knock on wood...)

Thanks again!

---

### Post by Frymaster on 2005-12-16
I had the same problem - I eventually found I could create the fat32 during install as long as it WASN'T mounted as /home

---

### Post by thezerogroup on 2005-12-16
MRCuadra, 

I just tried explore2fs and it rocks! Thanks for the tip

---

