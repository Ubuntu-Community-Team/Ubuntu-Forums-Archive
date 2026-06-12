---
title: "Installing on FakeRAID"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by phazonmutant on 2008-11-13
I'm having some trouble installing Ubuntu 8.04 on my system.
First off, I have an Asus Maximus Formula motherboard (X38 chipset), which uses the Intel ICH9R southbridge.  I have 2 SATA II hard drives striped in a RAID 0 array using the mobo's RAID controller.  As I've found out, Linux doesn't like that very much.

I've been referring to the FakeRaidHowTo article over in the Ubuntu documentation, but I'm stuck at creating the filesystem.  So far, I've installed dmraid successfully, partitioned my drive into 3 partitions -- one for windows, one for linux, and one for swap.  The output from "sudo fdisk -l "/dev/mapper/isw_cfebfidbf_Mother Brain 2" is:
```
Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cfebfidbf_Mother Brain 2p1   *           1       75277   604655612    7  HPFS/NTFS
/dev/mapper/isw_cfebfidbf_Mother Brain 2p2   *       75278       77500    17856247+  83  Linux
/dev/mapper/isw_cfebfidbf_Mother Brain 2p3           77501       77826     2618595   83  Linux
```

After that, "sudo mkfs -t "/dev/mapper/isw_cfebfidbf_Mother Brain 2p2"" returns:
```
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/mapper/isw_cfebfidbf_Mother Brain 2p2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```
After that, experimented a bit.  I discovered the command e2label, and tried out "sudo e2label "/dev/mapper/isw_cfebfidbf_Mother Brain 2"", which returns:
```
Bad magic number in super-block while trying to open /dev/mapper/isw_cfebfidbf_Mother Brain 2
Couldn't find valid filesystem superblock.
```

Next, I tried "sudo e2label "/dev/mapper/isw_cfebfidbf_Mother Brain 2p2"", hoping that would find the second partition.  Alas:
```
e2label: No such file or directory while trying to open /dev/mapper/isw_cfebfidbf_Mother Brain 2p2
Couldn't find valid filesystem superblock.
```

I'm out of ideas, and nervous that I've screwed up my partition table.
I'm a Windows user fed up with Windows.  Linux isn't making life easy, though, for probably the second time in my life I've used it.  Any advice on how to create the filesystem and/or finish the installation?  Thanks.

*PS: I'm not using 8.10 because the live CD boots to a black screen.  I'm guessing some incompatibility with my ATI HD 3870 graphics card.  Any ideas?*

---

### Post by cariboo on 2008-11-13
You are probably running into problems because of the spaces in the volume name:

> dev/mapper/isw_cfebfidbf_Mother Brain 2

with the spaces between Mother and Brain and Brain and 2, Linux thinks they are three different devices. Linux on the command line does not like spaces in file names, you should be able to fix the problem by using the \ in place of the spaces.

Jim

---

### Post by phazonmutant on 2008-11-14
Hmm, no, that didn't work.  Just to verify, I tried:
```
ubuntu@ubuntu:~$ sudo e2label "/dev/mapper/isw_cfebfidbf_Mother\Brain\2p2"
```
and
```
sudo mkfs -t ext3 "/dev/mapper/isw_cfebfidbf_Mother\Brain\2p2"
```
They returned the same results as before.

Shouldn't wrapping the string in quotes (as I did) solve the space problem?

Let me make sure I'm understanding some things: Ubuntu sees both hard drives, but doesn't mount them, instead, it maps to the RAID disk?  Also, are the RAID disks even mounted on a live cd?  So, when it says /dev/mapper/blah_Mother Brain 2p2, that means it's partition 2, right?
Also, random question, when I accidently type something like "sudo garbagestring", it starts only displaying ">" on new lines.  How do you get back to the main terminal thing?

---

### Post by psusi on 2008-11-14
What does ls /dev/mapper look like?

For general sanity, I would also get rid of the complex name with spaces and numbers.  Reformat the array in the bios and just leave the volume name the default, which should be just Volume0, not Mother Brain 2.

---

### Post by phazonmutant on 2008-11-14
Ah, that's what I was about to ask.  I have an existing Vista install in partition 1 that I'd really rather not destroy, if at all possible.  I agree, there's no point in having the volume name be odd, so is it possible to change without destroying the RAID array and/or the partitions?

