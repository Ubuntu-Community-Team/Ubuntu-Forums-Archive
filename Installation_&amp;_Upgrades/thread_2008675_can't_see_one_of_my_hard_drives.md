---
title: "can't see one of my hard drives"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by willis11of12 on 2012-06-23
I upgraded to 12.04 LTS about a month ago and have had a lot of problems since then, mostly with vino-server crashing all the time, which I seriously need for remote access.  So I decided to install 10.04 LTS (where vino server didn't always crash on me), on a separate hard drive.  

Now when I boot up the hard drive with 12.04 first, I can see the other hard drive and access the files just fine, but when I boot from the hard drive with 10.04 on it, I can't see anything from the other hard drive!  Is 12.04 formatted differently so that I can't see any of the files if I am using 10.04 as my OS?  Is there any way to access those files when I am using the 10.04?

---

### Post by dino99 on 2012-06-23
what did you mean by "not seeing" ?
are you talking about the "grub menu" or gparted or nautilus or ... ?

how is your install made ?

---

### Post by darkod on 2012-06-23
We are talking about proper ubuntu installations in both cases, right? One of them is not wubi or something?

All partitions/folders from the current installation should be under Filesystem when you look in Nautilus (the file browser).

All other partitions, linux and ntfs, should be in the left side menu in Nautilus and you should be able to open them by clicking on them.

To double check that all disks and partitions are recognized, you can also try in terminal:
```
sudo fdisk -l
```

---

### Post by willis11of12 on 2012-06-24
> **dino99 said:**
> what did you mean by "not seeing" ?
are you talking about the "grub menu" or gparted or nautilus or ... ?

how is your install made ?

I mean when I am using nautilus.  When I am using 12.04, I do see the 120gig Hard Drive listed on the left side, separate from the file system, but when I boot from the 120gig hard drive (using 10.04) I do not see my 1000gig hard drive.

I installed 12.04 from doing an update and then I installed 10.04 on the smaller hard drive using a CD of a recently downloaded disk image for 10.04 LTS.  I'm not sure if this is important to note or not, but I believe I disconnected the 1000gig hard drive and connected the 120gig hard drive when I went to install the 10.04 on the 120gig HD.

---

### Post by willis11of12 on 2012-06-24
> **darkod said:**
> We are talking about proper ubuntu installations in both cases, right? One of them is not wubi or something?

All partitions/folders from the current installation should be under Filesystem when you look in Nautilus (the file browser).

All other partitions, linux and ntfs, should be in the left side menu in Nautilus and you should be able to open them by clicking on them.

To double check that all disks and partitions are recognized, you can also try in terminal:
```
sudo fdisk -l
```

I'm not sure what wubi is, but yes, I believe I am using proper ubuntu installations.

I'm not sure why I don't see the other hard drive when I'm booting from the one using 10.04, but when I boot from the hard drive using 12.04 I do see the other one listed on the left as you say.  I used the command you suggested in the terminal and it shows up as being there, but not when I open nautilus.  here is the print out when I do that:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009acf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120102   964711424   83  Linux
/dev/sda2          120102      121602    12048385    5  Extended
/dev/sda5          120102      121602    12048384   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b699

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112412672   83  Linux
/dev/sdb2           13995       14594     4805633    5  Extended
/dev/sdb5           13995       14594     4805632   82  Linux swap / Solaris


Any suggestions about getting it to show up in nautilus like they do when I boot from the 1000gig hard drive?  If not, can I use the terminal to copy files from that hard drive to the other and then see the files?

---

### Post by darkod on 2012-06-24
It should be in Nautilus in the left side menu. It should list all present partitions.

But if you are talking about mounted partitions, that is different.

To make sure, from both systems. post the output of:
```
cat /etc/fstab
```

Do that from both so we can see what is mounted at boot.

Otherwise, yes, there should be an easy way to mount it and copy files to/from it. Lets see what fstab says first.

---

### Post by willis11of12 on 2012-06-24
Okay, here it is from the 120 HD with 10.04 running and then I'll boot from the other and post that one next...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aea24586-9e1b-4317-ad99-dc36705acc5c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by willis11of12 on 2012-06-24
And now here is what I see when I use that command booting from the larger HD with 12.04 as the OS:


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d9960483-055e-48db-bdef-28e7f37975d9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4babbc92-1aa8-4d6a-ba36-dc66f0d383a1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by darkod on 2012-06-24
> **willis11of12 said:**
> Okay, here it is from the 120 HD with 10.04 running and then I'll boot from the other and post that one next...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sda1[/COLOR]       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aea24586-9e1b-4317-ad99-dc36705acc5c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I think this is your issue. In the fstab of 10.04 you have /dev/sda1 instead of the UUID of the partition (compare it with the fstab of the 12.04 where the UUID for the root partition is used).

Boot the 10.04 and check the UUID of the root partition with:
```
sudo blkid
```

After that open /etc/fstab and change the /dev/sda1 with UUID=<the UUID string>. Save and close the /etc/fstab. Restart and boot into the 10.04 again. Did it help?

It should help using the UUID since it seems the disks are changing the /dev/sda and /dev/sdb names between them.

---

### Post by willis11of12 on 2012-06-24
It's not letting me type anything into that file.  I'm guessing I don't have permission and I don't remember how to make myself have permission to write on a file.

---

### Post by willis11of12 on 2012-06-24
I just tried this but it didn't work:

chmod u+x,g+x,o+x /etc/fstab
chmod: changing permissions of `/etc/fstab': Operation not permitted


Do I need to go that that folder first and then do the above?  Now I need to figure out how to change folders in terminal again.  :)

---

### Post by willis11of12 on 2012-06-24
Okay, I've really gotta run now or my wife is going to kill me, but here is what I just tried to do to give myself permission to change the file, but it still says only root has permission, so what am I doing wrong?  thanks in advance!

willis@willis-desktop:/$ cd /etc/
willis@willis-desktop:/etc$ chmod u+x,g+x,o+x /etc/fstab
chmod: changing permissions of `/etc/fstab': Operation not permitted
willis@willis-desktop:/etc$ chmod u+x,g+x,o+x fstab
chmod: changing permissions of `fstab': Operation not permitted
willis@willis-desktop:/etc$ sudo chmod u+x,g+x,o+x fstab
[sudo] password for willis: 
willis@willis-desktop:/etc$ sudo chmod u+x,g+x,o+x fstab
willis@willis-desktop:/etc$ sudo chmod u+x,g+x,o+x fstab
willis@willis-desktop:/etc$

---

### Post by darkod on 2012-06-24
You just needed to open it for editing with root permissions, using sudo.

For example, if you edit text files with gedit, you would open it with:
```
gksu gedit /etc/fstab
```

Be careful touching permissions of /etc/fstab, don't mess it up.

To run any command with root permissions simply type sudo in front of it. If the program is graphical, like the gedit editor, it's better to use gksu instead of sudo, the effect is the same.

That would open /etc/fstab for editing, you can edit it, save it and close it.

---

### Post by willis11of12 on 2012-06-24
Thanks, that allowed me to edit and save the file, but it still isn't showing up in nautilus, even after restarting the computer.  :(  I did not use the quote marks around what UUID equaled, since the other UUID in fstab didn't have it either, but was I supposed to?  Here is what I see when using blkid:

/dev/sda1: UUID="d9960483-055e-48db-bdef-28e7f37975d9" TYPE="ext4" 
/dev/sda5: UUID="4babbc92-1aa8-4d6a-ba36-dc66f0d383a1" TYPE="swap" 
/dev/sdb1: UUID="3367114a-2be5-4a13-965a-8eed765488ee" TYPE="ext4" 
/dev/sdb5: UUID="aea24586-9e1b-4317-ad99-dc36705acc5c" TYPE="swap" 

So in fstab, I replaced "dev/sda1" with "UUID=d9960483-055e-48db-bdef-28e7f37975d9", so is that what you were saying?  Was I supposed to use the quotes or include the TYPE="ext4"at the end in fstab?  Please let me know if I made a mistake, or if I should try something else.

And sorry for the noob question, but is this a problem with the larger HD being mounted in one OS, bot not the other?  Just wondering if I need to mount it in 10.04 maybe?  Again, my apologies if I totally misunderstanding this.  :)

---

### Post by darkod on 2012-06-25
It looks correct without the quotes since there are no quotes in fstab, but I wanted to try the other UUID, the UUID="3367114a-2be5-4a13-965a-8eed765488ee".

Yes, I said replace /dev/sda1 but you have to watch out and compare the UUIDs and the disks. As I mentioned, sda and sdb seem to be changing places so what was sda1 when 10.04 was installed is now sdb1 after the other disk was added. That's why grub2 uses UUID to avoid errors when disks are added or removed.

In your fstab of 10.04 compare the UUID of the swap partition. It's the one for sdb5, not sda5. So, for the root of 10.04 you would use the UUID of sdb1, not sda1.

If all of that made sense. :)

I think with the above UUID it will work.

On another note, how are you dual booting? Are you using only one grub2 boot menu selecting what OS to boot, or you are changing with BIOS to boot one or the other disk depending what OS you want?

Because if you change the boot order in BIOS that can change the sda, sdb naming of the disks, their order. But all of this doesn't matter anyway if using UUID in fstab.

---

### Post by willis11of12 on 2012-06-25
> **darkod said:**
> It looks correct without the quotes since there are no quotes in fstab, but I wanted to try the other UUID, the UUID="3367114a-2be5-4a13-965a-8eed765488ee".

Yes, I said replace /dev/sda1 but you have to watch out and compare the UUIDs and the disks. As I mentioned, sda and sdb seem to be changing places so what was sda1 when 10.04 was installed is now sdb1 after the other disk was added. That's why grub2 uses UUID to avoid errors when disks are added or removed.

In your fstab of 10.04 compare the UUID of the swap partition. It's the one for sdb5, not sda5. So, for the root of 10.04 you would use the UUID of sdb1, not sda1.

If all of that made sense. :)

I think with the above UUID it will work.

On another note, how are you dual booting? Are you using only one grub2 boot menu selecting what OS to boot, or you are changing with BIOS to boot one or the other disk depending what OS you want?

Because if you change the boot order in BIOS that can change the sda, sdb naming of the disks, their order. But all of this doesn't matter anyway if using UUID in fstab.

Hey hey!  That worked, and I was able to see it without restarting as well!  Though it seems to be responding a bit slower than normal.  Hopefully that will improve after I restart it.

The reason I am using both is because I figure 12.04 being newer is probably better for most things (maybe just me being a noob and thinking newer means better), but since I will be out of town for a few days coming up, I needed to make sure vino-server would be reliable and it isn't currently in 12.04.  So I didn't want to get rid of everything being setup on 12.04, but need to be able to do things on 10.04 for at least a little while, until I can find a better solution on 12.04, or Ubuntu fixes whatever keeps causing vino-server to crash in 12.04.  Any thoughts on that?

As to how I am booting, I have to hit F12 when I restart my computer to select which hard drive to boot first and that decides which OS it runs.  I tried doing it in what I think is the bios, but I only saw the order of things to boot first, second, third, and hard drive being one of them, but I didn't see it asking which hard drive to boot first unless I use F12 instead to select which drive to boot first.  Maybe there is a way to do it in bios and I'm just not educated enough about how to use it, that's actually very likely.  :)  Also, if I don't hit F12 each time I restart and select the smaller HD, it will always boot to 12.04 on the larger HD, even if I restarted from 10.04...  I'm not sure why that is, but it is.

---

### Post by willis11of12 on 2012-06-25
By the way, I just wanted to say I really appreciate all your help!  Thanks!!

---

### Post by darkod on 2012-06-25
No problem.

Booting with F12 will do its job, but if you can find the setting for configuring the HDD order, you can consider booting with the 12.04 hdd first always. In its boot menu you will have the option for 10.04 too. In most newer boards (last few years or so) there are two different settings: one is for devices, like you say, for cd-rom, hdd, usb, etc. But as people started using more and more multiple disks the manufacturers started implementing one more setting which lists the HDDs in which order you want them to be tried for a bootloader.

Or you can continue selecting the disk with F12. Whet ever works best for you.

If you consider the thread resolved please mark it as Solved. You can do that in Thread Tools above the first post.

---

### Post by willis11of12 on 2012-06-25
BYW, I just looked a little closer and found that the bios does have a place for me to select which drive to boot from by default, so I made that switch.  I have noticed that since I switched to using 10.04 over the weekend that my time keeps drifting off and causing problems for my time sensitive apps as my clock falls behind that of the servers I am connecting to!  I found where to set up syncronizing the clock, but according to what I just read, it looks like even than, it only does so once a day, and I'm not sure if that will be good enough with as fast as the time was drifting before I synced the time...  I guess I'll see as the day goes on if I have to manually correct the time again like I kept having to do before the sync.

---

### Post by willis11of12 on 2012-06-25
> **darkod said:**
> No problem.

Booting with F12 will do its job, but if you can find the setting for configuring the HDD order, you can consider booting with the 12.04 hdd first always. In its boot menu you will have the option for 10.04 too. In most newer boards (last few years or so) there are two different settings: one is for devices, like you say, for cd-rom, hdd, usb, etc. But as people started using more and more multiple disks the manufacturers started implementing one more setting which lists the HDDs in which order you want them to be tried for a bootloader.

Or you can continue selecting the disk with F12. Whet ever works best for you.

If you consider the thread resolved please mark it as Solved. You can do that in Thread Tools above the first post.

Okay, I will mark it solved.  Thanks!

---

