---
title: "delete everything!"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by nathan28 on 2011-04-04
Not really. But my personal machine is a dual-boot with Vista... and I don't have anything on Vista that I need except maybe iTunes, which I can use through XP on my dual-boot work machine.

So, it's time to nuke the windows partitions and go to a 'pure' linux machine.

But I don't want to lose my current /home files. Here's how I plan to partition:

part. 1 boot sector where GRUB lives
part. 2 modest swap (1-1.5 GB, I've got 4gb RAM but am kind of a just-in-case guy)
part. 3 / + /home for distro one (ext4) (Ubuntu 10.10) ~15 gig
part. 4 / + /home for distro two (ext4) (probably Fedora, maybe 11.04 until I decide that yes, Unity does suck, or, OMG Unity doesn't suck etc) ~15 gig
part. 5 (optional) / for Linux from Scratch (ext3) insane side-project (Why? Why? I don't even plan on working in IT, I just like doing difficult things, I guess)
part 6-whatever. data, i.e, true "home" partitions. (ext4)

Is that right? If I create a ~250mb /boot w/ the Ubuntu installer I'll be able to use that to get into another distro from grub, right? Or is there another way to do this?

Problem is that Windblows is on the first part of the disk, so I may have to straight-up dump my package list, copy my personal files and docs to a storage disk and do a full-on nuke & pave instead of tactical deployment. Should probably call AT&T and pay my overdue internet bills first.

[SIZE="1"](Yes, Ubuntu, I am breaking up with you)[/SIZE]

---

### Post by cbowman57 on 2011-04-04
It's just my opinion but I like at least 500mb for a dedicated /boot partition in case I play with an assortment of kernels.

---

### Post by Hedgehog1 on 2011-04-04
If you are planning on converting your partition map from the MBR style (with 4 primary partitions max) to the GPT style (with 'unlimited' partitions), you will need to move your data off the disk, change the partition map, and add the partitions back onto the disk in the order you want.

You can copy partitions from disk to disk using gparted - but gparted changes the UUIDs of them.

You can also use clonezilla, and I think that leaves the UUID of the partition alone.

You could also get a 1tb disk, move your partitions to it, and use this disk as storage....


***The Hedge***

:KS

---

### Post by matt_symes on 2011-04-04
Hi

The general advice is, if you want to hibernate makes sure your swap is at least as large as your RAM.

Kind regards

---

### Post by srs5694 on 2011-04-04
> **Hedgehog1 said:**
> If you are planning on converting your partition map from the MBR style (with 4 primary partitions max) to the GPT style (with 'unlimited' partitions), you will need to move your data off the disk, change the partition map, and add the partitions back onto the disk in the order you want.

Actually, [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) can convert from MBR to GPT non-destructively. That said, nathan28 didn't mention GPT. GPT isn't necessary for the sort of configuration than nathan28 is describing; it would just be necessary to create many of the partitions as logical partitions rather than as primaries. OTOH, GPT does have several (mostly minor) advantages over MBR, and on a Linux-only system, IMHO these minor advantages are enough to recommend GPT over MBR. You've got to do some research, though, if you're not familiar with GPT. My GPT fdisk page, to which I've just linked, is a start.

As to the more general plan, I recommend using a single /home partition for all your distributions. You should be careful to use different home directories on that partition for each distribution, though. This is most easily accomplished by using different usernames for each distribution; however, you can change the username *without* changing the home directory after creating the initial account if you'd like to have the same username for all the distributions.

---

### Post by Hedgehog1 on 2011-04-04
> **srs5694 said:**
> Actually, [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) can convert from MBR to GPT non-destructively. That said, nathan28 didn't mention GPT... 

Well, I could have saved myself some extra hassle last week had I realized this.  ***Did I mention how much I keep learning?***

You are correct, nathan28 do not mention GPT. His partition list did show it growing from 4 to 6 partitions over time, with no mention of extended partitions; so I made a leap (into the deep end, it appears).



***The Hedge***

:KS

---

### Post by nathan28 on 2011-04-09
> **srs5694 said:**
> As to the more general plan, I recommend using a single /home partition for all your distributions. You should be careful to use different home directories on that partition for each distribution, though. This is most easily accomplished by using different usernames for each distribution; however, you can change the username *without* changing the home directory after creating the initial account if you'd like to have the same username for all the distributions.

I had felt like having multiple usernames under /home wasn't the elegant solution as far as end use, on my work machine I have a dual boot and four user IDs. But I'm thinking from a disk perspective that might be the best choice.

so let's say I have a /home partition.

/home/me_ubuntu
/home/me_fedora
/home/me_snowflakeinhell_linuxfromscratch

If i create a directory

/home/documents
/home/downloads

etc. and sym-link /home/me_ubuntu/documents and /home/me_fedora/documents to that "true" /home/documents, That should dump files from the different distros into the 'true' directory? What config files could I edit to avoid the sym-link?

---

### Post by srs5694 on 2011-04-09
I'd use one of the home directories (say, /home/me_ubuntu) as the "master" one for files you'd want to use across distributions and then symlink to it from the other distributions' home directories. That's probably simpler than trying to edit configuration files to look in unusual places, since you'd likely have to change quite a few different configuration files to do it that way.

---

### Post by nathan28 on 2011-04-09
> **srs5694 said:**
> I'd use one of the home directories (say, /home/me_ubuntu) as the "master" one for files you'd want to use across distributions and then symlink to it from the other distributions' home directories. That's probably simpler than trying to edit configuration files to look in unusual places, since you'd likely have to change quite a few different configuration files to do it that way.


That's true, and there'd probably be issues with files in different /tmp's, too.

I'm marking this as solved since it's not really a "problem" question.

---

