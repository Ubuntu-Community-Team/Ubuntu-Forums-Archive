---
title: "hangs at configuring language-base-en-base"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by ArtDeco on 2007-07-11
Trying to install xunbuntu 7 on an older Dell laptop w/only 128mb ram, 10 gig disk as a dual boot win2k / ubuntu system. On my third try so far - first with a CD packed with Ubuntu linux bible that hung at a solid white screen, second with an ISO downloaded from MadTux that wouldn't boot, this time with the new internet based installer (wubly ?) that doesn't require partioning the hard disk (very cool if it works) . 

Afer rebooting into ubuntu, the Installer seems to hang at configuring language-pack-en-base. Status bar shows 1% for several hours so far. No sure if I should let it go all day or if it's really hung up.

I googled 'language-pack-en-base' and found several references in the forums but I don't know enough to tell if they were ever resolved and if so how ?

Any help appreciated.

---

### Post by bapoumba on 2007-07-11
May be you'll have more luck with the alternate CD:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/")

---

### Post by ArtDeco on 2007-07-11
Thanks. I will do that. Actually, I thought I _was_ using the alternate cd install just by picking Xubuntu rather than full Ubuntu. I wonder if I will have to uninstall wubi and download another ISO for the alternate install or if there is some way to access it from the command line. I rebooted into Win2K and found the log files from the wubi install. Actually pretty interesting to be able to look at linix grub files in a windows editor- ok I am a geek - but the drive is nearly full now - the files wubi left are huge.
Maybe that's why it hung?

---

### Post by bapoumba on 2007-07-11
If you are running out of space, yes, that's possible.
I do not know Wubi. Please check the [Wubi sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=234") in the Third party area.

Edit: how much space did you set up for xubuntu ?

---

### Post by ArtDeco on 2007-07-12
It actually just took whatever space was available without asking me - in this case 4.4 gig mostly in reserved (empty) files with names like swap and system. Maybe It will give some of that back once the install completes. But maybe not...

---

### Post by ArtDeco on 2007-07-12
I am installing more memory and am searching for the documentation for the alternate cd install but I can't find it - got this message:
The requested URL /ubuntu/dists/edgy/main/installer-i386/current/doc/ was not found on this server.
Any body know where the manual went?

---

### Post by ArtDeco on 2007-07-14
Installation of Xunbuntu via Wubi on ancient Dell laptop is complete in three easy steps :)

1)Ran uninstall of Wubi which deleted old files and  backed up  the good ISO.
2)I put an additional memory stick of  256mb of ram in the Dell 4000 for a total of 320mb. 
3)Ran the  Wubi install again. I asked me a couple questions,  found the ISO, and chugged away for about an hour .

I now have a dual boot Win2K and Xunbuntu laptop without ever partioning the disk. Amazing what a $70 ram stick can do.

This thread can be closed.:)

---

