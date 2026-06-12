---
title: "new to linux and need help"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by starfarer on 2005-02-19
Hi everybody, I'm totally new to Linux though once(around 98-99) tried without much success  :-? . This time round i'm really impressed by installation and detection of hardware and even the read capability of NTFS filesystem. Some questions:

1) I'm using Athlon AMD XP cpu and reading that kernel should be 686 while on my system its 386. If i want to change then how? can you post detail instructions.

2) I can mount and read NTFS(winxp) which is primary partition on primary ide. How to I  mount(hda#) for extended partition on primary ide(thats actually partition of fat32)?

3) How to make windows XP default at boot? currently it's linux.


i think this thread will be long........ :grin:

---

### Post by CyrilleMortreux on 2005-02-19
> 1) I'm using Athlon AMD XP cpu and reading that kernel should be 686 while on my system its 386. If i want to change then how? can you post detail instructions.

Using synaptic or apt-get

Try to fing "linux-image" and choose no 686, no 386, but K7 because you are using an Athlon. 

Try "apt-cache search linux-image K7"
Look at the list and install the right image
"apt-get install linux-image-2.6.11-1-k7" (this is just an example)

Using synaptic should be easier but I don't use it myself. 

> 
2) I can mount and read NTFS(winxp) which is primary partition on primary ide. How to I  mount(hda#) for extended partition on primary ide(thats actually partition of fat32)?

Harder...
Your system has to have the ntfs module loaded, and then most of the time, you will be able to read it, not to write on it. 

All as root : 

- Making a mount point first
"mkdir /mnt/ntfs"

- Loading the ntfs module
"modprobe ntfs"

- Mounting your disk 
"mount /dev/hda1 /mnt/ntfs"

- Browsing your NTFS disk
"cd /mnt/ntfs && ls"

If someone has something easier ...
This way works for all Linux boxes.

> 

3) How to make windows XP default at boot? currently it's linux.

Depending if you are using GRUB or LILO, but I think that must be GRUB.
The easiest way is to install "grubconf" and to use it with Gnome

"apt-get install grubconf"

And use it  :roll:

---

### Post by starfarer on 2005-02-19
ok now updating kernel K7..actually its available after adding extra repositories. Before was showing message "package not available". 

Actually my question was: how the hard disk notation is in linux? 
Primary IDE - Primary partition - hda1
Primary IDE - Extended Partition - hda?
Primary IDE - Logical Partition - hda?

Secondary Slave - Primary Partition -h??
Secondary Slave - Extended Partition - h??
Secondary Slave - Logical Partition - h??

Thanks.

---

### Post by kassetra on 2005-02-19
Ok, let's start here:
 Primary drive, Primary ide chain: hda
 Secondary drive, Primary ide chain: hdb
 Primary drive, Secondary ide chain: hdc
 Secondary drive, Secondary ide chain: hdd
 
 As far as the numbers go:
 1 = usually the primary partition
 2,4 or 5 = usually the extended partition
 logical partition numbers start after the extended partition number, so 3, 5, or 6 respectively.
 
 Does that help?

---

### Post by starfarer on 2005-02-20
Thanks and it did helped!. Now i'll try to install driver for ATI RADEON and soundcard which is Turtle Beach Santa Cruz.

---

