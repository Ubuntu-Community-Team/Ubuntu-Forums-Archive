---
title: "how many installations of ubuntu are possible on one HD?"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by wormy11 on 2008-09-24
and how would i set that up?

Ubuntu rocks so hard, i want as many installations as possible!  ;o)

Thanks!

---

### Post by snowpine on 2008-09-24
> **wormy11 said:**
> and how would i set that up?

Ubuntu rocks so hard, i want as many installations as possible!  ;o)

Thanks!

Theoretically as many as you want, but why not just do one installation, then set up several user accounts, each with different settings? Otherwise, you'd be wasting your hard drive space duplicating the same system files over and over again. :)

---

### Post by wormy11 on 2008-09-24
I am aware of multi-user accounts, but need seperate installs for my current project.

Specifically, I'd like to know how to: 1-use the install wizard (either from the LiveCD, or from the first ubuntu subsequent install) for these multiple installs, and 2-how exactly to setup the partitioning for each install.

---

### Post by snowpine on 2008-09-24
> **wormy11 said:**
> I am aware of multi-user accounts, but need seperate installs for my current project.

Specifically, I'd like to know how to: 1-use the install wizard (either from the LiveCD, or from the first ubuntu subsequent install) for these multiple installs, and 2-how exactly to setup the partitioning for each install.

Let's say for the sake of argument you want 4 completely separate Ubuntu installs.

Boot from the Live CD and start the GParted Partition Editor (it's in the System menu or type 'gparted' from the command line).

Set up 3 primary partitions and 1 extended partition. Add 2 logical partitions inside the extended partition. This will give you a total of 5 partitions. Format 1 of the partitions as linux-swap and make it equal to 1.5x your ram (it can be smaller or larger depending on your needs). Format the remaining 4 partitions to ext3 filesystem and make them equal in size (I recommend 5gb minimum).

When you install and you get to the partitioner stage, choose Manual. Pick a partition, say /dev/hda1, and mount it as /. (You don't need to format since it is already ext3.) Proceed with the installation.

When doing install #2, manually install it to the next available partition by mounting /dev/hda2 (for example) as /.

That's the quick version... Does that make any sense?

You can also explore virtual machines using an application such as Virtualbox. That would allow you to have multiple Ubuntus runniing at the same time on different windows, very useful for comparing.

---

### Post by wormy11 on 2008-09-24
Is it possible to use 1 primary partition and use that as the boot loader (say 256mb); than a second as an extended partition, and then setup say 9 logical partitions from that extended space, and install 8 installs and one swap there?

is there a limit on logical partitions? and can i use reiserfs instead on all the partitions including the bootloader?

---

### Post by snowpine on 2008-09-24
> **wormy11 said:**
> Is it possible to use 1 primary partition and use that as the boot loader (say 256mb); than a second as an extended partition, and then setup say 9 logical partitions from that extended space, and install 8 installs and one swap there?

is there a limit on logical partitions? and can i use reiserfs instead on all the partitions including the bootloader?

I am pretty sure you can have 9 partitions, but I'm afraid your other questions are heading into uncharted territory for me. :)

I would be curious to find out more about your experiment and what you hope to learn.

---

### Post by wormy11 on 2008-09-24
ok, i will give it a go now on a fresh hd.  i'll report back with my findings shortly.

thanks for your help snowpine

---

### Post by xebian on 2008-09-24
> **wormy11 said:**
> Is it possible to use 1 primary partition and use that as the boot loader (say 256mb); than a second as an extended partition, and then setup say 9 logical partitions from that extended space, and install 8 installs and one swap there?

is there a limit on logical partitions? and can i use reiserfs instead on all the partitions including the bootloader?

Absolutely.  The limit on logical is probably how big is your hard drive.

---

### Post by sneeks on 2008-09-24
there is a vid that alan pope has done that covers this in a way,check out the ubuntu screencasts that uses the text install for ubuntu,hope it helps..
sneeks

---