Anyway, ls /dev/mapper returns:
```
control isw_cfebfidbf_Mother Brain 2
```


One huge question at this point: Can I safely shut down from the live CD?  Do I need to delete the partitions I created or anything?

---

### Post by psusi on 2008-11-14
I don't think you can change the name without reformatting.  From the livecd can you post the output of sudo dmraid -ay -dddd -vvvv?

It looks like dmraid fails to activate the partitions in the device, possibly because of the space in the name.  It shouldn't do that, so if that is the case I'll ask you to file a bug and attach the dump of your metadata for debugging and I'll see if I can fix the bug.

---

### Post by phazonmutant on 2008-11-14
Here's the output.
```
ubuntu@ubuntu:~$ sudo dmraid -ay -dddd -vvvv
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: isw metadata discovered
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_cfebfidbf
DEBUG: _find_set: not found isw_cfebfidbf
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: not found isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: not found isw_cfebfidbf_Mother Brain 2
NOTICE: added /dev/sdb to RAID set "isw_cfebfidbf"
DEBUG: _find_set: searching isw_cfebfidbf
DEBUG: _find_set: found isw_cfebfidbf
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: found isw_cfebfidbf_Mother Brain 2
DEBUG: _find_set: found isw_cfebfidbf_Mother Brain 2
NOTICE: added /dev/sda to RAID set "isw_cfebfidbf"
DEBUG: checking isw device "/dev/sda"
DEBUG: checking isw device "/dev/sdb"
DEBUG: set status of set "isw_cfebfidbf_Mother Brain 2" to 16
DEBUG: set status of set "isw_cfebfidbf" to 16
RAID set "isw_cfebfidbf_Mother Brain 2" already active
INFO: Activating GROUP RAID set "isw_cfebfidbf"
NOTICE: discovering partitions on "isw_cfebfidbf_Mother Brain 2"
NOTICE: /dev/mapper/isw_cfebfidbf_Mother Brain 2: dos     discovering
NOTICE: /dev/mapper/isw_cfebfidbf_Mother Brain 2: dos metadata discovered
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 21
DEBUG: _find_set: not found isw_cfebfidbf_Mother Brain 21
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 22
DEBUG: _find_set: not found isw_cfebfidbf_Mother Brain 22
DEBUG: _find_set: searching isw_cfebfidbf_Mother Brain 23
DEBUG: _find_set: not found isw_cfebfidbf_Mother Brain 23
NOTICE: created partitioned RAID set(s) for /dev/mapper/isw_cfebfidbf_Mother Brain 2
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_cfebfidbf_Mother Brain 2"
DEBUG: freeing device "isw_cfebfidbf_Mother Brain 2", path "/dev/sda"
DEBUG: freeing device "isw_cfebfidbf_Mother Brain 2", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_cfebfidbf"
DEBUG: freeing device "isw_cfebfidbf", path "/dev/sda"
DEBUG: freeing device "isw_cfebfidbf", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_cfebfidbf_Mother Brain 21"
DEBUG: freeing device "isw_cfebfidbf_Mother Brain 21", path "/dev/mapper/isw_cfebfidbf_Mother Brain 2"
DEBUG: freeing devices of RAID set "isw_cfebfidbf_Mother Brain 22"
DEBUG: freeing device "isw_cfebfidbf_Mother Brain 22", path "/dev/mapper/isw_cfebfidbf_Mother Brain 2"
DEBUG: freeing devices of RAID set "isw_cfebfidbf_Mother Brain 23"
DEBUG: freeing device "isw_cfebfidbf_Mother Brain 23", path "/dev/mapper/isw_cfebfidbf_Mother Brain 2"

```

If I need to dump the metadata, can you point me to a tutorial on how to do that?

---

### Post by psusi on 2008-11-14
sudo dmraid -rD will dump it to a few output files in the current directory.  Toss them into a tar.gz and attach it to a bug report on launchpad.  File the bug against dmraid and name it something like "Partitions fail to activate on volumes with complex names".

---

### Post by phazonmutant on 2008-11-15
OK, will do.
In the meantime, are there any workarounds?  Is my only recourse relabeling the array?

---

### Post by phazonmutant on 2008-11-17
Sorry for the delay.  The bug is submitted to launchpad under the title: "Partitions fail to activate on RAID volumes with complex names"

---

