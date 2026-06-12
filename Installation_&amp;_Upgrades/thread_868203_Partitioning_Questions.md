---
title: "Partitioning Questions"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Helical on 2008-07-23
I have my free space made and am doing a manual partitioning but I have a few questions. My Windows setup already has two partitions a "recovery partition" and the main Windows partition. What I need to know is how many more partitions I can make, I've heard there is a limit; is this limit on primary and logical partitions (what is the difference between these)? I also don't know if partitions should be at the beginning or end.

Here is my ideal setup: [Windows Recovery] [Windows] [/Home] [/] [swap]

But I'm not sure if I'm able to do that with a SATA HDD. Do all of these need primary partitions? Thanks.

P.S. Sort of unrelated question but, I'm going to probably need to do a fresh install of 64 bit Vista which is already installed but will that be a problem (I hear Vista is finicky about this sort of thing).

---

### Post by avtolle on 2008-07-23
There is a limit of four physical partitions. The way around this is to create an extended partition, under which one may have a large number of logical partitions. What I would suggest you try is to first, resize your main Windows partition using the Vista tool for this purpose. Then, for your manual partitioning scheme, you could create one more physical partition, formatted ext3, for root, mount point /. Then, create an extended partition, under which you might create the swap partition and the home partition (mount point /home).

The Liux partitions may all be logical partitions under the extended partition, if you want to do it in that fashion.

EDIT: [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) may be of some interest to you in your planning as well. Good luck (and remember to defrag that Windows partition at least twice before resizing).

---

