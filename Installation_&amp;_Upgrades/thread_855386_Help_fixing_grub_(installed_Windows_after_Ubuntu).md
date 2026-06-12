---
title: "Help fixing grub (installed Windows after Ubuntu)"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by bluesniper90 on 2008-07-10
Hi, I have been running Ubuntu as my only OS but needed Windows so I ran the live CD then resized my main partition. I then installed windows in the unallocated space and would boot automatically into it.  I ran the liveCD again and tried this:

sudo grub
root (hd0,1)
setup (hd0)
quit

Now I will see Ubuntu in grub on startup (but not windows) but it will get an error if I try to select it.  Can anybody help please?

---

### Post by louieb on 2008-07-10
At the grub> prompt check to see where GRUB lives  use the output of 
```
find /boot/grub/stage1 
```in the root statement then do your setup.
IF you get the GRUB menu but Ubuntu still won't boot check the** uuid in /boot/grub/menu.lst and etc/fstab**

Run the** blkid** command to list your partitions uuid and fix the above files as needed.

Your window entry should look something like this.
```
title Windows
root (hd0,0)
chainloader +1
```Change the root statement to your windows install partition.

---

### Post by bluesniper90 on 2008-07-10
> **louieb said:**
> 
In the root statement then do your setup.
IF you get the GRUB menu but Ubuntu still won't boot check the uuid in /boot/grub/menu.lst and etc/fstab

Run the** blkid** command to list your partitions uuid and fix the above files as needed.

Your window entry should look something like this.
```
title Windows
root (hd0,0)
chainloader +1
```Change the root statement to your windows install partition.

My grub was found at (hd0,1) but I still cannot boot.  I can't find those files, my /boot does not have a grub folder in it.  Also I found etc/fstab but don't know what to do there. (I'm running from the liveCD now if that matters).

---

### Post by VMC on 2008-07-10
> **bluesniper90 said:**
> My grub was found at (hd0,1) but I still cannot boot.  I can't find those files, my /boot does not have a grub folder in it.  Also I found etc/fstab but don't know what to do there. (I'm running from the liveCD now if that matters).

It would have been better to resize ubuntu first , then move ubuntu to the right making room for Windows as the first drive. Linux doesn't care where its located, but Windows prefers the first partition.

Doesn't matter, we can fool it into thinking its there. Type the following from a Terminal:

```
sudo fdisk -l
```

So we can see where everything is located.

---

### Post by louieb on 2008-07-10
> **bluesniper90 said:**
> My grub was found at (hd0,1)my /boot does not have a grub folder in it. 
Something is wrong. If there wasn't a /boot/grub/stage1 the find command would have  said file not found.  

 When you ran the setup command did you see the word [B]sucess?

[/B]Did you originally made a separate  /boot partition?    
So where are you now do you get the grub menu?

does it boot to the GRUB> prompt?
does it return error ##? what are the numbers?

Please like VMC requested post the output of sudo fdisk -l (lowercase L at the end).

---

