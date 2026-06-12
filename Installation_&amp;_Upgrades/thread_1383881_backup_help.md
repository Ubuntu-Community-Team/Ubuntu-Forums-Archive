---
title: "backup help?"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by dragonnutds on 2010-01-17
i need some help with backing up, i am trying to install Ubuntu with duel boot but i am worried about losing my data, i don't have any disks that came with my xp, so if i loss it in a corruption, i will not be able to get my windows back. so i have some questions, all these questions are focased on the windows xp defalt backup software. 

if i backup to my hard drive, will it be safe wile trying to partition my drive?

can a backup shrink in size so i can store it on a 4 gb flash drive? 

are there any free online backup storage sites?

if everything on a hard drive is lost, can a backup still boot?

i would really appreciate it if somone could respond as soon as possible.

---

### Post by Sef on 2010-01-18
>  if i backup to my hard drive, will it be safe wile trying to partition my drive?

As long as your hard drive is not connected to your computer.

>  can a backup shrink in size so i can store it on a 4 gb flash drive? 

Files that should not be a problem as long as they are under 4 gb.
>  are there any free online backup storage sites?

The ones that I have seen are limited to 2 gb for free.  Canonical (Ubuntu's sponsor) has a free 2 gb.

>  if everything on a hard drive is lost, can a backup still boot?

If you used a cloner, like [Clonezilla]("http://clonezilla.org"), you can reinstall the os.

---

### Post by dragonnutds on 2010-01-18
ok, thanks, not good with the resources i have. ok, is there anyway to transfer files from one computer to another with wireless lan, maybe i can store the clonzilla file on my laptop if it is safe to have operating system files in the computer

---

### Post by Sef on 2010-01-18
> ok, is there anyway to transfer files from one computer to another with wireless lan, 

If you have the computers set up to share, you could do it that way.  I have never done that, so I will let someone else handle how to.

---

### Post by QuimNuss on 2010-01-20
Are you worried about losing the data (photos, documents and alike) or afraid of losing Windows?

You don't have any external USB hdd to back up the data to (no even a friend's)? That would be the easiest way to go.

I'm not familiar with network folder sharing in Windows, I recall setting the workgroup accordingly in two computers sometimes worked, sometimes not. Are there any other computers on the network? Are they running ubuntu or other Operating Systems? 

Sharing folders between ubuntu machines is straight forward, if there's another Ubuntu machine on the network, you can use the LiveCD with yours to share from there.

Concerning the Ubuntu installation, if you have your hard-disk already partitioned (Many laptop ships have it partitioned by default) and your LiveCD *try ubuntu without making any changes* worked fine, it's unlikely that something happens to the Windows partition if you choose the other one for Ubuntu. That's another issue anyway, I recommend backing up the files as an habit.

---

### Post by Leppie on 2010-01-20
you could also use the dd command to create a backup of your xp partition:
```
sudo dd if=/source/partition of=/path/to/image
```or if you want it compressed:
```
sudo apt-get install gzip
sudo dd if=/source/partition | gzip > /path/to/image.gz
```
you can do this using the ubuntu livecd and writing the image to an external backup device (like a flash drive if it's big enoug).

---

