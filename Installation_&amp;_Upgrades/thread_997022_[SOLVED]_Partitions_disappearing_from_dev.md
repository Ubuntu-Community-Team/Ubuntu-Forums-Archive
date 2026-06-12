---
title: "[SOLVED] Partitions disappearing from /dev"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by ThatOtherOtherGuy on 2008-11-29
**[COLOR="Red"]This issue was resolved by deleting and recreating the partions with gparted. For some reason it didn't like partitions created with cfdisk.[/COLOR]**

Hi all, didn't find anything in search, sorry if I missed it.
Trying to migrate from gentoo to ubuntu 8.10, but having some problems with the installer.

```

/dev/sda1   *           1       15502   117192704    7  HPFS/NTFS
/dev/sda2           15502       15634      997920   82  Linux swap / Solaris
/dev/sda3           15634       15766      997920   82  Linux swap / Solaris
/dev/sda4           15766       51681   271518761    5  Extended
/dev/sda5           15766       17704    14651248+  83  Linux
/dev/sda6           17704       20287    19527448+  83  Linux
/dev/sda7           20287       51681   237340000+   c  W95 FAT32 (LBA)

```

I can't blow away my partition table as I have information I need to maintain.

```

 ls -al /dev/sda*
brw-rw---- 1 root disk 8, 0 2008-11-29 17:08 /dev/sda
brw-rw---- 1 root disk 8, 1 2008-11-29 17:08 /dev/sda1
brw-rw---- 1 root disk 8, 2 2008-11-29 17:08 /dev/sda2
brw-rw---- 1 root disk 8, 3 2008-11-29 17:08 /dev/sda3
brw-rw---- 1 root disk 8, 4 2008-11-29 17:08 /dev/sda4
brw-rw---- 1 root disk 8, 6 2008-11-29 17:08 /dev/sda6
brw-rw---- 1 root disk 8, 7 2008-11-29 17:08 /dev/sda7

```

You'll notice that sda5 is missing. The device node is there when I first boot, I can mount it and format it manually, but as soon as the (graphical.. haven't tried text.. if there is one) installer tries to prepare the drive for installation, the device node disappears for some reason. I checked /var/log/messages but there's no indicator of a problem. Here's a excerpt from the installer debug log
```

partition: ('1', '1048576-120006377471', '120005328896', 'primary', 'ntfs', '/dev/sda1', '')
partition: ('2', '120006377472-121028247551', '1021870080', 'primary', 'linux-swap', '/dev/sda2', '')
partition: ('3', '121028247552-122050117631', '1021870080', 'primary', 'linux-swap', '/dev/sda3', '')
partition: ('5', '122050149888-137053028351', '15002878464', 'logical', 'ext3', '/dev/sda5', '')
partition: ('6', '137053060608-157049167871', '19996107264', 'logical', 'ext3', '/dev/sda6', '')
partition: ('7', '157049200128-400085360639', '243036160512', 'logical', 'fat32', '/dev/sda7', '')
partition: ('1', '32256-120031511039', '120031478784', 'primary', 'fat32', '/dev/sdb1', '')
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:2414: GtkWarning: gtk_cell_layout_set_attributes: assertion `GTK_IS_CELL_RENDERER (cell)' failed
  self.grub_device_entry.set_text_column(0)
partition: ('1', '1048576-120006377471', '120005328896', 'primary', 'ntfs', '/dev/sda1', '')
partition: ('2', '120006377472-121028247551', '1021870080', 'primary', 'linux-swap', '/dev/sda2', '')
partition: ('3', '121028247552-122050117631', '1021870080', 'primary', 'linux-swap', '/dev/sda3', '')
partition: ('5', '122050149888-137053028351', '15002878464', 'logical', 'ext3', '/dev/sda5', '')
partition: ('6', '137053060608-157049167871', '19996107264', 'logical', 'ext3', '/dev/sda6', '')
partition: ('7', '157049200128-400085360639', '243036160512', 'logical', 'fat32', '/dev/sda7', '')
partition: ('1', '32256-120031511039', '120031478784', 'primary', 'fat32', '/dev/sdb1', '')
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1163: Warning: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2384: instance `0xa784b50' has no handler with id `1582'
  self.scale_changed_id)
