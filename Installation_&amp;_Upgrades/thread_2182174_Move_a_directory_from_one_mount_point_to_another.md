---
title: "Move a directory from one mount point to another"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Da_Panther on 2013-10-20
Hey everyone, 
I've been trying to find a way around reformatting my hard drive, seeing as I am dual boot and I really don't feel like reinstalling two OS's. 

I have a partition that is basically a twin copy of my root partition that got creaded only God knows how. But it is not being modified to keep track of my live root partition, so I can basically trash that partition. I would resize another partition to use its space, but my partitions are a mess and this particular partition is stuck between two partitions that cannot be moved (BiosGrub and another partition). 

So my question is, how do I relocate a folder from my root partition (e.g. /var or /bin) to this partition, and give it its mount point? I already have my /home folder in its own partition, so I would also like your input as to what folder should be moved to its own partition.

I hope you understand what I am asking, and if you need me to specify anything, don't be shy. 

Thanks!

Here is my partition map btw..


```
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI system partition  boot
 2      210MB   105GB  105GB   hfs+            Untitled
 3      105GB   105GB  1049kB
 4      105GB   117GB  11.7GB  ext4
 7      117GB   117GB  1049kB                                        bios_grub
 5      117GB   127GB  10.2GB  ext4
 6      127GB   131GB  4096MB  linux-swap(v1)
 8      131GB   160GB  29.1GB  ext4
```

partition implicated: number 4

---

### Post by SeijiSensei on 2013-10-20
You'll need to boot into recovery mode to do this properly.  Choose the "root shell" option when offered, then run the command "mount -o rw,remount /" to make the filesystem writable.  Note there is no space after the comma.  You won't need sudo for any of these commands since you have root privileges by default.  Now create the partition; let's suppose it is /dev/sda2.  I would use fdisk for this.  If you are more comfortable with a graphical partitioner like gparted, create the partition in advance before booting into recovery mode.

Now, if you haven't created a file system in /dev/sda2 yet, run "mkfs -t ext4 /dev/sda2".  When it is finished, mount the partition into a temporary location like /mnt.  Then we'll use rsync to transfer the contents of /var to the new location like this:

```

mount /dev/sda2 /mnt
cd /var
rsync -av . /mnt

```

That should copy the contents of /var to /mnt.  When it is done, create an entry in /etc/fstab like the one you created for /home to mount /dev/sda2 as /var.  Reboot.

Other than /boot, /home, and /var, there are not many branches of the filesystem that benefit from separate partitions.  Even /var is a bit suspect.

Ah, I guess you want to use /dev/sda4 for this purpose?  Since it already exists, just format it with mkfs and follow along from there.

---

### Post by Da_Panther on 2013-10-20
I'm going todo one better - complete system reinstall, of both OS's. It will make for a cleaner system. Thanks for the hel

---

### Post by Da_Panther on 2013-10-21
ok, so I change my mind as often as I change boxers.

Once I have copied the contents of my /usr folder to the new partition, do I need to delete the contents of the /usr folder on my root partition? or will this be done automatically when I make /usr my mount point for /dev/sda4 ?

---

### Post by Johan De Cauwer on 2013-10-21
rsync is basically making a copy, so the original data remain were they were. After a reboot the new partition will be used, but you have to take care of the old directory. But why /usr instead of /var? Just to try it out?

---

### Post by Da_Panther on 2013-10-22
Well I am trying to make as much free room as possible on my root partition (I don't have enough room to upgrade to 13.10). I thought that moving /usr would free up more than enough space (over 4gb). 
I got some help on an IRC channel last night and pretty much have my head wrapped around the operation, but me and the persons helping me realized that my system uses UUIDs for my partitions. Meaning, when I boot normally, my partitions show up as /dev/sda# . But I had booted up with an external USB drive and now my drive shows up as /dev/dsb# ... So if I play around in my fstab, will this cause conflicts?


EDIT : after looking over carefully my fstab, if I use the UUID instead of the /dev/sda# as an identifier for the partition in my fstab, then it will respect the necessary protocols for the filesystem to be mounted properly? 
meaning if I do this:
UUID=e9975122-292a-4349-88ea-0652cb45d935 /usr           ext4    defaults        1       2

istead of:
/dev/sda4 /usr       ext4     defaults     1      2

Things should go well right?

---

### Post by Da_Panther on 2013-10-22
So, for those of you who are interested in (or are in s situation they must) move a folder from the root partition to a different partition, here is the walkthrough:

Target partition, moving the /usr folder : 

```
user@computer:/# sudo -i           (or your favourite method of superuser)
root@computer:/# mkfs.[filesystem] /dev/hda#         (formats your filesystem, replace [filesystem] by your type to be used, e.g. ext4)
root@computer:/# mount -rw /dev/hda# /mnt          (mounts the newly formatted partition at mount point /mnt)
root@computer:/# cd /usr ; tar cpsf /mnt/file.tar .     (makes a tar archive, while keeping permissions, of the /usr directory, and places it in /mnt)
root@computer:/# cd /mnt ; tar xf file.tar      (decompresses your tar file in /mnt, hence your new partition)
```

Now the files are copied to their new partition, and permissions are kept as they were in the root partition.
Now what is left to do is add your partition to fstab with its proper settings. Open it in your favourite text editor, as root.

I came across a little particularity, which I figured out how to get around. I was hoping it would be as easy as adding the following line:
```
/dev/hda# /usr ext4 defaults 0 2
```

but when I opened up my fstab, I saw that my fstab uses unique identifiers (UUIDs). Don't panic - go in a shell:
```
root@computer:/# blkid         (run this as root, it will print the UUIDs for all partitions it can detect)
/dev/sda1: LABEL="EFI" UUID="2860-11F4" TYPE="vfat" 
/dev/sda2: UUID="1a2db651-459c-3325-8bde-3bb0b8040621" LABEL="Macintosh HD" TYPE="hfsplus" 
/dev/sda4: UUID="71ae1341-0f3f-4ae7-bc19-495a96884309" TYPE="ext4" 
/dev/sda5: UUID="dbd97dee-588f-4703-a153-3417e10cb5e8" TYPE="ext4" 
/dev/sda6: UUID="6a43fcf8-67c6-48bb-a8bc-b45785535bd6" TYPE="swap" 
/dev/sda8: UUID="e9975122-292a-4349-88ea-0652cb45d935" TYPE="ext4" 
```

Find your target partition, and replace the /dev/sda# you were going to use with its UUID. Problem solved.
Save your fstab, then reboot. Make sure everything works properly.

Once everything works properly, you can boot up with a live session disk or USB key, and then mount the root partition containing your "old" folder, the one you want to move. As a precaution before deleting, I moved everything into a subfolder (instead of having the /usr subfolders in their place, I moved them to a new folder /usr/old). I rebooted to make sure everything still worked, and it did, so I went back and erased the old folder completely. 

I do not guarantee this is foolproof, or safe, or recommended, and I have very big doubts as to what kind of damage you could do to your system if you follow this walkthrough. However, it worked for me, and it allowed me to free up some space on my root partition and reuse an old partition that was lost unused space. 

If anybody wants to improve on this, please go ahead!!

---

