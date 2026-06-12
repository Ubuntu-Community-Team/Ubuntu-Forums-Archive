---
title: "Going to GRUB 2?"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coldReactive on 2009-09-03
Well I just wanted to know how we will upgrade to GRUB 2.

It says that they cannot upgrade your existing GRUB as it could be dangerous, blabla. So what do we do? Just reinstall 9.10 freshly and it'll remove the old grub and install the new grub? Or do we have to wipe the whole drive using something like DBAN and then installing 9.10 freshly?

---

### Post by Slug71 on 2009-09-03
Doing a fresh install will give you Grub 2. You can upgrade to it too. Its just not recommended to chainload into it.

---

### Post by coldReactive on 2009-09-03
> **Slug71 said:**
> Doing a fresh install will give you Grub 2. You can upgrade to it too. Its just not recommended to chainload into it.

Thanks, I guess. Because the Alpha4 page didn't explain it all too well if you ask me. I'll post a reply to this if that doesn't happen.

---

### Post by philinux on 2009-09-03
> **Slug71 said:**
> Doing a fresh install will give you Grub 2. You can upgrade to it too. Its just not recommended to chainload into it.

Can you explain.

I've got jaunty on disk 1 and karmic on disk 2 with grub 2. I chainload to karmic from the grub legacy on the mbr of disk 1. Grub 2 is installed to the first partition of disk 2 although it did complain.

End bit of menu.lst.
title        SDB Karmic

root (hd1,0)
chainloader +1

---

### Post by drs305 on 2009-09-03
> **coldReactive said:**
> Well I just wanted to know how we will upgrade to GRUB 2.

It says that they cannot upgrade your existing GRUB as it could be dangerous, blabla. So what do we do? 

See this thread that explains conversion to Grub 2 from Grub Legacy (if you want to attempt it). Just remember the developers elected *not* to do this by default:
[Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing")

---

### Post by ranch hand on 2009-09-03
If you check to see what veesion of grub-common you are using I think that you will find that all the files that you need for grub2 are already on your box.  I am on 9.04 right now and all Iwould need to be upgraded to grub2 is install the grub2 (GRand Unified Bootloader, version 2 (dummy package)) and grub-pc.

I would also remove or rename any grub-legacy only files.  I would rename some of them, like the menu.lst file, so that it would not do anything but would be there if I want to use it in the future or just refer to it for some reason.

---

### Post by coldReactive on 2009-09-03
> **ranch hand said:**
> If you check to see what veesion of grub-common you are using I think that you will find that all the files that you need for grub2 are already on your box.  I am on 9.04 right now and all Iwould need to be upgraded to grub2 is install the grub2 (GRand Unified Bootloader, version 2 (dummy package)) and grub-pc.

I would also remove or rename any grub-legacy only files.  I would rename some of them, like the menu.lst file, so that it would not do anything but would be there if I want to use it in the future or just refer to it for some reason.

I would rather wait until 9.10 comes out actually. I don't want to mess up this installation anymore than I already have. ;)

---

### Post by ranch hand on 2009-09-03
You will note that I have four clean install variations on 9.10 and four upgrades from 9.04.

I am not using any one of them right now, this is the OS I use the most and I certainly have not screwed with it at all with Alpha experiments.  I want to keep using this one.

All my alpha stuff is on other drives from this one.  This one is turned off when I am playing with 9.10.  There have been a couple of times that I was very happy about that.

---

### Post by gavshouse on 2009-09-04
> **coldReactive said:**
> I would rather wait until 9.10 comes out actually. I don't want to mess up this installation anymore than I already have. ;)

i upgraded to grub2 and i made a youtube video about it, did it in vmware its got all the steps its in HD here [http://www.youtube.com/watch?v=4hlsK7q8uns&fmt=22](http://www.youtube.com/watch?v=4hlsK7q8uns&fmt=22)

its easy

---

### Post by coldReactive on 2009-09-04
> **gavshouse said:**
> i upgraded to grub2 and i made a youtube video about it, did it in vmware its got all the steps its in HD here [http://www.youtube.com/watch?v=4hlsK7q8uns&fmt=22](http://www.youtube.com/watch?v=4hlsK7q8uns&fmt=22)

its easy

I reinstall every time there's a new version of Ubuntu though, not really needed.

---

