---
title: "How to setup ext4"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cjnkns on 2009-03-04
I am wanting to eerr re-install jaunty but how do I set it up for ext4?

I know I have to manually partition, but does anybody have any suggestions on how to do this. Or documentation on how to do this in Ubuntu/Jaunty?

Thanks!

---

### Post by andrewabc on 2009-03-04
> **cjnkns said:**
> I am wanting to eerr re-install jaunty but how do I set it up for ext4?

I know I have to manually partition, but does anybody have any suggestions on how to do this. Or documentation on how to do this in Ubuntu/Jaunty?

Thanks!

In the step when partitioning comes up, you have to select manual partition. Then select what partition to install to, and select ext4 as filesystem (and format the partition, mount as / ).

I'm guessing you havn't done a manual partition installation before?

There should be screenshots of manual partitioner somewhere.

---

### Post by schms on 2009-03-05
FYI:

After turning a / - filesystem (ext3) in a ext4 filesystem my jaunty alpha 5 does not boot anymore with kernel 2.6.28-8-generic. The error messags is:

Boot from (hd0,0) ext4

Error 13: Invalid or unsupported executable format

Press any key to coninue....


With kernel 2.6.28-7-generic the system boots and works as expected.

Has anyone else seen this problem ?


In addition, after applying the patches from March 4, the X system is broken and I do not get further as the gdm login screen

---

### Post by nyarnon on 2009-03-05
Jup, seems that grub doesn't support ext4 yet hence the advice to not ext4 the /boot. I'm not sure though that applies as much to the bootloader as the /boot dir as I have /boot on a ext4 but the loader on a NTFS and this works fine.

---

### Post by taavikko on 2009-03-05
> **nyarnon said:**
> Jup, seems that grub doesn't support ext4 yet hence the advice to not ext4 the /boot. I'm not sure though that applies as much to the bootloader as the /boot dir as I have /boot on a ext4 but the loader on a NTFS and this works fine.

Oh but yes it does,
```
grub (0.97-29ubuntu47) jaunty; urgency=low

  [ Colin King ]

  * New patch, ext4_support now allows grub to boot from ext4 partitions.
    This patch orginated from Quentin Godfroy <godfroy@clipper.ens.fr>

 -- Tim Gardner <tim.gardner@canonical.com>  Tue, 06 Jan 2009 17:24:26 +0000

```

---

### Post by nyarnon on 2009-03-05
> **taavikko said:**
> Oh but yes it does,
```
grub (0.97-29ubuntu47)
  * New patch, ext4_support now allows grub to boot from ext4 partitions.
    This patch orginated from Quentin Godfroy <godfroy@clipper.ens.fr>


```

Thanks for the confirmation I started to daubt it when I red this posting.

---

### Post by Kow on 2009-03-05
I'm using a vbox'd jaunty with ext4 and grub handles it just fine. When you convert an ext3 filesystem to ext4 you should follow this guide:
[http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

If you don't then of course your newly converted ext3->ext4 filesystem won't work.

---

### Post by nyarnon on 2009-03-05
Yeah thats where it say's:

Right now there's not a stable version of grub that supports booting a kernel from a ext4 partition. It's recommended that you keep /boot in a ext3 partition.

That's what put me on the wrong foot.

---

