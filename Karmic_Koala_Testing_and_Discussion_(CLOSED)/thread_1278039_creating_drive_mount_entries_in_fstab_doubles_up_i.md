---
title: "creating drive mount entries in fstab doubles up in nautilus pane"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-09-29
I added these lines to my fstab

UUID=23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0     0
UUID=f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4  user,auto 0    0


The folders I created in /media actually have the same names as the drive labels.

The problem is, now I have double entries in the nautilus side pane and it's really annoying.

---

### Post by VMC on 2009-09-29
> **sonicb00m said:**
> I added these lines to my fstab

UUID=23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0     0
UUID=f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4  user,auto 0    0


The folders I created in /media actually have the same names as the drive labels.

The problem is, now I have double entries in the nautilus side pane and it's really annoying.

Before you added those lines were there single entry in Nautilus? Why did you add them in the first place? Output "sudo blkid" so we can see what those uuis's are referring to.

---

### Post by sonicb00m on 2009-09-30
I added them because I needed them to automount. I don't want to have to open nautilus and click them so they mount.

Those uuids are refering to the drives I want automounted. Which are already listed in the nautilus pane.

I've always done this. Usually all it did was display the mount icon on the labels in nautilus. Not duplicate anything.

---

### Post by mc4man on 2009-10-01
@ sonicb00m
I did the same thing about a week or so ago to see and didn't get duplicate volumes in places.
The difference was I didn't use ext4, I'll give that a try and see what occurs.

---

### Post by mc4man on 2009-10-03
Went ahead and tried with an ext4, and while it mounted properly at boot, did show the duplicate entry in places.
fat32 and ntsc didn't, didn't try ext3.

Using /dev/sdXX instead of the UUID for the ext4 resulted in a proper mount at boot and only 1 entry in places

So I'm gathering that unless there is another way, or the issue is resolved, that using /dev instead of UUID is the way to go.

---

### Post by Longinus00 on 2009-10-03
> **sonicb00m said:**
> I added these lines to my fstab

UUID=23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0     0
UUID=f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4  user,auto 0    0


The folders I created in /media actually have the same names as the drive labels.

The problem is, now I have double entries in the nautilus side pane and it's really annoying.

What happens if you give it different mount options? Try taking away the auto or something.

---

### Post by sonicb00m on 2009-10-04
> **Longinus00 said:**
> What happens if you give it different mount options? Try taking away the auto or something.

No then the drives don't auto mount at start up. It did remove the double entries though.

---

### Post by sonicb00m on 2009-10-04
> **mc4man said:**
> Went ahead and tried with an ext4, and while it mounted properly at boot, did show the duplicate entry in places.
fat32 and ntsc didn't, didn't try ext3.

Using /dev/sdXX instead of the UUID for the ext4 resulted in a proper mount at boot and only 1 entry in places

So I'm gathering that unless there is another way, or the issue is resolved, that using /dev instead of UUID is the way to go.

hmm yes this fixed it. Now the extra entries disappeared as soon as I did a mount -a.

thanks

---

### Post by martin_lindhe on 2009-10-04
I found this thread while looking for a solution to similar issue here.

I set up my fstab using the LABEL directive:

LABEL=downloads /media/downloads   ext4   users,noauto,noexec,noatime,rw  0 5

and i also have duplicate entries in nautilus.

This seems like a bug but i dont know in what package. Nautilus?

It needs to understand disks identified by UUID or LABEL from /etc/fstab

---

### Post by martin_lindhe on 2009-10-04
I didnt find a bug report for this issue, so i opened one here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442130)

---

### Post by sonicb00m on 2009-10-05
thanks for submitting the report. You seem to have hit the nail on the head there.

Labelling the partitions is the easiest way to identify them so it's something I am keen to stick with. I have mounted with the /dev/sd* for now since I am not likely to make new partitions just yet so it's not a big deal but for the next install it would be great not to have to remember this :)

---

### Post by martin_lindhe on 2009-10-05
Upstream suggested a work-around:

Instead of using LABEL=xx, specify disk with /dev/disk/by-label/xx
For UUID=xx it is /dev/disk/by-uuid/xx

I can confirm this works, it no longer shows duplicate entries in Places.

---

### Post by sonicb00m on 2009-10-06
I'm sorry i've got the wrong end of the stick. I don't use the labels in fstab. I meant I only label the partitions with gparted to have a name.

my fstab is like this

UUID=23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0    0
UUID=f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4   user,auto 0    0

And it creates duplicates still.

The partition labels are also set to 01-media and 02-audio.

---

### Post by martin_lindhe on 2009-10-06
> **sonicb00m said:**
> I'm sorry i've got the wrong end of the stick. I don't use the labels in fstab. I meant I only label the partitions with gparted to have a name.

my fstab is like this

UUID=23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0    0
UUID=f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4   user,auto 0    0

And it creates duplicates still.

The partition labels are also set to 01-media and 02-audio.

Yes. To work around your issue, you need to change the syntax like this:

/dev/disk/by-uuid/23408a8a-0d1f-4138-b53d-52bc6defc92b /media/01-media ext4  user,auto 0    0
/dev/disk/by-uuid/f6c415d5-dfcd-48f8-a303-e3f4e901d70a /media/02-audio ext4   user,auto 0    0


Hope that helps!

---

### Post by sonicb00m on 2009-10-06
jo tack, nu funkar det ordentligt!

---

