---
title: "Backing up an entire hard drive and restoring to a different drive"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by tylersontag on 2011-05-09
So i just recently did a fresh install of Ubuntu 11.04 and just got done getting everything setup back to the way i like it.  About that same time i saw an advertisement for a SSD that i couldn't afford not to buy.

Now, i could just do a fresh install again, i've got everything backed up from the last time, but i wanted to use this as an opportunity to test out some data recovery plans.

I had always heard, one could just TAR up the root directory to a backup location then copy that back out to a new drive to effectively ghost ones hard drive.  Is this actually possible?  Am i going to have any massive problems having the same virtual drive information on a physically different drive?

Does anyone know of any guides that could give me a better idea of the process and its limitations?

---

### Post by Paddy Landau on 2011-05-09
Unlike, say, Windows, Linux is a bunch of files. No Registry or anything like that.

So, yes, it's possible to just copy the files from one drive to another.

Start by partitioning your SSD in the same way as you had your original drive.

If you have both drives connected to the same computer at the same time, simply enter this command:
```
sudo cp --archive / /path/to/mounted/SSD
```If you have multiple partitions (ignoring swap), you need to repeat this process for each partition; e.g.
```
sudo cp --archive /home /parth/to/mounted/SSDhome
```However, if the drives are not connected to the same computer at the same time, you have two choices.

[LIST=1]
[*]Use tar to create a massive file (one for each partition) and then uncompress that onto your SSD. However, this is very slow.
[*]Use a ghosting program.
[/LIST]
I strongly recommend that you use [CloneZilla]("http://www.clonezilla.org/") to ghost your machine. I have successfully backed up and restored both Windows and Ubuntu with this method.

CloneZilla is the best free ghosting program that I know of. It's not the easiest to understand when you first use it, but it is straightforward and it works.

You can use CloneZilla to back up and restore your entire drive, or do each partition separately -- whichever you prefer.

If you do the entire drive, I believe CloneZilla will partition your new drive for you. Otherwise, each receiving partition must of course be as large as, or larger than, the original respective partition.

Good luck.

---

### Post by Paddy Landau on 2011-05-09
I've just realised that when you restore the partitions, your file /etc/fstab may need adjusting before you can boot. You would have to do that with a Live CD.

---

### Post by tylersontag on 2011-05-09
Thanks for that clone information, that should help alot.  I was planning on backing up over my network overnight then hooking the new drive to my server and flashing it back to there.  But i might read up on Clonezilla some

i think that was most of my question, regarding the fstab directory or anything that would have data specific to the actual drive.  So once i boot up to the live disk, will i just need to edit the fstab file myself?  Is there any documentation on what i need to change it to?

---

### Post by Paddy Landau on 2011-05-10
You can find [documentation on fstab]("https://help.ubuntu.com/community/Fstab"), or Google it.

The important point is how Ubuntu finds your disks. The file /etc/fstab specifies where to find each disk, and how to mount (access) it.

By default, each disk is identified by a Universally Unique Identifier (UUID). You'll see something like the following at the start of two or more lines.
```
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8
```Every partition has a unique UUID.

You can prepare for your transfer by giving each partition a *label*, i.e. a name. Make the names identical on your original and target disk.

Here is how to do so:

Using a Live CD, find the file /etc/fstab on your home partition. **Make a backup of it** (copy it to, say, /etc/fstab-2011-05-10).

Still using your Live CD, open either GParted or Disk Utility. Ensure you give every partition a name; I will use the names [FONT=Courier New]ubuntu[/FONT] for your root partition, [FONT=Courier New]home[/FONT] for your home partition, and [FONT=Courier New]swap[/FONT] for your swap partition. You can choose different names. Note that I have used all lowercase to be consistent with typical Linux conventions.

If you don't have a separate home partition, you will change only the root and swap partitions.

If you have any other partitions, you might want to check with us before you proceed.

Still using your Live CD, edit your /etc/fstab (the one in your 'ubuntu' partition, not the one on your Live CD), replacing each UUID=... with LABEL=...

For example, find the following three lines (identify them by the second item in the row, being [FONT=Courier New]/[/FONT] for root, [FONT=Courier New]/home[/FONT] for home and [FONT=Courier New]none swap[/FONT] for swap):
```
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8  /      ext4  errors=remount-ro  0  1
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90  /home  ext4  defaults           0  2
UUID=413eee0c-61ff-4cb7-a299-89d12b075093  none   swap  sw                 0  0
```Replace the UUDI= with LABEL= as follows.
```
LABEL=ubuntu  /      ext4  errors=remount-ro  0  1
LABEL=home    /home  ext4  defaults           0  2
LABEL=swap    none   swap  sw                 0  0
```If you don't have a separate home partition, you will have only two lines to change.

If you have any other lines with UUID= on it, post them here so that we can help you make that change.

Finally, check that you can still boot normally. If not, use your Live CD to check your /etc/fstab for errors; if you cannot get it right, restore it from the backup that I asked you to make, and post back here.

---

