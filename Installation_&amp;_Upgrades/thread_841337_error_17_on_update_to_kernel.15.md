---
title: "error 17 on update to kernel.15"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2008-06-26
Hello there.  'Hope some one here can help me.  'Using Ubuntu 7.10 here.  I just clicked on update this morning; I saw that it was upgrading the kernel and I'd have to reboot, but that's never been a big deal before as the old kernel is always around to use in case something doesn't work right with the installation of the new one.

Anyway, I'm on a Dell Vostro 200.  It has a largish SATA hard drive, I think 80 gigs, and I had a dual boot system with Windows XP Professional installed just so that I can use Filemaker Pro at work.  The problem is that when I rebooted after the update my Windows partition was missing and when I tried to boot Ubuntu, either kernel, I got an "Error 17 unable to boot selected partition" message.

Please tell me what may have gone wrong with the update and/or point me in the right direction.

Thank you.

---

### Post by eryksun on 2008-06-26
Maybe GRUB can't find the boot partition? For example, maybe it's looking for /boot on (hd0,0) when it should be looking at (hd0,1)? See here

[http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update](http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update)

and here

[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by Nopposan on 2008-06-26
Yep.

I decided to try a few different partitions while I was waiting for a response.  (hd0,1) worked.

Thank you just the same for pointing me in the right direction.

Now I just need to remember how to edit the grub menu to give the option of booting the windows partition.

I'll keep you posted.

Cheers.

---

### Post by Nopposan on 2008-06-26
'Found my reminder at [URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu"]

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

Then I changed my Linux partition boots to (hd0, 1) and added the following after all of the Linux entries.

```
title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Problem solved. . . until the next update when I might have to do this again.

Thank you for tuning in.

---

### Post by eryksun on 2008-06-26
> **Nopposan said:**
> 

Problem solved. . . until the next update when I might have to do this again.

Thank you for tuning in.

I don't know why an update would mess with your XP boot options, unless you have it inside your automagic update section, i.e. before this line

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Also, if you scan down just below this line

```
### BEGIN AUTOMAGIC KERNELS LIST
```

there should be a default option, groot, for updates to use, which looks something like this:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

You can change it to (hd0,1) to have that setting applied to updates from now. But don't remove the # signs. To GRUB, they're just comments; the default settings are only meant for the updater to use.

---

### Post by Nopposan on 2008-06-26
O.K., I followed your advice and changed that entry to groot=(hd0,1).  Also, yes, the Windows stuff was before the comment-out line that you mentioned; I probably placed it there myself due to a misunderstanding of someone's instructions here on this forum long ago.

Anyway, thank you.

---

### Post by eryksun on 2008-06-27
> **Nopposan said:**
> O.K., I followed your advice and changed that entry to groot=(hd0,1).  Also, yes, the Windows stuff was before the comment-out line that you mentioned; I probably placed it there myself due to a misunderstanding of someone's instructions here on this forum long ago.

Anyway, thank you.

You're welcome. :)  I hope your next update is uneventful...

---

