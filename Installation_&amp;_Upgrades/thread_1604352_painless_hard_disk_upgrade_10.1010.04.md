---
title: "painless hard disk upgrade 10.10/10.04"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by roop_s on 2010-10-23
**Why I'm writing this:**
I need to move files from a 500GB drive to a 2TB drive without re-installing. I've tested this on a 10.04 system and later tonight I'll test it on a 10.10 system. I expect this would work on both. It took me several days to compile and test a procedure that would work (and a couple that didn't work). You would expect something so common would have many complete guides but no. Even on the ubuntu forums there is no clear single post with this information so here it is for you and future me.


**Before starting:**
Ensure backups are done of critical data before this procedure just in case however this procedure is meant to leave the old hard disk alone in the event the clone fails. In my environments the current drive is sda and the new drive is sdb and there are no other hard disks. I assume the new disk is blank and presently connected.


**Backup the MBRs:**
The new drive needs an MBR in order to boot up. I don't want to have GRUB recreate it as that's an extra step so I'll back it up since the MBR works perfectly fine right now:
sudo dd if=/dev/sda of=mbrsda bs=446 count=1
sudo dd if=/dev/sdb of=mbrsdb bs=446 count=1
If you compare them in a text editor or md5sum they should be different. Keep them handy however the MBRs should be copied.


**Copying paritions and the MBR:**
Boot into a GParted livecd, you should have access to sda and sdb. Select the partitions from sda (one at a time) and copy them to sdb in order to clone each partition:
- Copy the / paritions and resize it if needed.
- Copy any other paritions like /home if you keep that separate
[COLOR="Red"]- For swap, there's no need to copy it, just recreate it, either as a logical or primary partition but exactly the same as it was before. [/COLOR] Apparently this is not true. The swap is based on the UUID solely and not the partition name. If you don't clone the swap partition, you will not have swap space. If you are able to run your computer without a swap, you can later edit /etc/fstab and put swap's new UUID in there. It may be easier and less error prone to simply clone the swap partition at the expenses of some cloning time.
- Ensure swap is flagged as linux-swap. 
- If you flip between sda and sdb in GParted, they should look the same. 
- You don't have to tell GParted to copy the MBR, it just does it. I couldn't find more information on the net about this behavior.
- For 150gb of data on a 2.2ghz system, this took 1.25 hours.


**First boot of the clone:**
When GParted is done, shutdown the PC and disconnect the old hard disk.
Can you boot off the clone? If so, everything is good and you can skip the next section.


**It didn't work:**
Skip this section if it did work and you're running on the new disk.

Boot back into GParted and see if the clone drive is detected as sda now because it should with only the single new drive attached.

If it's sda in GParted but GParted didn't capture the MBR, you can try this:

GParted may not be able to mount your new partition if it's ext4 (couldn't in my case). Boot off the old hard disk or better yet a ubuntu live CD. Capture the MBR again and compare it to the first MBR file you saved. It should be identical. If not, copy the MBR saved on the first step onto the new drive. Here is a guideline command but you need to be 100% sure what "if" and "of" are.

dd if=mbrsda of=/dev/sda bs=446 count=1
Try booting now. if it still doesn't work, start googling, or maybe try this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


**Testing:**
If you're up and running with the new drive alone, depending on how critical the system is I'd start testing now. Maybe put the old hard disk somewhere safe and run with the new one for a week. If it works well, clear the old disk and you can use it for backup or something. If you do re-use the old drive, make sure it's on a different port so it doesn't become sda again.


**It works but what about UUIDs?**
The UUIDs are also cloned so files like /etc/fstab and /boot/grub/grub.cfg will have the cloned UUID.

If you don't clear the old disk (delete the partitions, re-create and format) I'd expect some kind of UUID conflict but I'm not sure on how the UUIDs are chosen. Once the old drive is cleared and a new partition is on it, you'll have a new UUID for the old drive and all is well:

ls -l /dev/disk/by-uuid/
lrwxrwxrwx 1 root root 10 2010-10-23 22:10 7832f6f2-9e3a-4b33-a808-dfa94726dabf -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-10-23 20:50 95cec1df-ee4d-4ca2-86fd-f7a536a03b5f -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-23 22:10 c440d02f-537d-4b68-ba3c-3c1501b43efe -> ../../sdb1

/etc/fstab will have the wrong UUID for the swap partition unless you cloned it but. You can edit /etc/fstab, update the swap UUID if you need to and reboot to get swap space. /boot/grub/grub.cfg will have the cloned UUID so it will be ok.

**Improvement on this thread**
How did the MBR copy?
I don't know. I didn't tell gparted to copy the MBR, it just did it. In my testing, the sda and sdb MBRs didn't match until I ask GParted to clone the first partition. 

UUID is cloned.
It probably shouldn't be but it does make this procedure really easy. If there's a way to not clone the UUID while keeping the steps minimal (and less human error prone) I'd like to hear it.

Is there a better way of doing this?
I sure hope so. I'll be referring back to this thread every time I have to upgrade a hard drive or replace a failing drive so if you have better ideas (which you have done and you know it works) please reply.

---

### Post by roop_s on 2010-10-24
The above steps worked really well on one computer and they didn't work at all on another. I used an older version of gparted above, and 0.6.4 on the second system. On the second system, I had to manually copy the MBR and even then, I just had a grub prompt. I'll have to check what gparted version the previous system used.

After some experimenting I came to this procedure that worked well and was fast:

1. Boot gparted livecd (or something else)
2. from a terminal run sudo dd if=/dev/sdb of=/dev/sda bs=8M
if = input drive (old one)
of = output drive (new one)
bs = 8 million (bits or bytes?) This gave me sustained 100mbyte/sec transfers.
3. Shutdown, disconnect the old drive and modify the BIOS if needed. You should be able to boot from the new disk.
4. If everything looks good on the new disk, boot back into gparted and resize the partition.

*To check the process of dd while it's running, run sudo kill -USR1  <dd pid>
credit: [http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html](http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html)

**If you don't specify a block size, the transfer rate is slow, near 25mbytes/sec. With a block size of 8M I got 100mbytes/sec which probably approaches the maximum practical transfer rate from drive to drive. I was able to copy 500GB in a little over an hour which is pretty fast compared to the 5+ hours without specifying a block size.

Given the simplicity of these steps, I'll just do this in future, rather than the more cumbersome graphical approach above.

---

