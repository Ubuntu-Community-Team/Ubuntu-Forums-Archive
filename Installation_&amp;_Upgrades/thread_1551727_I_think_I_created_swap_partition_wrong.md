---
title: "I think I created swap partition wrong"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by tjustleft on 2010-08-12
I just set up a windows 7 ubuntu hardy dual boot. When I created my swap partition it came out as 
/swap           ext3    relatime        0       2 in fstab. By chance I came across a post somewhere that said it should have been something like linux-swap and showed how to fix it. Sadly I can't find the page again. It showd how to delete the partition then add the swap back in the same spot the right way. 

Can anyone show me how this is done? Thanks :)

---

### Post by wilee-nilee on 2010-08-12
> **tjustleft said:**
> I just set up a windows 7 ubuntu hardy dual boot. When I created my swap partition it came out as 
/swap           ext3    relatime        0       2 in fstab. By chance I came across a post somewhere that said it should have been something like linux-swap and showed how to fix it. Sadly I can't find the page again. It showd how to delete the partition then add the swap back in the same spot the right way. 

Can anyone show me how this is done? Thanks :)

You really only want to mess with swap from gparted, boot the live cd open gparted and look at it, right click to turn it off, to adjust.

Here is what my fstab line looks like for swap.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=525037ee-bf6a-478b-91b5-eadff77eb42a /               ext4    errors=remount-ro 0       1
[B]# swap was on /dev/sdb6 during installation
UUID=05e757f7-cfb0-4edb-b045-f5c46524db5e none            swap    sw              0       0
```[/B]

---

### Post by tjustleft on 2010-08-12
Thanks :)

Installed gparted and loaded it up. Right clicked my messed up swap and chose to format as swap. Then changed the line in fstab from /swap           ext3    relatime        0       2 to none            swap    sw              0       0 and rebooted. Ubuntu didn't like that but did let me boot with ctrl d. Turns out swap was assigned a new uuid which I found with sudo blkid. Entered the new uuid in fstab and now swap is on!

Now let's see if I can mess up something else by uninstalling hardy and installing lucid :)

---

