---
title: "Won't boot after resizing secondary drive from windows"
date: 2018-06-16
forum: MINT
---

### Post by mwei0210 on 2018-06-16
I have a ssd with another hdd, have windows and mint on ssd, was trying to make a bit of space in my hdd just for mint storage as it's ext4. After shrinking my hdd from windows, i then proceed to gparted via live usb to create ext4 using the unallocated space from shrinking. But after that, i am stuck at here. Any idea whats wrong? Thanks

[ATTACH=CONFIG]280111[/ATTACH]

---

### Post by TheFu on 2018-06-16
Did you boot into maintenance mode, as suggested?

If resizing made the UUIDs change, then the /etc/fstab needs to be updated with any different UUIDs. Use the **blkid** command to see UUIDs.

And grub might need to be updated when partitions/drives with an OS are modified. **update-grub** is the command.

---

### Post by oldfred on 2018-06-16
Moved to Mint sub-forum.

Is Windows fast start up on?
Did you run chkdsk from Windows on the NTFS partition you  resized? That is required.

---

### Post by mwei0210 on 2018-06-17
Solved it by blkid and replacing the old uuid in /etc/fstab with the new one! Thanks guys! :)

---

