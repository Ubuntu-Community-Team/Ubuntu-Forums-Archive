---
title: "grub rescue  and Error reading boot CD"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by piyushmundra on 2010-04-10
I have a SONY VAIO CW26 laptop. I got a Windows-7 version prepacked with the laptop. 
 
I installed Ubuntu Karmic 9.10 over a new partition that i created using the inbuilt facility in windows7. Both the operatings systems i.e windows7 and ubuntu karmic 9.1 were working nicely.
 
Today i created 2 more partition within the partition inside windows.
 
Once I rebooted after creation of the new partitions my laptop is just showing a black screen with following message.
 
GRUB loading. 
error: unknown filesystem
grub rescue>_
 
After going throug previous posts i realized that i have corrupted my grub in the process of partitioning. 
 
 
Output of set command.
grub rescue> set
prefix=(hd0,6)/boot/grub
root=hd0,6
 
 
Output of ls command.
grub rescue> ls (hd0,6)/boot/grub
error: unknown filesystem
 
Whereas
 
Output of ls command
grub rescue> ls (hd0,9)/boot/grub
./ ../ device.map ....... 
....
... list of .mod files
 
 
Issue is after reading the posts on previous issues in forum i am trying to run 
 
linux and boot commands in grub rescue> prompt but in those cases its showing Unknown command 'linux' 
Unknown command 'boot'
 
 
[COLOR=red]**Also when i am trying to boot from the live cd of Ubuntu 9.10 karmic its giving **[/COLOR]

[COLOR=red]**"Error reading boot CD".**[/COLOR]
 
 
Please help me to find out solution to the problem......... :(

---

### Post by quixote on 2010-04-11
Can you get Windows to boot, or does nothing boot at all?  

If nothing boots, the steps to follow are probably to use a Windows recovery disk to remake the Master Boot Record.  (Assuming it will read that CD!)  

That would, I'm pretty sure, destroy your Ubuntu partitions, and any data on the Ubuntu partitions would be lost.  Is that okay?

Once Windows is resuscitated, then partition using the Ubuntu LiveCD and gparted, or do a wubi install without partitioning.  Do *not* use Windows because it assumes a Microsoft-only universe and will generally cause problems with other OSes.

I'll go over the steps in more detail if you want to do this.

---

### Post by bcbc on 2010-04-11
You can boot from the grub command line. It looks like your partitions changed, so the grub menu is invalid, but it's pretty simple to boot. As long as you know where ubuntu is (it sounds like it's on hd0,9.
```
insmod ext2
set root=(hd0,9)
linux	/vmlinuz root=/dev/sda9 ro quiet splash
initrd	/initrd.img
boot
```

Once it's booted, go to a terminal and run
```
sudo update-grub
```

Should be sorted after that.

---

