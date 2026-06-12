---
title: "Upgrading to larger hard drive"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by jefftuck on 2007-06-05
Hi, guys. I dual-boot Ubuntu Feisty and XP, but I'm running out of space on my hard drive. I'd like to buy a larger HDD and move both operating systems over, without doing a re-install of either. 

Does anyone have any advice on how to do this? It seems like if I use dd to just copy the drive, I could maybe get it going but it would have the same size partitions as it does now. 

Incidentally, this is actually a laptop. I can temporarily put the new HDD on a USB drive, or put both laptop HDD's in a desktop machine to do the actual copy, so that's not a problem. But, I can't just add a disk to this machine, I have to actually move everything from the existing disk to the new one.

Thanks for the help.

JT

---

### Post by coffeecat on 2007-06-06
I've done something similar, on more than one occasion. My preferred way is to use imaging software to get compressed images of each installation/partition, partition the new drive and then uncompress the images onto the appropriate partitions.

As far as Linux imaging software is concerned I often see requests on forums asking for advice on what to use and hardly anyone ever mentions the most readily available and efficient imaging app - tar. (man tar :wink: ).

But two potential pitfalls.

1 You have to re-install Grub to the mbr. Easy if you know how. A real show-stopper if you don't.

2 The quirky decision of the Ubuntu devs to use UUIDs in /etc/fstab. If you clone an Ubuntu installation and do not edit /etc/fstab there will be a major oops on bootup. Search these forums for 'UUID fstab' and I think you'll see what I mean.

You are a first-time poster but from your reference to dd you seem to be experienced, so I didn't know how much detail to add. But I've given you the basic principles of how I would proceed and I'll watch this thread to see if you post back.

**Edit:** I've just noticed that you intend to put the new HD into an USB case to do the copying. Good idea. Makes it a bit easier, and you could use Gparted to make whatever size partitions you want first. For the Linux partition(s), simply use cp to copy everything. Specifically 'cp -a' (man cp :wink: :lol: ). **Much** quicker than dd. But for Windows you'll need some sort of cloning software. I have Acronis. It works very well but it's commercial software - i.e. it costs. But you'll still have the grub and fstab issues to deal with.

---

### Post by reiki on 2007-06-06
look at partimage.
I used it here to do basically the same thing you're talking about. Image your current drive or image partitions separately. Restore them on the new drive. I think if you create teh new partitions on the new drive first and THEN restore them into those partitions, you won't have to resize. It's been a while since I used it, but I would definitely use partimage again. It even clones the UUID of the partitions.

---

