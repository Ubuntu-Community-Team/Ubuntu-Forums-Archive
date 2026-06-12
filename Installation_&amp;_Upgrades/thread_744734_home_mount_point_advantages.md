---
title: "/home mount point advantages"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by shazzed on 2008-04-03
Ok so I want to set my  /home mount point on the same drive but separate partition. Like my setup of my widows install

ie. hda1 20gigs windows
     hda2 60gigs Data/files/games

1) Is home what I need to move in order to have this setup ?
  - I will be using wine for a couple of apps and a few games, and I believe this is where wine and install resides.

2) If I blow up my linux install and need to re-install will I be able to just set /home in the installer later on and not have to format or overwrite files already there form last install ?

3) If 2 is correct is there a non console way to /home from partition 1 to partition 2? As I am very happy with my current Ubuntu 7.10 install.

Would also be interested what other folders are movable and their advantages if any.
Cheers
Shazz

---

### Post by Pumalite on 2008-04-03
This might be helpful:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
And yes, you can save your /home for a new installation.

---

### Post by shazzed on 2008-04-03
> **Pumalite said:**
> This might be helpful:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
And yes, you can save your /home for a new installation.

Thank you Pumalite, a very handy link! :)
Looks pretty straight forward, nothing too scary in terminal. I guess if I stuff it all up I can just re-install and set my /home point then, only loss will be all those damn updates.

---

### Post by zvacet on 2008-04-04
> only loss will be all those damn updates.

Use [APTonCD](http://aptoncd.sourceforge.net/) ans you will save your updates.No need to download it from site(APTonCD),you have it in repositories.

---

### Post by jebasan on 2008-04-04
> **Pumalite said:**
> This might be helpful:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
And yes, you can save your /home for a new installation.

hi,

i have a question about your post. i already have another partition (formated and ready) that i'd like to use as home. is this tutorial will work with the system already installed? or do i really need to run from a live CD. what i mean is, to move the home partition to the new one, can't i umount and backup and the mount again?

---

### Post by Pumalite on 2008-04-04
If you are using the drive, the drive is mounted. That's why you need the Live CD.

"Requirements
You must use a live CD for this process, for two reasons:

   1. In order to resize your existing / partition, it needs to be unmounted. The only way to unmount it is for it not to be in use, which means you can't boot to your regular Ubuntu installation while resizing it... which means you need a live CD
   2. If you screw up your installation by accident, you can use the live CD to restore your old settings and, in the worst situation, at least recover your important files"

---

### Post by wkulecz on 2008-04-04
A seperate home partition on the same drive as the system is IMHO a bad idea for two reasons.

1) Its hard to guess how much size you need for system and home, making everything on one partiton of the full drive minus swap and perhaps another OS is most efficient as space is available to both as needed until the drive is full.

2) Performance is degrated because seeks between system files and home files are longer than necessary to skip the unused space in the system partition. 

Having home on a seperate drive will increase performance and eliminates these two objections.

While saving home across updates sounds good,  all those hidden /home/.app-name directories of settings almost always break after an update.  Back up your /home files without the hidden application directories and restore your files to the new clean home directory is usually the most trouble free way to go.

you can as root  rename /home to something else, mount your second drive on startup as /home and then copy your /somethingelse/* file to /home rsync works great for this. This is easiest if done in single user mode without an X windows login  or after booting from a live CD.  I use Knoppix 5.1.1 as my live CD as it has rsync and all the tools and makes it easy to mout your drives and maket them writable.

--wally.

---

### Post by VMan on 2008-04-04
> A seperate home partition on the same drive as the system is IMHO a bad idea for two reasons.

Unfortunately, some of us only have one HD in the computer (ie. laptops).  In this situation, I have found it quite useful to have /home on a separate partition on the same HD.  On my desktop computer, I have two HDs.  One of them is dedicated to /home.  

When I do a new install, I boot from the live CD, wipe all the hidden directories (saving a few data files) in /home and then do a clean install reusing the /home partition.  I found that I have to create the users in the same order that I did originally though (that was with ancient Mandrake installs; not sure if it is still required, but I always do it anyway).  

I have never attempted an upgrade, I just do a clean install of the new version.

---

### Post by Pumalite on 2008-04-04
You have to create the same users if you are keeping your /home partition.

---

