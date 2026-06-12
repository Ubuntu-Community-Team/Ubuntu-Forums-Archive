---
title: "Unable to boot into Ubuntu, i have a fsck problem"
date: 2019-09-20
forum: Installation &amp; Upgrades
---

### Post by stephen-parish on 2019-09-20
Hi I am having problems with getting into ubuntu on my laptop, on startup it keeps telling me to run fsck manually.
I have googled instructions on this and tried every step that i found but just can not get fsck to run, i can't even see the recovery menu
at the moment the tect i have on my laptop screen is as follows  .....

/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found.

/dev.sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e. , without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda1 requires a manual fsck

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter `help` for a list of built-in commands.
(Initramfs)

I just can not get pass this or get my laptop to boot normally intu ubuntu. can you help me please.
Do bare in mind i am a novice at this so please keep replies as simple as possible.

Thank you.

The Laptop in question is a compaq Presario CQ57 - Dual core

---

### Post by oldfred on 2019-09-20
It says run manual fsck.
From Ubuntu live installer booted in live mode run the full fsck/e2fsck commands.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by stephen-parish on 2019-09-20
thank you for your reply, but i am still stuck as what to do next ?

---

### Post by stephen-parish on 2019-09-20
when i type sudo parted -l 
i get the following text ....
(initramfs) sudo parted -1
sh: sudo: not found
(initramfs)

---

### Post by stephen-parish on 2019-09-20
ok i think i have sorted it, i typed in the following
fsck -yf /dev/sda1
then pressed enter
let it do it's thing then just rebooted, it found and fixed a few errors and am now back into my Ubuntu system.

Hopefully that was the correct procedure.

Thank you

---

