---
title: "Reinstalled Windows 7, need to restore boot menu so I can dual boot Ubuntu"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by thatguyjeff on 2010-07-12
Hello, all.  I am here today because I am having trouble dual booting Windows 7 and Ubuntu.  I previously had Windows 7 primarily and then installed Ubuntu using Wubi onto a partition of my main hdd.  Now, after reformatting and reinstalling Win7, my boot menu is understandably reset to only booting Windows.

I still have my Ubuntu .disk files and everything on the Ubuntu partition, so I think it's just a matter of setting up the boot menu.  How do I go about doing this? Could I theoretically make another partition of my hdd and install Wubi there, later copying over my other Ubuntu installation files to that partition?

Thanks!

---

### Post by bcbc on 2010-07-13
> **thatguyjeff said:**
> Hello, all.  I am here today because I am having trouble dual booting Windows 7 and Ubuntu.  I previously had Windows 7 primarily and then installed Ubuntu using Wubi onto a partition of my main hdd.  Now, after reformatting and reinstalling Win7, my boot menu is understandably reset to only booting Windows.

I still have my Ubuntu .disk files and everything on the Ubuntu partition, so I think it's just a matter of setting up the boot menu.  How do I go about doing this? Could I theoretically make another partition of my hdd and install Wubi there, later copying over my other Ubuntu installation files to that partition?

Thanks!

Just move your root.disk and swap.disk somewhere outside of the \ubuntu directory (on the same partition is fine). (Move is quicker than copying on the same partition). Then delete the \ubuntu directory and reinstall with a minimal size (say 3 or 4 gb). Once the windows part is complete, before you reboot, copy the root.disk and swap.disk back to the \ubuntu\disks\ directory (deleting what's there) and it should work just like before. Keep your original root.disk as a backup as well.

If you have any issue with this, then do a full reinstall, and then copy over the root.disk only (the swap.disk will be initialized at that point).
Note if you reinstall to a different partition, then the grub menu on the root.disk will not be accurate (you can edit it manually, but easier not to have to). So, stick with the same partition.

EDIT:
Just a point. On the off chance that you have other .disk files. Most wubi installs do not, but it is possible if e.g. you installed to a fat32 partition or you manually separated your /home. In this case, copy and replace those too.

---

### Post by thatguyjeff on 2010-07-14
> **bcbc said:**
> Just move your root.disk and swap.disk somewhere outside of the \ubuntu directory (on the same partition is fine). (Move is quicker than copying on the same partition). Then delete the \ubuntu directory and reinstall with a minimal size (say 3 or 4 gb). Once the windows part is complete, before you reboot, copy the root.disk and swap.disk back to the \ubuntu\disks\ directory (deleting what's there) and it should work just like before. Keep your original root.disk as a backup as well.

If you have any issue with this, then do a full reinstall, and then copy over the root.disk only (the swap.disk will be initialized at that point).
Note if you reinstall to a different partition, then the grub menu on the root.disk will not be accurate (you can edit it manually, but easier not to have to). So, stick with the same partition.

EDIT:
Just a point. On the off chance that you have other .disk files. Most wubi installs do not, but it is possible if e.g. you installed to a fat32 partition or you manually separated your /home. In this case, copy and replace those too.

Hey. Thanks for the reply! I tried what you said but after rebooting and trying to boot into Ubuntu it gave me two errors, device not found and partition not found. It was on the same partition as before and everything, I copied only root.disk over. :( This is so frustrating!

---

### Post by bcbc on 2010-07-14
> **thatguyjeff said:**
> Hey. Thanks for the reply! I tried what you said but after rebooting and trying to boot into Ubuntu it gave me two errors, device not found and partition not found. It was on the same partition as before and everything, I copied only root.disk over. :( This is so frustrating!

OK... I've copied root.disk's between computers and to different partitions before and it works right off if the partitions are the same... but even when it's not it doesn't take a lot to get it running. so let's just figure out what is happening.

when you select Ubuntu, do you get the grub menu you are used to seeing? Or does it just drop you at the grub> prompt.

When you are at the grub prompt run and note the response to:
```
search.file /ubuntu/disks/root.disk
```

And post back.

But the quickest way to solve this would be if you have a live cd (an ubuntu install cd you can boot from and select 'try without changes') and you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back (instructions in link).

---

### Post by thatguyjeff on 2010-07-15
> **bcbc said:**
> OK... I've copied root.disk's between computers and to different partitions before and it works right off if the partitions are the same... but even when it's not it doesn't take a lot to get it running. so let's just figure out what is happening.

when you select Ubuntu, do you get the grub menu you are used to seeing? Or does it just drop you at the grub> prompt.

When you are at the grub prompt run and note the response to:
```
search.file /ubuntu/disks/root.disk
```

And post back.

But the quickest way to solve this would be if you have a live cd (an ubuntu install cd you can boot from and select 'try without changes') and you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back (instructions in link).

Yeah, it's the normal grub menu. I'll try this later and let you know what happens.

---

### Post by bcbc on 2010-07-15
> **thatguyjeff said:**
> Yeah, it's the normal grub menu. I'll try this later and let you know what happens.

That menu is actually being read from the root.disk. So the boot mechanism is working. It's just that the menu references a partition/device that's no longer valid. Which probably just means that when you reinstalled, win7 did something different.

But we just need to edit the menu entry a little and it should quite happily boot itself.

---

