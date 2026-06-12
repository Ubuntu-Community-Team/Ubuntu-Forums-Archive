---
title: "More than four partitions on Vista Dell 80GB?"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Stoikheion on 2007-12-03
I recently bought an Inspiron 1520 with Vista Home Premium and the smaller 80GB hard drive option (which I slightly regret now). I've really been itching to try Ubuntu in a dual-boot situation, so, after backing up most of my important data I decided to try taking a look at the partitions. This is how they appear in Vista's Disk Management utility:

Volume: " ", File System: " ", Status: "Healthy (EISA Configuration)", Capacity: 110 MB, % Free: 100%

10.00 GB Unallocated Space (it used to be the D: RECOVERY partition, but I erased it since I already have a reintallation DVD anyway.)

Volume: "OS (C: )", File System: "NFTS", Status: "Healthy (System, Boot, Page File, Archive, Crash Dump, Primary Partition)", Capacity: 61.92 GB, % Free: 25%

Volume: " ", File System: " ", Status: "Healthy (Primary Partition)", Capacity: 2.50 GB, % Free: 100%

Whenever I try to create two partitions in the unallocated space (I'm kind of scared of letting Ubuntu's installer take over and to what it wants, because I don't want it to alter my C: partition at all), by the time I try to create the second partition, it basically tells me that there isn't enough room to do this operation. Am I not allowed to have more than four partitions with an 80 GB hard drive? If so, what are the two unnamed, supposedly 100% empty, partitions for? They came with my computer, and I'd be extremely hesitant to delete them unless I knew what they were. What can I do to make an Ubuntu installation as painless and risk-free as possible with these conditions? I really don't need much room for it; I plan on using and SD card or an iPod as a document/music sharing system between the two OS's. Any advice would be greatly appreciated, but unfortunately I know very little about Linux or hard drives.

---

### Post by bigken on 2007-12-03
you have to create an extended partition 1st then create your ubuntu partitions you can only have four primery partitions

---

### Post by Stoikheion on 2007-12-03
What do you mean, I have to create an extended partition? So, expand my C: partition into the the other one (or two), and then start making Ubuntu partitions? If so, what do the other blank ones do, and why are they there? I guess this is mostly a Windows question, but hopefully still valid nevertheless.

---

### Post by bigken on 2007-12-03
ok you have 3 partitions ubuntu needs 2 partitons this makes 5 in windows delete 
you free space and create an extended partition use this for ubuntu

---

### Post by Stoikheion on 2007-12-03
How would I delete my free space and make an extended partition for Ubuntu? I have no idea how to do this, and most of the other documentation and support assumes that I can just scrap random partitions and reinstall Windows. How, specifically, would I do any of this using GParted, Windows Disk Management, or the Ubuntu boot disc?

---

### Post by bigken on 2007-12-03
use the windows disc management I suppose you could also delete 2.5 gig partition then you could just with the normal primary partition

---

### Post by Stoikheion on 2007-12-03
Well, I just successfully installed Ubuntu (somehow) with manual partitioning on the 10 GB free space *without* a swap partition, keeping my hard drive happy with the number of partitions. Is that okay? I have 2GB of RAM, and most of my power hungry applications are in Windows.

---

### Post by bigken on 2007-12-03
yep thats great no need for swap if you have 2 gig of ram hope enjoy ubuntu :)

---

### Post by Torgas Prim on 2007-12-03
You will enjoy Ubuntu much more than Vista, I promise. Especially where your privacy is concerned.

Side note: I would have just went down to Best Buy and purchased another hard drive for 50$ and used it for my Ubuntu...personally.
Removes a lot of hassles. ;)

---

### Post by Stoikheion on 2007-12-03
Hmm... I had issues in the past with installing Ubuntu on an external hard drive. Something about not being able to mount it during installation, even though it could access all of the files normally. But I definitely agree with you, Torgas, someday I'll just get a bigger hard drive and start from scratch :)

Thanks for your help, bigken!

Now now all I have to do is figure out how to get all of my drivers without knowing how to use Ubuntu...

---

### Post by bigken on 2007-12-03
i would imagine the only driver to install is your graphics chip if its nvidia just go with the restricted drivers in system/administration

---

### Post by Stoikheion on 2007-12-03
The wireless card in my notebook doesn't seem to be working at all, however, and whenever I try to unmute the sound, it doesn't detect any devices. But is this the wrong place to ask how to do basic Ubuntu operations like that? I really have no idea what the command terminal or "sudo" are, let alone how to extract the correct drivers and use them so I can set up internet and 3d effects.

---

### Post by bigken on 2007-12-03
your best bet is do a search 1st on your laptop model you should find all your answers :)

---

### Post by Torgas Prim on 2007-12-04
No, not an external hard drive...one that you can swap into your laptop.
They come out with one screw on the 1520s.

---

