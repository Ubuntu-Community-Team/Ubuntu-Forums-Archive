---
title: "No entry in /dev/disk/by-uuid/ after HD install"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by patsissons on 2007-05-01
as the title says, I installed a new disk into my system, booted up, partitioned, formatted, grab the uuid with vol_id <device>, and finally update /etc/fstab.  Only one problem, I can't mount the device because the uuid symlink doesn't exist.  I _could_ manually create the symlink but that seems oh so very wrong.  I could also just edit the fstab to have the old style, but that seems hackish.  Any thoughts on this one?

---

### Post by patsissons on 2007-05-01
answer:

sudo udevtrigger

this appears to force ubuntu to refresh its device nodes

---

### Post by thor918 on 2007-06-29
> **patsissons said:**
> answer:

sudo udevtrigger

this appears to force ubuntu to refresh its device nodes

thanks! 
but be carefull. in my system, where I have many disks, some of the disks got new uuid's, and
that's a little bad, when you have to go over the fstab and correct.

---

### Post by pxwpxw on 2007-06-29
tune2fs has some uuid changing capability, have not used it though.

---

### Post by evarlast on 2007-10-04
on feisty running udevtrigger did not work for me.

A quick google lead me to some udev documentation and the vol_id command.  

to refresh the uuid's in /dev/disk/by-uuid, run vol_id using sudo, passing the partition as the argument:

sudo vol_id /dev/sdc1

Then your uuids will be refreshed and you can mount using your uuid fstab entry.

---

### Post by dabl on 2007-10-04
Also

```
blkid
```

is handy for keeping the dev/sdn designations straight with the UUIDs (like when you're attempting to edit /etc/fstab and not make things worse ...)  :)

---

### Post by mcfisch on 2008-04-09
I have the same problem on Ubuntu-Server 7.10 (Alternate-Install).

The tip with "vol_id" does not work for me. So "man vol_id" says the tool only prints the values like UUID or Label. It only tells me already known information (e.g. the real UUID).

I've added an new Volume (lvm2) and formatted it as an ext3-partition. After that i can't mount it by its UUID, cause this ID isn't linked to "/dev/disk/by-uuid/".

"udevtrigger" isn't wanted, cause the server hosts some important customer-websites and uses DRBD on RAID & LVM2. I don't want to risk a failure in the disk-subsystem. 

"blkid" also lists data about the volumes, but doesn't make any changes. 

Is manual linking of volumes to "/dev/disk/by-uuid/" an option?

:confused:

---

### Post by Ralph Corderoy on 2008-04-26
mcfisch, I agree with your summary.  vol_id isn't relevant.  blkid too only reads them.  I've found nothing that modifies /dev/disk/by-uuid and have asked a question on Launchpad: [https://answers.launchpad.net/ubuntu/+source/udev/+question/30919](https://answers.launchpad.net/ubuntu/+source/udev/+question/30919)

---

### Post by Ralph Corderoy on 2008-04-26
`sudo /etc/init.d/udev restart' works.  It makes udev work through the block devices again and /dev/disk/by-uuid gets up to date.

---

### Post by paul cooke on 2008-06-07
> **Ralph Corderoy said:**
> `sudo /etc/init.d/udev restart' works.  It makes udev work through the block devices again and /dev/disk/by-uuid gets up to date.

and just how do you do that with a system that's borked after an upgrade and dumps you into a busybox shell?

---

### Post by mcfisch on 2008-07-09
> **Ralph Corderoy said:**
> `sudo /etc/init.d/udev restart' works.  It makes udev work through the block devices again and /dev/disk/by-uuid gets up to date.

Thanks for the tip, 2 weeks after my first question at the german ubuntuusers.de-forum for a solution of this problem the server crashed - after reboot the UUID was active ;). I'll try your tip, when i have to make a new volume next time.

---