Error unsetting `/desktop/gnome/volume_manager/automount_drives': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```

Nothing seems to indicate a problem here either.

I've gone so far as to recreate that particular partition ( a step I would rather like to avoid repeating :) )

Anyway, I thought it worth mentioning here in case anyone is having the same issue.

---

### Post by icanfly0307 on 2008-11-29
By migrating from Gentoo to Ubuntu, do you mean that you want to get rid of Gentoo entirely? If so, then you might as well run the LiveCD installer and tell it use the entire disk (assuming you don't have other operating systems or important data).

By the way, if you have any sort of Intel hardware, DON'T download Ubuntu 8.10. Instead, go for Ubuntu 8.04. It's more stable and it is really easy to setup.

Good Luck!:)

---

### Post by ThatOtherOtherGuy on 2008-11-29
> **icanfly0307 said:**
> By migrating from Gentoo to Ubuntu, do you mean that you want to get rid of Gentoo entirely? If so, then you might as well run the LiveCD installer and tell it use the entire disk (assuming you don't have other operating systems or important data).

By the way, if you have any sort of Intel hardware, DON'T download Ubuntu 8.10. Instead, go for Ubuntu 8.04. It's more stable and it is really easy to setup.

Good Luck!:)

Yes, I'll be formatting / and just keeping /home if possible, I also have vista install on sda1 which I need to keep unfortunately. I'll look into 8.04, though I can say I'm not one to give up quite so quickly. The problems are half the fun. :)

Thanks.

---

### Post by icanfly0307 on 2008-11-29
Alright, I can see that you won't be *entirely* reformatting your computer. If I were you, I would backup my /home partition and get rid of it because there could be problems between the hidden files when Ubuntu tries to write them over. Are you using the LiveCD or the alternate install CD (text mode)?

And I'm sure you'll change your opinion about the problems being 'fun', once you try to fix them in 8.10. :) It's really time-consuming and tedious.

And what was it that you were saying about sda5 disappearing in your first post? I didn't really get what you were saying.

---

### Post by ThatOtherOtherGuy on 2008-11-29
> **icanfly0307 said:**
> 
And I'm sure you'll change your opinion about the problems being 'fun', once you try to fix them in 8.10. :) It's really time-consuming and tedious.

And what was it that you were saying about sda5 disappearing in your first post? I didn't really get what you were saying.

I'm coming off about 5 years of gentoo :) So I hate myself enough to enjoy that kind of stuff.

So when I boot the liveCD, all my partitions are fine. Including sda5. I can format it, mount it, write to it... etc(via cli). But as soon as the installer tries to format it.. the /dev/sda5 node gets deleted for some reason. Of course the partition is still there, and a reboot fixes it, but it makes it a bit hard to installed when "/dev/sda5: no such file or directory" pops up when the installer tries to format the partition. 

I'm playing with gparted right now and seem to be able to duplicate the issue using that, so it may be a parted issue. 

Anyway, I hope that makes it a bit clearer.

---

### Post by icanfly0307 on 2008-11-29
What exactly do you plan to use sda5 as? /home? /? swap? Wouldn't it be easier to backup your stuff, delete all the Gentoo partitions, including swap, and then tell the Ubuntu installer to use the existing free space?

---

### Post by ThatOtherOtherGuy on 2008-11-29
> **icanfly0307 said:**
> What exactly do you plan to use sda5 as? /home? /? swap? Wouldn't it be easier to backup your stuff, delete all the Gentoo partitions, including swap, and then tell the Ubuntu installer to use the existing free space?

Yeah, that would have been easiest but unfortunately when I built the table years ago I made my primary storage partition inside of an extended. I did however get it resolved. I guess maybe there was some strangeness with the way CFDISK built the partitions? I'm not sure. But blowing away both / and h/home (sda5 and sda6 respectively) and rebuilding them with gparted allowed me to pass that particular problem :)

Thanks for the advice!

---

### Post by icanfly0307 on 2008-11-29
Glad to know you got it working! :)

---