### Post by Helical on 2008-07-23
I was unable to defrag and I used G-Parted to resize my Windows partition (but many guides suggest this I don't think it will be a problem); this is because I couldn't access my Windows partition due to BSOD from a crappy Windows Update which installed drivers that messed everything up. So I cannot access Windows at all no matter how many ways I try, system restore doesn't even help, so that's why I said earlier that I would have to probably reformat Windows. I only got my laptop on the tenth so it shouldn't be too fragmented right now anyway.

How do I make an extended partition? I'm looking at the installer and I'm doing the manual partitioning and it doesn't say anything about extended partitions.

---

### Post by louieb on 2008-07-23
> **Helical said:**
> ...How do I make an extended partition? I'm looking at the installer and I'm doing the manual partitioning and it doesn't say anything about extended partitions.

The easiest way is to use GParted before you start the install. 
Just select the unallocated space and create a new extended partition using all the unallocated space. 
The space will still show as unallocated. Select it again to create the / (root) /home and swap partitions. Should just let you create logical partitions - thats alright - thats what you want.

When you get to the partition part of the install choose manual. Then select the partition to use for / (root) edit it and tell the installer to mount it as / (root). Do the same for /home. The installer should pick up and use the swap partition automatically.

---

### Post by estyles on 2008-07-23
I think Ubuntu is one of the LiveCD's that lets you install straight from the boot-up menu, instead of making you run the OS off the LiveCD, then install.  Assuming that's true, I thought I would mention that you should choose "Try Ubuntu without installing it" or whatever the option is called that lets you boot onto the LiveCD.  Then go to System->Administration->Partition Editor, and use that to partition your drive.  The partitioner that runs as part of the install is kind of balls.  It stalled up on me several times (both with Ubuntu and Linux Mint, which, being almost identical to Ubuntu, I'm sure uses the same partitioner in the install), and I thought I would lose my Windows partition.  Luckily I didn't lose any data, but definitely boot the LiveCD and use gparted before installing.

---

### Post by Helical on 2008-07-23
Wow, thanks, G-Parted is a lot easier than the installation partitioner. I just have a some other questions:

1. Is it ok to leave some free space before my partition so that I can add it to my Vista or Ubuntu partition should I need to later? It would be setup like this: [Recovery] [Vista] [Free] [Ubuntu extended partition]
2. I'm probably going to be reinstalling Vista, this won't be a problem will it (if Ubuntu is already installed)?
3. This extended + logical partition setup will allow me to later on delete the root logical partition if I want to try a different distrobution correct?
4. What is the optimal size for the root partition?

Again, thanks for all the help and info.

---

### Post by estyles on 2008-07-23
No problem at all leaving some free space.  You can add it in as you see fit.  Note that if you want to change the size of the extended partition, you'll need to use GParted off the LiveCD.  You can't use GParted to resize an active partition, and if Ubuntu is part of the extended partition, and it's active, that makes the whole extended partition off-limits.

When you re-install Vista, it might clobber Grub.  Not sure about this.  If so, you should be able to reinstall Grub using the LiveCD.  Someone else may have more info on this.

You *can* delete Ubuntu and install a different distro, using the same home directory.  Unfortunately, if you delete Ubuntu because something is screwed up, you might not know if it's the OS or something in your settings (which are stored in your home partition).  I use a more complicated partitioning scheme, where I *don't* mount a /home partition (/home is stored on the same partition as the OS), but I mount partitions for /Documents, /Music, /Downloads, and /Wine.  It gets a little crazy, but the idea is that I can copy over my /etc/fstab file, and there are symbolic links in the home directory that I can copy (i.e. Pictures is a link that points at /Documents/Pictures, and /Documents is a mounted partition - so I just copy all the symbolic links in the home directory) any time I install a new distro.  I haven't completely tested this out, but it seems to work well so far.  I *did* start out with a separate /home partition, and when I decided to wipe out Ubuntu and put on Linux Mint, that's when I went with the more complicated system.  But it is *definitely* more complicated.  For now, you should be fine using /home, and if you decide to change that, you can just copy stuff over from your old /home partition.  So, short answer, yes.

Root should be around 10GB.  I tend to go with 15GB, to be safe.  You could get by on as little as 5GB.  10GB is probably optimal.  I have yet to get a distro over 7GB usage, but then I haven't really tried that hard or for very long either.

---

### Post by Ptero-4 on 2008-07-23
Gentoo based distros tend to go a bit close to that 7GB you said.

---

### Post by estyles on 2008-07-23
> **Ptero-4 said:**
> Gentoo based distros tend to go a bit close to that 7GB you said.

Gentoo is source-based, IIRC, right?  If so, I can see what you mean, if they download and compile the source for *everything*, assuming that the source isn't deleted afterward.  Of course, I've never used Gentoo or looked into it very much, so maybe I have no idea what I'm talking about...  \\:D/

---

### Post by louieb on 2008-07-23
> **Helical said:**
> 
2. I'm probably going to be reinstalling Vista, this won't be a problem will it (if Ubuntu is already installed)?

Last OS installed will get its boot loader called from the MBR. Not a problem thought. You'll just get to learn how to restore GRUB to the MBR and you'll get the bonus of learning how to make GRUB boot VISA. (or you can go the easy route the Super GRUB CD can do all that for you.)

A full install if Ubuntu - /home is a little less than 4GB.   I usually make my / (root) partition 7-10GB.

---

### Post by Ptero-4 on 2008-07-24
> **louieb said:**
> Last OS installed will get its boot loader called from the MBR. Not a problem thought. You'll just get to learn how to restore GRUB to the MBR and you'll get the bonus of learning how to make GRUB boot VISA. (or you can go the easy route the Super GRUB CD can do all that for you.)

A full install if Ubuntu - /home is a little less than 4GB.   I usually make my / (root) partition 7-10GB.

Wow. didn't know GRUB could boot credit cards.

---

### Post by louieb on 2008-07-24
> **Ptero-4 said:**
> Wow. didn't know GRUB could boot credit cards.
:guitar:But yea if it can be chainloaded Grub can boot it.
Was hoping there was a VISA Linux but this is as close 
[IMG]http://www.linuxfund.org/img/usbank-card.jpg[/IMG]

[IMG]https://applications.usbank.com/oad/begin?locationCode=9592&sourceCode=71013[/IMG]

---

