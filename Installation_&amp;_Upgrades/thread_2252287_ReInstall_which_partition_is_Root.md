---
title: "ReInstall which partition is Root"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by tpedersen6 on 2014-11-10
My system will suddenly only boot to a black screen that says "minimal bash-like line editing is supported..." then "Grub_"
I've tried Boot Repair without success.
I would like to try to just reinstall Ubuntu 14.04 but when I get to "Something Else" and my partitions I get "No root file system is identified"
I have several choices the most obvious is /dev/mapper/ubuntu-vg-root    type ext4 995220 MB
The other 2 likely choices are /dev/sda1  efi  536 MB      or  dev/sda2   ext2
Any thoughts on which one may have been the original Root /  ?

Thanks
Tim

---

### Post by TheFu on 2014-11-10
You used LVM on the prior install. That mapped device above is the root volume group. If you don't want the data, I'd remove all partitions and start over. Otherwise the steps forward completely depend on how good your backup are.

---

### Post by tpedersen6 on 2014-11-10
So do I want to reinstall and choose the partition labelled ubuntu-vg-root as the root partition for the reinstall?

---

### Post by TheFu on 2014-11-10
> **tpedersen6 said:**
> So do I want to reinstall and choose the partition labelled ubuntu-vg-root as the root partition for the reinstall?

Do you want the old data or not? If not, I'd wipe all partitions and start fresh. If you don't know how to use LVM, don't use it this time. Stay with simple partitioning.

---

### Post by tpedersen6 on 2014-11-10
I would like to keep the old data.  How should I proceed?

---

### Post by TheFu on 2014-11-11
> **tpedersen6 said:**
> I would like to keep the old data.  How should I proceed?

Do you have a backup?

---

### Post by tpedersen6 on 2014-11-11
I do have most of my data backed up but again if I can just do a reinstall to preserve the current configuration that's my first choice.  I know that I can wipe it all and start over. Do you have a suggestion on how to do that? I thought I could just redefine which partition was my root during the reinstall and I would be all set.  Maybe not but how should I proceed?
Tim

---

### Post by tpedersen6 on 2014-11-11
If it can't be done or is ridiculously difficult just say so and I'll give up on saving my current configuration and I'll reformat the entire drive.  Please post how to either recover or reformat.
Tim

---

### Post by TheFu on 2014-11-11
> **tpedersen6 said:**
> I do have most of my data backed up but again if I can just do a reinstall to preserve the current configuration that's my first choice.  I know that I can wipe it all and start over. Do you have a suggestion on how to do that? I thought I could just redefine which partition was my root during the reinstall and I would be all set.  Maybe not but how should I proceed?
Tim

My skills do not cover your needs. Sorry.  It may be a trivial thing to do what you need, I just can't say that nor can I provide steps.  If I had to do it, I'd have to google greatly and would RTFM a bunch before trying any command I didn't understand.  What I'd try to do:
* boot a live CD
* mount the existing volume
* backup all data and settings
* start over from scratch, not using LVM this time.
I doubt these are 1 command for each step.  With a 100% backup, I'd be willing to try things that might fail too. 

I have daily backups of all data and system configurations, so the situation you are in doesn't happen here.
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains.  However, LVM puts a wrinkle into everything for many of those methods. I use LVM on physical hardware, but those are minimal configurations here. Most of the systems run inside virtual machines which adds complexity, but also increases flexibility about 10x.

Wish I knew more to help. Sorry.

---

