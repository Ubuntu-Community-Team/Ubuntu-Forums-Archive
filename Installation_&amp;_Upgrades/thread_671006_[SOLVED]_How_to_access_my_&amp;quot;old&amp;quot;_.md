---
title: "[SOLVED] How to access my &amp;quot;old&amp;quot;  xfs drives"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by BillDozer on 2008-01-18
I recently reinstalled my server with 7.10 server and put xubuntu-desktop on it afterwards.

But now I cannot access my xfs formatted disks anymore. When I look at them with Gparted, I can see that they are there but the only feature for xfs is that it can be detected.

I think I need to install xfs support, but how do I do that?

---

### Post by Gen2ly on 2008-01-18
xfs support is still in the kernel but probably not a standard part of it anymore.  look in the tip and tutorials for howto compile a kernel.

---

### Post by renzokuken on 2008-01-18
xfs support should already be there, you just need to mount it. you can do this on boot by adding it to the **/etc/fstab** file

make a folder in you media file

```
sudo mkdir /media/folder
``` (you can change folder for whatever you like, as long as it matches the entry to the fstab)

now open your fstab

```
sudo nano /etc/fstab
```
and add the following line

```
/dev/hda5 /media/folder xfs defaults 0 0
```

(make sure you use the correct drive name instead of hda5, running **sudo fdisk -l** should tell you.)

save the file by pressing Ctrl+X, Y then Enter

now run
```
sudo mount -a
``` to remount everything and see if it worked.

---

### Post by BillDozer on 2008-01-18
Thanks, 

I know, I am not unfamiliar with mount. But haven't tried it, only mounted from xubuntu. it could be that that is the problem, I'm not at my machine right now, but I will try it when I get back home.

---

### Post by BillDozer on 2008-01-21
Ups,

I think i have reformatted the drives some point in time, that is probably why they show up empty and that was the reason I was confused about it.

 My bad ;-)

Thanks for the replies.

---

