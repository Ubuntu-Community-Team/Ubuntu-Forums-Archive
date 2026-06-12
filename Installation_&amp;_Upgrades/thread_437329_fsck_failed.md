---
title: "fsck failed"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by jinxjinx on 2007-05-08
So i boot my laptop running feisty and i get this 
"An automatic file system check (fsck) of the root file system failed. 

and it wants me to run fsck manualy. any idea how to do that?

Thanks

---

### Post by taurus on 2007-05-08
It should drop you to a prompt at that point.  Run

```
fsck /dev/hda1
```
**_if_** /dev/hda1 is where your root partition, /, is.

---

### Post by jinxjinx on 2007-05-08
so i ran
fsck /dev/sda1
and got a bunch of output here are a few things i jotted down
/dev/sda1 contains a file system with errors, check forced.
Pass 1: checking inodes, blocks, and sizes....
exception Emask 0x0 Serr 0x0 ....
action 0x0 [ 452.812000].... I/O error on device sda1, logical block 6324213
buffer I/O error on deice sda1....
then crashes...

eventually it says error reading block whatever (attempt to read block from file system result in short read) while doing inode scan. Ignore error<y>? 

and keeps asking me this over and over. if i say no it aborts: "cant read next inode"....

---

### Post by taurus on 2007-05-08
What was the last thing you did before you shutdown your machine or reboot your machine?  Did the power go out or something on your laptop?

Do you have a LiveCD handy somewhere?  Boot from it and post the output of this command.

```
sudo fdisk -l
```

---

### Post by jinxjinx on 2007-05-08
thanks it says 
cannot open /proc/partitions

oddly enough the power did go out last night, but its a laptop so shouldnt that not matter?

---

### Post by taurus on 2007-05-08
When the power went out, did it crash your machine or did you shut it down normally?

---

### Post by jinxjinx on 2007-05-08
not sure. its actually a friends laptop. im guessing its reformat time...

---

