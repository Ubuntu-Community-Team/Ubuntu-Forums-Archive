---
title: "Resizing windows partition"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-22
Ive done this before and it wasnt a problem. Now however its not letting me resize the Windows partition, mounted or unmounted. It currently occupies the whole disk.


I would rather not reinstall the whole thing over again, but I will if I have to. Isnt there an easy way to shrink a Windows partition? I swear Ive done this before and it wasnt this hard.



Could it be a problem with the Mint installer that now asks me if I want to unmount my disks before it goes into install mode? Thats new.


On this PC I would like to have

Windows XP :(
Mint
Ubuntu-Studio
Edubuntu
One of the E17 OSs
Puppy Linux (to create a remix)

I am probably going to put most of the linux partitions on the second laptop drive but I want to install files on a non WIndows NTFS partition.

---

### Post by oldfred on 2010-07-22
Try windows chkdsk on the XP partition.

I had issues with my working XP partition not mounting with gparted. But after I ran chkdsk on the windows partition it then worked in gparted with out issue.

---

### Post by Nick_Jinn on 2010-07-22
So you do or dont want them mounted? The mint installer unmounted everything. Is that the problem?

---

### Post by confused57 on 2010-07-22
> **Nick_Jinn said:**
> So you do or dont want them mounted? The mint installer unmounted everything. Is that the problem?
You want the Window's partition unmounted before resizing.  Try running chkdsk as oldfred suggested & if it still doesn't work, you could try disabling the page file in Windows, then turn it back on after resizing.

---

### Post by Nick_Jinn on 2010-07-22
Calibration failed when I used the check disk option in Gparted.

How do I used the terminal to check a specific hard drive or partition?

---

### Post by oldfred on 2010-07-22
You should use a windows cd to run chkdsk on NTFS partitions.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

### Post by gadolinio on 2010-07-23
> **oldfred said:**
> Try windows chkdsk on the XP partition.

I had issues with my working XP partition not mounting with gparted. But after I ran chkdsk on the windows partition it then worked in gparted with out issue.
This worked for me once.

---

