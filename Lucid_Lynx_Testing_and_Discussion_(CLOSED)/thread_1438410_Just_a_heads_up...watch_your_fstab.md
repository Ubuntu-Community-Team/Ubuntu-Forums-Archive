---
title: "Just a heads up...watch your fstab"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Anduu on 2010-03-25
If your like me and like your partitions mounted a certain way and modify your fstab,this latest kernel update left my system unbootable.It seems kernel 2.6.32-7 has changed the way it handles things.

My old fstab:
```
UUID=12d33a6e-c3de-4463-8e39-b26272cbccfe / ext3 defaults 0 1
UUID=9629a967-dd4e-48aa-9f0b-9e53eb9f5ddd /home ext3 defaults 0 2
UUID=438555c3-d8c0-4577-95dc-ced04d563670 swap swap sw 0 0
UUID=95020a66-0411-4ea6-90cc-c47bf385afe7 /media/TempBackup ext3 defaults 0 0
/dev/sda1 /media/XP ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sda2 /media/Vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0
[COLOR="Red"]/dev/sdb1 /media/500GB\040SATA2 ntfs-3g defaults,locale=en_CA.UTF-8 0 0[/COLOR]
/dev/sde1 /media/FreeAgent\040Drive ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sr0 /media/cdrom0 udf,iso9660 users,auto,exec 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 users,auto,exec 0 0
```

My new fstab with modifications I had to make to get my system up again:
```
UUID=12d33a6e-c3de-4463-8e39-b26272cbccfe	/	ext3	defaults	0	1
UUID=9629a967-dd4e-48aa-9f0b-9e53eb9f5ddd	/home	ext3	defaults	0	2
UUID=24440C85440C5C44	/media/500GB_SATA2	ntfs-3g	defaults,locale=en_CA.utf8	0	0
UUID=848C46548C4640C2	/media/FreeAgent\040Drive_	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf8	0	0
UUID=DED886A5D8867B91	/media/Vista	ntfs-3g	defaults,locale=en_CA.utf8	0	0
UUID=BC886F48886EFFEE	/media/XP	ntfs-3g	defaults,locale=en_CA.utf8	0	0
UUID=438555c3-d8c0-4577-95dc-ced04d563670	swap	swap	sw	0	0
[COLOR="Red"]/dev/sdb1 /media/TempBackup ext3 defaults 0 0[/COLOR]
```

Notice the entries in red.Under the 2.6.32-16 kernel sdb1 was the 500GB ntfs drive.With 2.6.32-17 sdb1 is now the 100GB ext3 drive.

The result of the ext3 drive attempting to mount as ntfs was a chain reaction of errors which brought my system to it's knees.

Hopefully this may help someone who finds themselves in my position.It took me a couple days of hair pulling and gnashing of teeth to sort this out. ](*,)

---

### Post by Longinus00 on 2010-03-25
This is why you should be using UUIDs instead of depending on in what order the kernel finds drives (which is by no means certain).

---

### Post by Anduu on 2010-03-25
> **Longinus00 said:**
> This is why you should be using UUIDs instead of depending on in what order the kernel finds drives (which is by no means certain).

In my four years with Linux this is the first time I have ever had an issue :-k

---

### Post by autocrosser on 2010-03-25
I remember when UUID was first phased in there were a ton of problems if you used /dev/sdx for your fstab--I converted to UUID a couple of years ago & it looks like you could benefit by doing so also.....I know that it's more of a pain to use them, but it's easier in the long run......I've used linux for 8+ years now & making the switch was hard for me---I was use to re-writing my fstab as I needed to.

---

### Post by Irihapeti on 2010-03-25
UUIDs don't currently work in Lucid kernels. There's a bug report filed. I think a fix has been done, but it hasn't made its way to the repo kernels yet. (Just tried with 2.6.32-17 kernel.)

---

### Post by dcstar on 2010-03-25
> **Irihapeti said:**
> UUIDs don't currently work in Lucid kernels. There's a bug report filed. I think a fix has been done, but it hasn't made its way to the repo kernels yet. (Just tried with 2.6.32-17 kernel.)

So the UUIDs that were installed and work in my 10.04 fstab file are somehow impersonating something that does work?

---

### Post by dcstar on 2010-03-25
> **Longinus00 said:**
> This is why you should be using UUIDs instead of depending on in what order the kernel finds drives (which is by no means certain).

Especially when people put removable drives in their fstab files.

Even using partition labels means mounts are more certain that relying on arbitrary /dev/sd tags.

---

### Post by Irihapeti on 2010-03-25
> **dcstar said:**
> So the UUIDs that were installed and work in my 10.04 fstab file are somehow impersonating something that does work?

I don't know what's happening in your case. I do know that there's a bug report filed and they don't work for some people. I'm one of them.

---

### Post by Anduu on 2010-03-25
I have been meaning to move everything over to UUID's...just never got around to it.

