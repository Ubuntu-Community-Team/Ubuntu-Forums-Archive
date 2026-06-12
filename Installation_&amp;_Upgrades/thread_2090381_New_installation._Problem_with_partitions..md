---
title: "New installation. Problem with partitions."
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by iamkodi19 on 2012-12-02
i have a 2 partitions in my hdd, then my first partition is where i install my ubuntu, then the second is my backup.. after the installation, it didnt show my backup partition.. :(

when i type fdisk -l in terminal:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000000bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   620967935   310482944   83  Linux
/dev/sda2       620969982   625141759     2085889    5  Extended
/dev/sda5       620969984   625141759     2085888   82  Linux swap / Solaris

and i think the:
"/dev/sda2       620969982   625141759     2085889    5  Extended"
is my backup partition change into ext4 i think

anyone can help me how i can change it back to ntfs or i maybe i can mount it so i can access my files..:(

---

### Post by coffeecat on 2012-12-02
Post moved to own thread.

iamkodi19, please start your own threads.

I've given your thread what I hope is a suitable title, but it is not clear exactly what your problem is. For people to be able to help you, you need to give more details.

---

### Post by darkod on 2012-12-02
What filesystem do you have on that second backup partition? Did you create a mount statement in /etc/fstab for it?

The partitions that are mounted can be accessed with their mount point.

The partitions that are not mounted, can be found in the Devices section when you open the file browser Nautilus (the standard file browser).

---

### Post by iamkodi19 on 2012-12-02
> **darkod said:**
> What filesystem do you have on that second backup partition? Did you create a mount statement in /etc/fstab for it?

The partitions that are mounted can be accessed with their mount point.

The partitions that are not mounted, can be found in the Devices section when you open the file browser Nautilus (the standard file browser).

darkod where i can find this Devices, im using lubutu..

---

### Post by darkod on 2012-12-02
Unfortunately I don't know the lubuntu interface. In ubuntu the Devices would be shown on the left side in that window you posted.

Where it says Places, you see there is like a small arrow to the right of it. Try clicking on it and maybe that can change Places into Devices.

Alternatively, in the main menu of the window, look in File, etc.

---

### Post by iamkodi19 on 2012-12-02
> **darkod said:**
> Unfortunately I don't know the lubuntu interface. In ubuntu the Devices would be shown on the left side in that window you posted.

Where it says Places, you see there is like a small arrow to the right of it. Try clicking on it and maybe that can change Places into Devices.

Alternatively, in the main menu of the window, look in File, etc.

sir, check my attachment, is the hi lighted one is your talking about?.. thats is where i can access my devices.. but my other partition is not showing, the one that i talking about above...

---

### Post by darkod on 2012-12-02
That looks like a usb stick.

I just noticed you updated your first post with the fdisk results. They show that you only have one root partition (/dev/sda1), and one swap partition (/dev/sda5).

sda2 is only the extended container that contains the sda5 logical partition.

So, there is no other partition to show. sda1 is the main root partition, and sda5 is the swap partition.

---

### Post by Cheesemill on 2012-12-02
What darkod said.

You only have one Linux partition on your drive.

---

### Post by iamkodi19 on 2012-12-03
yes thats my flash drive.. and your right! it doesnt show my backup partition.. maybe it hidden or something?  coz when i boot xp using hirens and scan my harddisk, it appeared...

---

### Post by arpanaut on 2012-12-03
> it appeared...
What appears?

If your partition with your backup data appears then copy it to somewhere safe as quickly as possible!
Because it appears to me that your install was initiated with the "Use Entire Disk" option, as you are showing only a /root partition and an extended partition with a /swap partition within that extended partition. Everything else has been overwritten by the install.

Common practice would be to stop using the hard drive on your system and only use cd/usb booted media.  Take a look at the links in this post by oldfred: [http://ubuntuforums.org/showpost.php?p=11839619&postcount=2](http://ubuntuforums.org/showpost.php?p=11839619&postcount=2)

Be sure that you understand what you are doing before you proceed.
This is not going to be simple or fun!
Good Luck!!!

---

### Post by darkod on 2012-12-03
XP wouldn't be able to show any linux partitions. And if it does, I would be very careful touching linux partition from windows. It can easily mess them up.

Further more, look at the start/end sector numbers of the fdisk results. Where sda1 ends, sda5 continues (with only small space between them), and sda5 ends almost at the end of the disk. So, all of the disk is taken by sda1 + sda5. I don't see where another partition would be.

---

