---
title: "Dual boot Ubuntu/Vista"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by {Nabla} on 2008-10-15
hi I've got vista installed and want to dual boot it with ubuntu. I followed the guide here: 

[http://apcmag.com/how_to_dualboot_vi...lled_first.htm](http://apcmag.com/how_to_dualboot_vi...lled_first.htm)

and made the partition like it said.

Then I ran through the installation and at the final stage where it gave the option to install, it gave an installation summary, and said:

> 
The following partitions are going to be formatted:

partition #5 of SCSI1 (0,0,0) (sda) as ext 3
partition #6 of SCSI1 (0,0,0) (sda) as swap 

I selected 'guided - select largest continuous free space' for the installation options, but I want to be sure that I'm not formatting my vista/data partition.

How can I check this? Can you do it through disk management, because the partitions don't appear to be named?

---

### Post by Partyboi2 on 2008-10-15
You should be able to check what partitions are what by opening gparted (system>Admin>Partition Editor) or from a terminal
```
sudo fdisk -l
```

---

### Post by Pumalite on 2008-10-15
You have to allocate space for Ubuntu wi5th Vista partitioner firsat. Then use Gparted Live CD and make 3 'New' partitions:
10 GB for '/'
The rest minus your RAM for /home
Your RAM for /swap
In the freed space make an extended partition and within that place allk the others:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by {Nabla} on 2008-10-15
Partyboi: How can I run a linux command in Vista? I haven't installed linux yet. (I am new to linux)

Pumalite: I have made the partition using [rightclick] Computer > manage > disk manager > shrink vista partition. So I now have a smaller Vista partition, and some unallocated space (which I want to install Ubuntu on).

Can you please walk me through what I need to do now with Gparted? I have never done this before.

Thanks alot.

Edit: my partition looks like this so far:

[IMG]http://img392.imageshack.us/img392/2449/58641099ev4.jpg[/IMG]

---

### Post by Pumalite on 2008-10-15
Do not shink Vista with Gparted. Use the Vista partitioner to allocate free space for Ubuntu first

---

### Post by {Nabla} on 2008-10-15
I haven't used Gparted yet, I used windows disk manager to shrink it, as this is what the guide suggested. 

> Use the Vista partitioner to allocate free space for Ubuntu first 

How do I do that?

---

### Post by Aero-Z on 2008-10-15
> **{Nabla} said:**
> I haven't used Gparted yet, I used windows disk manager to shrink it, as this is what the guide suggested. 



How do I do that?
Nothing to do there anymore. The Unallocated Space is the free space where you can install Ubuntu.
The "use largest continuous free space" checks for that unallocated space. I don't remember anymore but if you use guided then check for the sizes of the partitions Ubuntu's installer want to create (the installer should notice you at some point how large are those new partitions going to be). "ext3" plus "swap" should be a total of around 29.79GB.

---

### Post by {Nabla} on 2008-10-15
> **Aero-Z said:**
> Nothing to do there anymore. The Unallocated Space is the free space where you can install Ubuntu.
The "use largest continuous free space" checks for that unallocated space. I don't remember anymore but if you use guided then check for the sizes of the partitions Ubuntu's installer want to create (the installer should notice you at some point how large are those new partitions going to be). "ext3" plus "swap" should be a total of around 29.79GB.

Ahh ok thanks so I have the free space set up already now for Ubuntu install. I can't recall the installer notifying me of how big the partitions are, It simply referred to them obscurely (and un-helpfully) as:


> partition #5 of SCSI1 (0,0,0) (sda) as ext 3
partition #6 of SCSI1 (0,0,0) (sda) as swap 


but I will run it again and see to make sure.

By the way, what do you mean by "the partitions Ubuntu's installer wants to create"? I thought I had already created a partition for the Operating system, I don't understand why the installer needs to create any more partitions for it. Are you saying the guided mode will search for the unallocated space, and partition it into those partitions above? Because they are two different formats/file systems I think I have picked up.

I wish there were just some easy way to be sure of which partitions I am formatting before I install...for instance if the unallocated space in windows disk manager was labelled as "SCSI (0,0,0) (sda)" Then everything would make sense and I would happily continue.

---

### Post by Pumalite on 2008-10-15
Read my post # 3

---

### Post by Partyboi2 on 2008-10-15
> By the way, what do you mean by "the partitions Ubuntu's installer wants to create"? I thought I had already created a partition for the Operating system, I don't understand why the installer needs to create any more partitions for it.
All you did with vista disk management is make  space (unallocated) for the ubuntu partitions. You still need to make the partitions for ubuntu which you can do as mentioned by Pumalite.

---

### Post by {Nabla} on 2008-10-16
I have it all working now thanks, just need to change the bootloader according to the guide, and then start learning/configuring Ubuntu.

---

### Post by Pumalite on 2008-10-16
Good:
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

