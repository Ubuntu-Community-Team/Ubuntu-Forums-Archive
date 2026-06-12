---
title: "Dual boot two drives"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by mbrocketry on 2008-11-19
Ok here is the situation, I have two hard drives that I want to dual boot on. The first drive is a 250 gig drive split in half windows XP on the first partition. The second partition and all of the second 250 gig drive will be available for ubuntu. I had Fedora 9 installed on the second partition of the first drive and using all of the second drive. Well Fedora keeps updating everything since Fedora 10 is about to come out. All these updates keep breaking several of my apps. I saw that unbuntu 8.1 came out and I wanted to give it a try since unbuntu seems a bit more stable as far as updates.

Now the problem, I cleared the fedora partitions with gparted and loaded up the ubuntu cd (64bit). I came to the partitioner and there where several options all the guided  and manual. The issue is that the guided setup will not allow me to use all the free space (second partition on the first drive and all the second partition). It either wants to use the free space behind the windows install on the first partition and nothing else or the second partition only or the entire first of second drive. Then I course there is manual install but I can't find any real good info on that either.

Fedora never has an issue with using all free space whether it is a single drive or multiple drives with mixed partitions.

Has anyone run into this before and if so how did you get around it?

---

### Post by Mr_JMM on 2008-11-20
Sorry about the probs you had with Fedora, I never had those (still prefer Ubunutu though).

This may not exactly answer your query but it's my advice...

What's your ideal?
If you still use windows a lot:

Reformat the remainder of the 1st drive (with windows on it) as FAT32 and treat it as a shared documents drive.
Install Ubuntu completely on the 2nd harddrive, set BIOS to install from the Ubuntu drive.

If you're moving away from Windows (*big grins*):
Shrink that Windows partition down as much as you're comfortable with.
Create a 3 new partitions on the remainder (no more than 4 primary otherwise use an extended) for swap, root and home.
Reformat the 2nd drive as one big fat ext3 and use as a backup or master docs drive or even a "what Distro shall I play with next" drive.

---

### Post by Pumalite on 2008-11-20
And read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by mbrocketry on 2008-11-20
> **Mr_JMM said:**
> Sorry about the probs you had with Fedora, I never had those (still prefer Ubunutu though).

This may not exactly answer your query but it's my advice...

What's your ideal?
If you still use windows a lot:

Reformat the remainder of the 1st drive (with windows on it) as FAT32 and treat it as a shared documents drive.
Install Ubuntu completely on the 2nd harddrive, set BIOS to install from the Ubuntu drive.

If you're moving away from Windows (*big grins*):
Shrink that Windows partition down as much as you're comfortable with.
Create a 3 new partitions on the remainder (no more than 4 primary otherwise use an extended) for swap, root and home.
Reformat the 2nd drive as one big fat ext3 and use as a backup or master docs drive or even a "what Distro shall I play with next" drive.

Thanks Mr. JMM, I still like and use fedora, just my personal box I was having to recompile several programs about every other week and it was getting to be a pain. I know I don't have to use the latest updates but there a few programs that I am waiting for and they need the newer kernels. 

Anyway to answer your question the windows partition is only there for gaming. It is an NTFS partition and it set to 120 gig for a reason. I have 75 gigs worth of games COD4, Steam, Quake Wars etc. and I leave or need the last amount of space (about half) for windows swap and paging. I always leave half the drive open otherwise windows will start to slow down so I don't want to change the size at all. 

I currently have ubuntu on just the second 250 gig drive. I only want the other 115 gig because I do a Lot of video editing and storage so having 365 gig over 250 for me helps with more storage so that is why I want to have all the second partition on the first drive and the whole second drive dedicated to ubuntu. I don't want to have two or more different mount points, I just want one big partition.

I guess I don't understand why the ubuntu partitioner can't use all free space like fedora's partitioner does?

Here is a link to my modded gaming PC I am talking about: [http://mbppg.com/media/photoalbums/fly_n_high_pc_mod/index.html]("http://mbppg.com/media/photoalbums/fly_n_high_pc_mod/index.html")

---

### Post by mbrocketry on 2008-11-20
> **Pumalite said:**
> And read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Thanks Pumalite I had read all those before posting but my real issue is not dual booting. It is setting up the partitions to use half of one drive and the whole second drive. Sorry my title is very misleading. 

I can't seem to find and real info on how to manually setup partitions properly for ubuntu. I don't want to have /home and /storage etc. just to make this work I just want one big /.

---

### Post by caljohnsmith on 2008-11-20
Maybe either of these tutorials will help you:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)
[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Let me know if that is what you are looking for.

---

### Post by mbrocketry on 2008-11-20
Thanks CalJohnSmith, I will have to read up on that. 

I did try to do a manual install but I want to keep the install to one big drive. So when I tried to mount / on two separate drives it would give me an error. That is what I am fighting now.

---

### Post by caljohnsmith on 2008-11-20
> **mbrocketry said:**
> Thanks CalJohnSmith, I will have to read up on that. 

I did try to do a manual install but I want to keep the install to one big drive. So when I tried to mount / on two separate drives it would give me an error. That is what I am fighting now.
OK, I think I see what is causing the confusion; the root "/" mount point is for the main Ubuntu file system, so you can only mount that on one partition. If you want to use other partitions for storage, you don't need to set a mount point for them during the installation, you can just add them to your /etc/fstab afterwards so they are automatically mounted as simply partitions. Or you could put your /home directory on a separate partition and use that as storage by setting that partition with a mount point of "/home" during the installation. Is that maybe what you are looking for?

---

### Post by mbrocketry on 2008-11-20
Well actually I only really want the one root / mount point. I don't want a /home or /storage. I looking into being able to add the second partition on the first drive to the current /. Make sense?

---

