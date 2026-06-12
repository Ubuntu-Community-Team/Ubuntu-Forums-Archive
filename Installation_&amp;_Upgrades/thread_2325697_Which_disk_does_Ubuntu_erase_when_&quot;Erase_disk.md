---
title: "Which disk does Ubuntu erase when &quot;Erase disk and install Ubuntu&quot; is selected?"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by 894532185610544562 on 2016-05-24
I have an SSD that I want to install Ubuntu on and I also have a backup HDD that is fully-encrypted that windows sees a "Raw" partition on. Mint sees it as "Basic Data." Obviously I would like Ubuntu to leave this HDD alone.
[The install guide]("https://help.ubuntu.com/community/GraphicalInstall") says nothing about which disk will be erased. Which disk in the system does the Ubuntu installation select for erasure and OS installation?

---

### Post by QIII on 2016-05-24
My suggestion would be to simply unplug the HDD and any other drive you do not want to install to.  No chance for mistakes then.

Are you trying to use the entire SSD?  If so, I would recommend "zeroing" it to factory condition so that you do not leave data in erasure blocks and reduce the effective size of the drive.

There is a good tutorial for how to do that [here]("https://wiki.archlinux.org/index.php/SSD_memory_cell_clearing").  This will start you out with a "fresh" SSD with no lingering junk.

---

### Post by 894532185610544562 on 2016-05-24
> **QIII said:**
> My suggestion would be to simply unplug the HDD

I was afraid of this answer. If no one really knows, then I will begrudgingly-manually unplug sata connectors.

> **QIII said:**
> 
Are you trying to use the entire SSD...I would recommend "zeroing" it...

The drive already contains an encrypted install of Mint (not just the home folder) so, there's no use for that. I no longer want Mint.

> **QIII said:**
> 
...you do not leave data in erasure blocks and reduce the effective size of the drive.

Why would the installer's "erasure" process leave "data" in erasure blocks?

---

### Post by QIII on 2016-05-24
We do know the answer:  It is installed to the drive you select for it to be installed to.  But unplugging all other drives avoids mistakes.

If you don't trim or zero, you may have a lot of junk lying around in erasure blocks.

If you want to trim the entire SSD, all of it will have to be included in a file system and you will need to create your new partitions *after* trimming.

---

### Post by 894532185610544562 on 2016-05-24
> **QIII said:**
> We do know the answer:  It is installed to the drive you select for it to be installed to.

[https://help.ubuntu.com/community/GraphicalInstall#Installation_type](https://help.ubuntu.com/community/GraphicalInstall#Installation_type) doesn't specify that...unless there's a subsequent screen after you click continue...

In regards to trim operations, I understand my Samsung 840pro gets periodically auto-trimmed in Ubuntu derivatives so I'm not particularly worried?

---

### Post by QIII on 2016-05-24
I don't know about whether derivatives add the weekly trim to cron or not.  I'd run trim on the fs to be sure.

But remember in any case that it's **fs**trim.  If you have, for instance, a single partition and that is all covered by your file system, then trimming before shrinking the partition to make room for the new OS will suffice.  If you don't trim the entire file system prior to shrinking the partition, you *may* end up with trash in erasure blocks.  If you have two partitions now and one is unallocated, you can't be sure of the condition.

That said:  The link you posted is for cases assuming one device and one OS.  It sound like you want to dual boot.  Is that correct?

---

### Post by 894532185610544562 on 2016-05-24
[delete me]

---

### Post by QIII on 2016-05-24
Trim is added to cron to maintain the SSD's performance.  It's not a sneaky attempt to do anything.  :)

OK.  So I would go back to zeroing the driver per the Arch wiki -- if that will work with an encrypted file system.  You want to be sure that the device is clean as a whistle and you get the maximum space.

---

### Post by 894532185610544562 on 2016-05-24
I was referring to unrelated, off-topic Linux apps that decide to put in these jobs. I couldn't figure out why the same background tasks were starting so after spending many hours going through startup applications and init scripts, I finally found cron and was supremely annoyed at the time.
I still don't have an answer to the original question...is there a subsequent screen when you click continue to select which drive you want erased or do you know?

---

### Post by QIII on 2016-05-24
On the "Installation Type" screen, choose "Something Else".  That will bring you to a GUI where you can choose which device and create a new partition table of your own design if you wish.

You can use that option even if you only have one device -- for instance if you have disconnected your other drives.

---

### Post by oldfred on 2016-05-24
I do not know nor use encryption. 

But you may want to review these:
[https://wiki.archlinux.org/index.php/Dm-crypt/Specialties#The_encrypt_hook_and_multiple_disks](https://wiki.archlinux.org/index.php/Dm-crypt/Specialties#The_encrypt_hook_and_multiple_disks)
The encrypt hook only allows for a **single** cryptdevice= entry.

       Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061)

---

### Post by 894532185610544562 on 2016-05-25
[delete me]

---

