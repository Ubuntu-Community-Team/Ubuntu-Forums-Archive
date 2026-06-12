---
title: "Dual Boot Trouble (Newbie)"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by mwh2ooo on 2008-05-22
Hi, this is my first post. I'm a completely new to Linux, so I appreciate any help.  I have a Dell e1505.  I partitioned my hard drive into 3 partitions (through my windows install), one for Windows (~40gb), one for data (~10gb) and one for Linux (~50gb).  I installed windows media center first, then installed ubuntu 8.04LTS Desktop.  Under the Ubuntu install, I reformatted the Linux partition into 2.  One for swap that is 4gb and root that is the rest (in ext3 format).

When I get to the Grub menu, windows doesn't show up as an option.  Here is what I saw I lot of people posting:

michael@michael-laptop:~$ sudo fdisk -l

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     4000153+  82  Linux swap / Solaris
/dev/sda2   *        6375       10581    33792727+   7  HPFS/NTFS
/dev/sda3           10582       11977    11213370    f  W95 Ext'd (LBA)
/dev/sda4             499        6374    47198970   83  Linux
/dev/sda5           10582       11977    11213338+   7  HPFS/NTFS

I have tried editing the grub menu, but to no avail.  I'm not really completely sure how to edit, but there was no windows option in the grub list file.

I really appreciate any help, thanks in advance.

---

### Post by meierfra. on 2008-05-22
Did you try:

title Window XP
root (hd0,1)
chainloader +1

for your windows item?


What kind of error messages did you get when you tried to boot Windows?

Does the grub menu appear at boot up?
If not change "timeout 3" to "timeout 10" and "hiddenmenu" to "#hiddenmenu" in menu.lst

What used to be  in the space which is now occupied by swap? 

Post your boot.ini:

```
sudo mkdir /Windows
sudo mount -t ntfs /dev/sda2 /Windows
cat /Windows/boot.ini 
```

---

### Post by mwh2ooo on 2008-05-22
The GRUB menu comes up.  The error I get with that setup in GRUB is "NTLDR is missing."

The swap used to be a partition I created under the windows installer.  I made one 50 gig partition with windows. Then in the linux install, deleted that partition and used the free space to make swap and the root partition.

I tried the boot commands, but there is no boot.init.  This probably seems silly?  Am I supposed to have a boot file in windows?  I apologize if this is some simple mistake; I'm still very much a beginner.

Also, is there something I need to do to unmount the partition? Thanks a lot for your help thus far.

---

### Post by meierfra. on 2008-05-22
Its boot.ini (not boot.init)  .

---

### Post by mwh2ooo on 2008-05-22
Sorry, typo when I was posting, but I entered it correctly in terminal.

---

### Post by meierfra. on 2008-05-22
> Am I supposed to have a boot file in windows? 

Yes, grub cannot boot Windows by itself. Grub just turns the control over to the windows partition.

---

### Post by meierfra. on 2008-05-22
I'm afraid that the booting information for XP was on the partition you deleted. This link might help you to fix the problem:

[http://support.microsoft.com/?kbid=922809&sd=RMVP]("http://support.microsoft.com/?kbid=922809&sd=RMVP")

---

### Post by mwh2ooo on 2008-05-22
When I installed ubuntu did I mess up my windows partition or is there a place where I can download a new boot.ini?

---

### Post by meierfra. on 2008-05-22
Actually before you do that you might try to locate boot.ini by double clicking on the icon for the Windows partition in "Computer->Places".

---

### Post by meierfra. on 2008-05-22
> When I installed ubuntu did I mess up my windows partition or is there a place where I can download a new boot.ini?

boot.ini itself isn't really the problems (you could recreate it yourself).But there are other boot files which probably are also missing "ntldr" is one of them. They are available  on the web. I would find a link for you, but I'm out of time right now. I'll check back tomorrow.

---

### Post by mwh2ooo on 2008-05-23
Yeah, I did I search on that partition and nothing was found.

Okay.  I just did a fixboot through the windows recovery console.  Should it be using root hd(0,2) in GRUB? When I tried that with the fresh boot files and hd(0,2), I get "Starting up..." and then nothing happens.

This time I added the line makeactive to the GRUB list.  Now I get "error 12: Invalid device requested."

---

### Post by meierfra. on 2008-05-23
> Should it be using root hd(0,2) in GRUB? 
No, it needs to be "root (hd0,1)" Grub starts counting at 0. So (hd0,1) is the second partition on the first hard drive.


Here is  page which has the missing files and also helps you rebuild your "boot.ini":

[http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")

---

### Post by mwh2ooo on 2008-05-23
I reinstalled Windows then Ubuntu (through the live version) and GRUB was fine.  Thanks so much for all the help.

---

