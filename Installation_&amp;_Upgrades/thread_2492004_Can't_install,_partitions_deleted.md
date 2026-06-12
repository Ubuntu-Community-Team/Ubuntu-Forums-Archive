---
title: "Can't install, partitions deleted"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2023-10-27
I have obtained an old HP desktop which used to be dual-boot with Windows and Linux, but no longer has either OS installed. I can boot a Lubuntu installation USB disk, but it refuses to install on the hard disk. Using KDE Partition Manager, I see that the former partition structure seems to have been deleted  (see uploaded screen image). I'd be grateful for advice on how to rebuild a suitable partition structure which will permit installation of Lubuntu.

---

### Post by TheFu on 2023-10-27
Using the Installation Flash drive you've already made, choose the "Use Whole Drive" option. This should wipe the disk, removing any prior data and partitions.

---

### Post by yancek on 2023-10-27
If the use the whole drive option does not work for you, you will need to post more details and explain what  "it refuses to install on the hard disk" means.  Warning or error messages?  I'm not familiar with KDE partition manager but it should have an option to create a new partition table for the device, perhaps from the Device tab at the top of the window?

---

### Post by jet-bundle on 2023-10-28
Thanks for both the comments. The suggestion that I use the "erase whole drive and start again" option in the USB installer has in fact now worked, so I'll mark this thread as closed.

But it's strange. When I used the installer yesterday, I'm sure that the "erase whole drive" option wasn't available, and that in fact there were no available installation options. That's what I meant by "it refuses to install on the hard disk". But as I didn't take a photo of the installation screen, I can't provide documentation to justify this. Still, it's now academic. Thanks again.

---

### Post by guiverc on 2023-10-28
> **jet-bundle said:**
> When I used the installer yesterday, I'm sure that the "erase whole drive" option wasn't available, and that in fact there were no available installation options. That's what I meant by "it refuses to install on the hard disk". But as I didn't take a photo of the installation screen, I can't provide documentation to justify this. Still, it's now academic. Thanks again.

This is solved I know, but...

I'll provide a link to the manual - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)  (*that's the latest stable release; ie. 23.10, as you didn't provide release details*)

I suspect you had a *mounted* partition on the drive, either because of exploration to *peek* at what was there, or had a partition *automount*. In the manual the following warning is provided

> If you had a previous Linux install with a swap partition you will need to unmount the swap. To do this run

as if a *mounted *partition exists on that drive, no *Erase Disk* option will appear.  Either way we won't know what the actual issue was now.

---

### Post by yancek on 2023-10-28
The image in your first post shows the drive as a 1TB drive with unknown for the filesystem type.  Could be  a corrupted filesystem or partition table.  Glad you got it working.  Also possible it was an ntfs filesystem which had been left hibernated.  Just speculation.

---

### Post by jet-bundle on 2023-10-28
Thanks for the additional comments and link. Sorry I can't provide any more information on the problem (though I'll mention that I stick to LTS versions, so I'm still on 22.04).

---

