---
title: "Urgent help needed!"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Tomosaur on 2006-06-29
Right guys, I have a major problem here. I was trying to resize a paritition so I could dual boot windows and ubuntu, and the bloody installer crashed! The hard drive wasn't resized as far as I can see, but now it just says the filesystem is unkown. I can't boot windows now, and ubuntu still isn't installed. I can choose to format my windows partition back to NTFS, but will this actually wipe the partition? I do not have a windows installation cd so I can't afford to lose this partition. Is there any way of getting the computer to reset the filesystem without losing the data on it? Surely all of the data on it should still be stored in the same way as it was before?

Please help!

---

### Post by tonyr on 2006-06-29
I assume you are using the LiveCD to install.  Open a terminal 
(Applications->Accessories->Terminal, type **sudo fdisk -l**,
and post the result here. (That's ELL, not EYE, in the command.)

---

### Post by Tomosaur on 2006-06-29
Here's the output:

```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         790       21174   154110600   82  Linux swap / Solaris
/dev/hda2   *           1         789     5964808+  12  Compaq diagnostics
/dev/hda3           21175       21175        7560   83  Linux
/dev/hda4           21176       21176           0+  83  Linux

Partition table entries are not in disk order
```

---

### Post by rcarring on 2006-06-29
If you reformat the windows partititon (which doesn't appear to be listed above) you will lose all your data.

Right now you have two choices:

a) get a professional disk recover firm to try to retrieve your windows drive
b) buy windows xp and reinstall from scratch

You could try borrowing someone elses xp disk and trying to boot to a recover console as well.

---

### Post by Tomosaur on 2006-06-29
Hmmm tricky. Right now my priority is getting my files back. I guess I'm lucky this happened while I'm out of uni for the summer, and I don't really need the work any more, but I prefer to keep it for a while just in case. I'll try the recover console thing first, hopefully that'll work.

HOWEVER:

Would it be possible for me to create an NTFS formatted partition, then extend it to cover the one which USED to be NTFS but is now nothing? Does that even have a remote possibility of working?

---

### Post by tonyr on 2006-06-29
This shows a list of the partition definitions including partition types.  It looks
to me like the line that shows **/dev/hda1** should probably be your Windows
partition.  The partition type (ID) should be 7 (or 07 or 0x7), which is the  NTFS
type number.  You can try resetting that directly with **fdisk**.  The
following instructions will not change anything on the disk until the last
command (**w**), which writes the changes and exits **fdisk**.  The
only uncertainy here is that the current partition table says that the first
partition, **/dev/hda1**, is currently labeled as ID 82 Linux Swap.  If the
installation got far enough to act on that before it crashed, it may have
formatted that partition.  You would have seen some warning about that,
though, I think.  


In a terminal
**sudo fdisk /dev/hda**

will ask for your password and respond with a short desription and a prompt:
**Command (m for help): **

Enter **m** just to get a look at the commands.  You can look at the partition
table again with command **p**.

Enter command **t**, to change the partition type (id).  The
response should be
**Partition number (1-9):**

Enter 1.  The next response should be 
**Hex code (type L to list codes):**

If you enter **L**  you will see a grid of partition type numbers (id numbers),
and then the **Hex Code** prompt again.  At the Hex Code prompt,
enter 7.  It should respond with an announcement of the changed partition
type and the command prompt.  Enter **p** to examine the partition table
again.  It should show a partition ID of 7 with  System name HPFS/NTFS for /**dev/hda1**.

Write the changed partition table to the disk with the command **w**.
If the Windows partition was truly not affected, you should be able to mount
the partition normally, or even boot into it.

---