Guess this was kick in the pants I needed ;)

---

### Post by kansasnoob on 2010-03-25
> **Irihapeti said:**
> UUIDs don't currently work in Lucid kernels. There's a bug report filed. I think a fix has been done, but it hasn't made its way to the repo kernels yet. (Just tried with 2.6.32-17 kernel.)

Where do you get such an idea?

Look at mine:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / is on /dev/sda2
UUID=91760bb5-455b-4adc-8e34-a8f2d5cae023 /               ext3    errors=remount-ro 0       1
# /home is on /dev/sda10
UUID=3128dea7-b986-4b45-8004-0b48bf97f9dd /home           ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda6       ext3    defaults          0       2
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda8       ext3    defaults          0       2
#/dev/sda9    /mnt/sda9 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda9       ext3    defaults          0       2
# swap is on /dev/sda5
UUID=58aec1b2-6dfe-4f02-b77d-207fe6cc5551 none            swap    sw                0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

You can see that I mount 4 partitions with their UUID. Furthermore I symlink them from my home folder.

---

### Post by Irihapeti on 2010-03-25
> **kansasnoob said:**
> Where do you get such an idea?

 

Here: [https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027](https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027)

It also affects Lucid.

Evidently not everyone, which I wasn't aware of.

---

### Post by Longinus00 on 2010-03-25
> **Irihapeti said:**
> Here: [https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027](https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027)

It also affects Lucid.

Evidently not everyone, which I wasn't aware of.

The bug you quote says that it's fixed in lucid (and likely has been for some time). UUID has been the default for some time now so if it stopped working most people wouldn't be able to boot.

---

### Post by VMC on 2010-03-25
Once I switched to UUID's I have never had an issue. And never looked back.

Come to think of it, that(UUID) was the "button" discussion of its day :)

---

### Post by anaconda on 2010-03-25
Actually people have often problems with mounting  
swap partition using UUID:s
The problem is ofcourse that UUID changes when reformatted, and swap partition is sometimes reformatted.. eg. when installing another linux on a different partition.

So that is why I prefer to point to swap partitions the old way
/dev/sda4 
instead of using UUID for it..

---

### Post by autocrosser on 2010-03-25
> **VMC said:**
> Once I switched to UUID's I have never had an issue. And never looked back.

Come to think of it, that(UUID) was the "button" discussion of its day :)

Yes--I remember the topic was quite heated---just like Pulseaudio is now......the flame topic of the day......:D

---

### Post by dino99 on 2010-03-25
Hello guys,

i'm lucky on my end, no issues, but i never found a script or else to build or reconfigure fstab in a clean ubuntu standard.
If someone knows about such a command, let me know.

---

### Post by seeker5528 on 2010-03-25
> **dino99 said:**
> Hello guys,

i'm lucky on my end, no issues, but i never found a script or else to build or reconfigure fstab in a clean ubuntu standard.
If someone knows about such a command, let me know.

Would the program in the attached screenshot cover the "or else"?

Later, Seeker

---

### Post by wkulecz on 2010-03-25
> instead of depending on in what order the kernel finds drives (which is by no means certain)

But the drive order should be certain.  UUIDs cause havoc if you are unfortunate enough to have to restore your system from backups.

UUIDs at least don't suffer from the name collisions of by Label mounts.  But I fail to see any advantage of a non 1 to 1 mapping of ports and the attached hardware.  Pretending IDE devices are sd devices is just plain confusing.  If I want it to be accessed as an sd device I'd use a SATA adaptor.

---

### Post by coffeecat on 2010-03-25
> **anaconda said:**
> The problem is ofcourse that UUID changes when reformatted, and swap partition is sometimes reformatted.. eg. when installing another linux on a different partition.

Extraordinary, isn't it? Why on Earth would an installer need to reformat a pre-existing swap partition? The Ubuntu installer doesn't, although it says it will. But then another distro's installer (openSUSE iirc) doesn't say anything but goes ahead and causes havoc by reformatting the swap partition. I wonder what the (Suse?) devs were putting in their cocoa when they thought that one up. :rolleyes:

---

### Post by dino99 on 2010-03-25
> **seeker5528 said:**
> Would the program in the attached screenshot cover the "or else"?

Later, Seeker

Thanks, i search something to repair broken fstab.

---

### Post by markbuntu on 2010-03-26
It has been my experience that the ubuntu installer changes the uuid of any swap partition it comes across. If you have multiple hds with multiple partitions and multiple distros the fstab uuid scheme can deteriorate fairly rapidly.

---

### Post by coffeecat on 2010-03-26
> **markbuntu said:**
> It has been my experience that the ubuntu  installer changes the uuid of any swap partition it comes across. If you  have multiple hds with multiple partitions and multiple distros the  fstab uuid scheme can deteriorate fairly rapidly.

