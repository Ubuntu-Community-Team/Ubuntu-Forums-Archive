---
title: "Lost my boot sector and grub"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2008-02-11
This is Lenovo Thinkpad. After last-night's update ( on both Vista and Ubuntu ), not sure which one screwed up my grub, to start with.

This morning, when I booted my laptop, I didn't see the vista entry.

I ran 'tstdisk' and now I think I screwed up something and have lost all OS's.

When I boot my laptop now I get "1234F:".

I then loaded the Ubuntu CD and now when I do fdisk -l, I get the following entries
> 
Device|Start|End|Blocks|Id|System
/dev/sda1|1|877|70...|5|Extended
/dev/sda5|1|877|70...|7|HPFS/NTFS


But there are three other partitions which doesn't show up, while I can see them
if I go to the advanced mode of fdisk.

I'm unable to mount either of these two drives, to fix grub.

Please advice.

Thanks,
Kramer.

---

### Post by taurus on 2008-02-11
Maybe you can use Super GRUB to fix your GRUB.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

