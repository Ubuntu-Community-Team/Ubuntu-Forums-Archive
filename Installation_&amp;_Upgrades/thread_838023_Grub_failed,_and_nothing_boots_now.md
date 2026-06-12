---
title: "Grub failed, and nothing boots now"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by newbie86 on 2008-06-23
I tried to install ubuntu.  Everything went fine until at the end.  It said grub failed, and it's a fatal error.  I've looked around and I couldn't find anything that can help me.

Here is the fdisk -l from booting into Live CD for ubuntu:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bddda92
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       11999    86135808    7  HPFS/NTFS
/dev/sda3           12000       12024      200812+  82  Linux swap / Solaris
/dev/sda4           12025       19457    59705572+   5  Extended
/dev/sda5           12025       19457    59705541   8e  Linux LVM

I believe sda1 is the drive that stores the Vista backup that came along on my Acer laptop.  sda2 is obviously my vista partition.

I tried installed ubuntu twice, once using sda3 as my swap, and once marking sda3 as "not used for ubuntu", but just sda4/sda5.

I previously set up Fedora on sda3 to sda5 (exactly the same partition that I have now).  I'm simply installing ubuntu over fedora, but my grub is failing miserably.

When I boot, I get into grub command line, and no OS can be booted now.

Is there an expert that can help me?  Thank you very much.
:confused:

---

### Post by newbie86 on 2008-06-23
Here is the "sudo fdisk -l" output again.  Got messed up by the formatting:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       11999    86135808    7  HPFS/NTFS
/dev/sda3           12000       12024      200812+  82  Linux swap / Solaris
/dev/sda4           12025       19457    59705572+   5  Extended
/dev/sda5           12025       19457    59705541   8e  Linux LVM

Thanks.

---

### Post by VMC on 2008-06-23
That sda1 might be the key to information passed to Grub .
Output the following:

```
cat /boot/grub/menu.lst
```

Since its not booting, you will have to boot from livecd and mount the drive that has "/", which is sd5. Can you do that?

---

### Post by forger on 2008-06-23
> **newbie86 said:**
> 
I previously set up Fedora on sda3 to sda5 (exactly the same partition that I have now).  I'm simply installing ubuntu over fedora, but my grub is failing miserably.


Does this mean that you go manually partitioning your formats?

Did you check the column where it says "Format" for sda5 ? Also, did you set it as mount "/" (the root partition)?

If not, please explain step by step what you do, or give us a screenshot of the manual partition changes you set.

---

### Post by newbie86 on 2008-06-23
Thanks for your reply.

I was lucky to get a friend working in IT to help me out.  I think there is a bug in Ubuntu during my installation process.  I will document it here for the benefits of others.  By the way, I didn't even have /boot/grub/menu.lst file after installation.

I did check on the format checkbox the first time I tried installing Ubuntu.  Ubuntu did format the disk for me (since it took some time for that step).  But somehow it didn't change the Partition Type, which was "Linux LVM" I believe, from Fedora.  Then that partition type got stuck there for Ubuntu.  Ubuntu tried installing grub without success because that was the only partition.

It took my friend a long time to figure that one out, because no grub commands could work successful due to mount failure(?).

At the end, I used Ubuntu live CD to run "fdisk".
He asked me to press "t" if I remember correctly to change the Partition type from 8e "Linux LVM" to 83 which is "Linux".  After changing to Linux type, and manually created a menu.1st with nano as the root thru "sudo su"

default 1
timeout 8
title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.24-16-generic
title           Microsoft Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Now everything works, and it defaults to boot Vista.

Certainly I can never figure this myself out.  Thanks to my friend.

Hope this will help any other people who may run into problems.  Be careful with fdisk though.  One can wipe out lots of things if he is not careful.

---