Only a single HD on this laptop but I've got Jaunty, Karmic and Lucid in adjacent partitions. The UUID for the swap partition is correct in all three fstab files and I don't recall having to edit either of the Jaunty or Karmic fstab's for swap. However, next time I do a fresh Ubuntu install (probably when Lucid goes final), I'll make a note to watch the swap UUID. I've got multiboots on all my machines so I'll have plenty of opportunity.

But to go back to an earlier point...

> **Longinus00 said:**
> This is why you should be using UUIDs instead of depending on in what order the kernel finds drives (which is by no means certain).

I believe you can get odd things happening when you've got a mixture of ide and sata drives connected, but if you have all-SATA or all-IDE drives, isn't the order of drives determined by the BIOS? I.e., if you don't move things around, sdb should remain sdb.

---

### Post by VMC on 2010-03-26
> **anaconda said:**
> Actually people have often problems with mounting  
swap partition using UUID:s
The problem is ofcourse that **UUID changes when reformatted**, and swap partition is sometimes reformatted.. eg. when installing another linux on a different partition.

So that is why I prefer to point to swap partitions the old way
/dev/sda4 
instead of using UUID for it..

No it does not. I just blkid before ubiquity installed to another partition and checked swap after format. The swap uuid was **not** changed, even though it was formated. I don't think ubiquity truly formats the swap. The uuid has never changed, and I have installed daily-live many times.

---

### Post by Irihapeti on 2010-03-26
> **VMC said:**
> No it does not. I just blkid before ubiquity installed to another partition and checked swap after format. The swap uuid was **not** changed, even though it was formated. I don't think ubiquity truly formats the swap. The uuid has never changed, and I have installed daily-live many times.

You may be right about Ubiquity - I haven't checked. My experience is that some other distros will certainly format swap, and then that will cause some confusion, including not mounting swap at all.

---

### Post by Tass on 2010-03-27
OK - so I've done the same thing on my recent Lucid upgrade, and can't boot.  Can anyone tell me how I can re-edit my fstab & get things working again?  I'm stuck on the mauve screen....

Edit: So I've now gone into the maintenance shell, sitting at the root prompt.  Now I just need to figure out how to edit my fstab.  gedit doesn't work as it can't be displayed, edit doesnt' seem to work either.

???

---

### Post by seeker5528 on 2010-03-27
> **Tass said:**
> Edit: So I've now gone into the maintenance shell, sitting at the root prompt.  Now I just need to figure out how to edit my fstab.  gedit doesn't work as it can't be displayed, edit doesnt' seem to work either.

Personally I prefer VIM for most things when at the command line, but....

A: I don't think it it is included by default. 
B: It does have a learning curve.

Nano is probably what you want. It's included in the base install and relatively easy.

Later, Seeker

---

### Post by maestrobwh1 on 2010-03-27
I actually just checked mine and it had 

/dev/sda1 / ext4 (options)

so I changed /dev/sda1 to 

UUID=(uuid of sda1) and rebooted.  It works fine and it just seems to give me more confidence that my system will be "less confused" now.

---

### Post by ptipton on 2010-04-15
I'm having the following problem which i think is related to this.
I have four drives that I'm trying to mount in to specific points such as mounting dev/sda1 to /mnt/music
If I do this in etc/fstab in the way I'm used to the drives seem to change identity  every time I boot and I end up with different drives mounted to different mount points.

From reading the posts above I bel;ieve I need to change fstab and use UUID's but I'm not sure where to find the UUID's or the exact format of the entry in fstab. 
(Its interesting to note that the 1st drive with the system installed is listed in fstab in the dev/sdc1 style, do I need to cahge this too?)
Any help much appreciated,please exscuse my ignorance.

---

### Post by cariboo on 2010-04-16
USe uuid's to instead of the device labels. To find the block id's, just open a terminal and type:

```
sudo blkid
``` 

the output should look something like this:

```
 sudo blkid
[sudo] password for me: 
/dev/sda1: UUID="6c97d50b-e070-4450-a25e-ea10e4e95164" TYPE="ext4" 
/dev/sdb2: UUID="1f467abb-26b1-411d-8789-da4afd4851a8" TYPE="swap" 
/dev/sdb6: UUID="c3502602-c749-479e-b2fa-406c3da100e3" TYPE="ext4" 
/dev/sdb1: UUID="3530feac-e0f6-4b70-8f4f-fb1ca8086454" TYPE="ext4" 
/dev/sdb5: UUID="1ab88036-a110-4f9f-8f64-145a29394c27" TYPE="ext4" 
/dev/sdc1: UUID="57D3-0244" TYPE="vfat"
```

---

### Post by Longinus00 on 2010-04-16
Check out the example fstabs
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This might still work if you don't want to edit the fstab yourself
[https://help.ubuntu.com/community/UsingUUID#Converting%20to%20UUIDs](https://help.ubuntu.com/community/UsingUUID#Converting%20to%20UUIDs)

---

