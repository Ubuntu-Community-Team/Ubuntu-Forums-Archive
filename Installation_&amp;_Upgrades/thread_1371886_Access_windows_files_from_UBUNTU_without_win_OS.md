---
title: "Access windows files from UBUNTU without win OS"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by paddydd on 2010-01-03
Hi,
  I have a P4 with windows on it and I want to convert it to Linux-UBUNTU.
I would like to preserve many of the files on the system the bulk of which are on a large secondary disk (DRIVE K:) - This is a 320GB file system. The smaller disk is 157GB - drive C: which contains the windows os.

  I want to put UBUNTU onto the disk that contains the windows os -- that would be drive c:. If I setup UBUNTU to use only the first disk will I be able to access in any way the files on the K drive.

Thanks
Paddy

---

### Post by Marrkk on 2010-01-03
Hi Paddy, and Happy new year mate.
Yes, there should be no problems at all,
suggestions:

 - if you're new to partitioning, i really recommend just unplugging the power lead from the hard drive with all the goodies on it while installing Ubuntu. or whatever system. better safe thn sorry.
you probably will need to enter a password when you want to access the drive, once ubuntu is running. no biggie tho.
you will need the windows codecs too, so you will most likely need to install (in synaptic) 'ubuntu restricted extras' or maybe even enable the MEDIBUNTU repository too - to be able to watch the videos :)
Mark

---

### Post by drs305 on 2010-01-03
Yes you will be able to access them. There is a package called ntfs-config which can easily set up your system to mount and read NTFS partitions. 

Just be careful during the Ubuntu install not to select and format that drive - as long as you don't opt to use that disk and don't select it as one of the install partitions your data should be safe.

If you are really concerned, you can always unplug your data drive to ensure both it isn't overwritten or deleted during the install, and also to prevent any system files from mistakenly being placed on a data drive.

---

### Post by paddydd on 2010-01-04
Thanks for your replies.

The issue is that the hard drive is very difficult if not impossible to unplug and then plug back in and a pain to get at and remove. I can remove it if needed but the question is will the UBUNTU installer care about drive sdb if it is installing on drive sda? How can I be sure that sdb is left alone at install time -- short of unplugging it.

Thanks again,
Paddy

---

### Post by drs305 on 2010-01-04
I don't advocate unplugging it - it's just an option that paranoid users might use.  ;-)

The Ubuntu installation disk will ask you where you want to install it. Where it is going to be installed should be fairly clear. Just make sure you have the correct drive designated. There will be a graphic so you can check the size of the install drive to make sure you are dealing with the correct one.

If you get to Step 4 of the installation (drive/partition selection) and don't understand it, just step back and ask on the forum. In this case, a snapshot of what you are looking at would be very helpful.

---

### Post by K.J. on 2010-01-04
It *should* by default ignore the drive unless you **choose** to reformat it. It's fairly straight forward and it should be obvious if it's being reformatted before the format is actually done.

Although, as a warning, while you can use NTFS drives in Ubuntu, it can be problematic. You'll want to make sure that you have an XP CD handy for running checkdisk on the drive. NTFS-3G needs the -f (force) to mount a drive flagged as unclean, and sometimes can't unmount it all.

I would see if someone has an external drive you can borrow long enough to copy the data off and reformat your drive to ext3 or reiserfs.

---

### Post by paddydd on 2010-01-04
Hi,
  Thanks for all of your help. It worked! I have Linux on sda and the NTFS windows stuff on sdb and I can see it just fine. I did not need to load any packages. Synaptic shows something called ntfs-3g and the comments says it can read and write NTFS for FUSE.

Thanks once more.

Paddy

[Solved]

---

