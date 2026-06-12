---
title: "Trying to clone flash drive installation"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by bryceowen on 2010-02-16
I have installed Karmic on a 4gb flash drive that has been working famously for the past few months. I am now in possession of an 8gb flash drive that I would like to migrate the install to. I can't use the methods I've used in the past to clone Windows installs due to the tools not being able to read ext4.

First, a description of the source drive:
3.5gb ext4 partition as /
512mb swap partition

Here's what I've tried and what the result was (sdb is the source, sdc is the target), all of which tried on a separate machine using Karmic:

Method: Clone the drive using dd_rescue
Result: Cloned drive fails to boot, resulting in blinking cursor in the upper left of screen.

Method: dd if=/dev/sdb of=/dev/sdc
Result: Grub-rescue prompt throwing an error of unknown filesystem. ls shows (hd0),(hd0,1), but all other commands throw the filesystem error.

Method: Install Karmic on the new drive using the previous install's partitions then running dd if=/dev/sdb1 of=/dev/sdc1
Result: After installing Karmic fresh on the drive, it boots fine. After cloning the / partition, grub2 throws the previously mentioned filesystem error.

Method: Install Karmic on the new drive using the previous install's paritions (again) and directly copying the contents of the source partition to the target partition.
Result: In progress. Will let you know when it finishes installing and copying.

So, anyone have any luck doing this? Any hints how to make it work? There's no encryption on either drive, so that shouldn't be a factor.

---

### Post by ajgreeny on 2010-02-16
Are the drives and partitions using different UUIDs?  I thought dd copied everything including that, but maybe that's not so, and a quick edit of the UUID info in the menu.lst or the new grub.cfg indirectly with the config files in /etc/grub.d or /etc/default/grub will do the trick.

---

