---
title: "&quot;This computer has no operating system on it&quot;"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by leucippus on 2010-08-26
Hey guys...I installed Fedora 13 and everything went fine, and so I decided to dual boot Ubuntu 10.4/Fedora 13. 

  Problem is, when I get to the part where I partition with Ubuntu, the only option is "use entire drive" because Ubuntu doesn't "see" the Fedora install.

  Any ideas? Thanks  :D

---

### Post by M93 on 2010-08-26
u can use the make a new partion option

---

### Post by M93 on 2010-08-26
u can use the make a new partition option

---

### Post by leucippus on 2010-08-26
I heard you the 1st time...lol

 Yeah, I think learning manual partitioning would solve my problem. 

 Another user shared several links to learning partitioning for beginners. I tried booting to gparted, but the damn mouse and keyboard kept freezing up on me, and couldn't get any practice in. :p

---

### Post by leucippus on 2010-08-27
Well, after doing some more research, I've learned the problem is with something called "Grub"

 Apparently, Ubuntu uses "Grub2" by default, and Fedora uses "Grub legacy", and they don't play well together.

 Someone suggested using a "chainloader", :shock: so it looks like it may be awhile before I'm dual-booting Ubuntu/Fedora. :rolleyes:

---

### Post by coffeecat on 2010-08-27
Grub has nothing  to do with this problem. The fact that Fedora uses legacy grub and Ubuntu uses grub 2 is irrelevant. It sounds as though the problem is the installer not being able to make out the partition layout on your hard drive. When left to its own devices, Fedora will make a LVM partition - or at least it used to. This is almost (completely?) impossible to resize. I wouldn't be surprised if Fedora has used almost your entire hard drive for one LVM partition with just a couple of small ones for boot and swap. That is perhaps why Ubuntu can only install by using the whole hard drive. It has to replace Fedora or do nothing at all.

That's why I always set up my partitions before attempting to install Fedora. I have Fedora 13, Ubuntu and Vista on one of my laptops and the mix of grubs is no problem.

If you want to investigate this further, boot up with the live Ubuntu CD but don't start the installer. Open a terminal and post the output of...

```
sudo fdisk -l
```

---

### Post by leucippus on 2010-08-27
> **coffeecat said:**
> Grub has nothing  to do with this problem. 
If you want to investigate this further, boot up with the live Ubuntu CD but don't start the installer. Open a terminal and post the output of...

```
sudo fdisk -l
```

 Cool...definitely appreciate your time and help! Here's a screenie of my terminal.

---

### Post by coffeecat on 2010-08-27
Yes, you have a LVM partition, but that isn't the reason why the Ubuntu installer couldn't resize existing partitions. You've used up the complement of 4 primaries. You cannot create new partitions without removing at least one first.

A quick run-down on your partition layout:

sda1 = primary = approx 98GiB. This is an ext2/3/4 partition. Do you have a separate /home? I cannot think what else it might be.

sda2 = an extended partition at the "end" of the drive (out of order). An extended replaces a primary and is simply a container for one or more logical partitions. In this instance it contains only sda5, your swap partition, about 6 GiB.

sda3 = primary = approx 500MiB. My guess is that this is your /boot partition and will be ext2. Fedora has an obsession with separate boot partitions. In my book they are a waste of time and unnecessary.

sda4 = primary = the LVM partition, about 194 GiB, most likely the Fedora root partition.

Fedora really has splurged itself in a most unsatisfactory manner all over your hard drive and made it near impossible to install anything else. This is typical of Fedora. Sorry. The only way to add more logical partitions to make room for Ubuntu is to remove sda4 (the Fedora root) so that you can extend sda2 backwards. Which means losing Fedora. And if you do that you might as well reformat the whole disc with a more sensible layout and start over. But before you think of doing that, we need to find out what is on sda1. It might be a separate /home or it might be empty and could therefore be used for Ubuntu.

I given you some food for thought. I'll be logging off soon, so you won't get anymore from me tonight. If you want to start over,  this means re-installing Fedora to pre-prepared partitions and then Ubuntu afterwards (**not** Fedora second). It'll be a bit daunting for a newcomer because the Fedora installer is a bit user hostile if you choose manual partitioning. 

What you don't have to worry about is grub, if you install Ubuntu second. Ubuntu will detect Fedora and set up a multi-boot menu. Fedora does not detect other Linux installations (but does pick up Windows) and you have to manually edit the grub configuration file yourself.

Post back with what you want to do, and we'll take it from there.

---

### Post by leucippus on 2010-08-27
> **coffeecat said:**
> 







 If you want to start over,  this means re-installing Fedora to pre-prepared partitions and then Ubuntu afterwards (**not** Fedora second). It'll be a bit daunting for a newcomer because the Fedora installer is a bit user hostile if you choose manual partitioning. 



  Okay, that sounds like a plan. Thanks

---

### Post by coffeecat on 2010-08-28
I won't tell you exactly what to do, but give you some thoughts which might help you decide how to go about it. I've been using both Fedora and Ubuntu for some years and both have quirks which you need to bear in mind.

First - before you do anything, it would be a good idea to find out what's on sda1. It's a Linux partition, but what is it? You could boot into the Ubuntu live CD and find it in the Places menu, and then look to see what's there. There may be some data you need to backup.

Next - you need to work out your own partitioning scheme before installing, rather than allow the installer to decide for you. And for this, you need to understand something about partitions and filesystems. I know you're not a beginner, but if you want somewhere to read up about partitioning, here's a good place to start:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Follow all the links - it's got some good stuff. You might want to think about setting up an extended partition with enough logicals in it for Linux. Linux can boot happily from a logical partition (unlike Windows) so you can put your root, swap and whatever other partitions you want in them. And you only need one swap partition. That can be used by whichever Linux OS you have booted into.

When you've got a good idea of what you want, I suggest you start a new thread to get some feedback. One thing that someone will inevitably suggest is a separate home partition. It's a good idea for easing upgrades from one release to the next, but it has definite downsides when you mix distros.

The first problem is that your UUID will be different in Fedora and Ubuntu: 500 in Fedora and 1000 in Ubuntu, so if you have the same username in the two distros you'll get permissions conflicts. But you won't have the same username because Fedora capitalises the first letter of your username whereas Ubuntu leaves it as all lower-case. Linux is case-sensitive so these are effectively separate names. And different usernames makes the whole point of a separate home partition moot.

What you might want to consider is a shared data partition, so that your personal files are accessible from both OSs. Trouble is, if you use a Linux filesystem (ext3 or 4) you'll have permissions problems again. You can get round this by using NTFS - which both Ubuntu and Fedora can deal with quite happily - but that's not a good idea if you haven't got Windows on the same machine. NTFS is a Windows filesystem and you really need Windows tools to repair it if you get filesystem corruption.

Once you've got a sensible partition scheme on your HD (use Gparted in the Ubuntu live CD), choose the 'advanced' option in the Fedora installer and the 'manual' option in Ubuntu. That gives you the opportunity to specify to the installer which partitions you want used for what. 

Lastly, just to repeat, install Fedora first because it won't detect Ubuntu. Then install Ubuntu which will install grub2 to the mbr of your HD and put a Fedora entry in Ubuntu's grub menu.

Good luck!

---

