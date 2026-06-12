---
title: "Win7/Ubuntu 9.10 no dualboot"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by Maintech on 2010-02-28
I have been reading the other posts that are similar but not the same as mine when determining the cause of grub not 'seeing' Win7. I have done all the usual things like 'update-grub' but it doesn't see it. I ran the script that has been suggested but can't identify what the issue is. Can anyone help? The output of the script is posted.

---

### Post by darkod on 2010-02-28
promise_fasttrack_raid_member

It seems the disk was a member of a raid array earlier.

I guess you are obviously NOT running raid with only one hdd, so just execute:

sudo dmraid -E -r /dev/sda

After that

sudo update-grub

should do the job.

Note: If you ARE running raid the dmraid command can break your array!

---

### Post by WubiNoob on 2010-02-28
If you think that Windows is still on the machine, just download a copy of Super Grub Disk, and then boot that to fix your Windows MBR. If that dosen't work, I don't know what to say.

---

### Post by Maintech on 2010-02-28
> **darkod said:**
> promise_fasttrack_raid_member

It seems the disk was a member of a raid array earlier.

I guess you are obviously NOT running raid with only one hdd, so just execute:

sudo dmraid -E -r /dev/sda

After that

sudo update-grub

should do the job.

Note: If you ARE running raid the dmraid command can break your array!

WOW!!!! This computer has never had a raid array in it. Never. It has one hard drive and contained XP and Ubuntu 9.10. I upgraded the XP to Win7-64 and reinstalled 9.10. What caused Ubuntu to think it ever had raid??? Your answer was exactly correct. I would never have dreamed that would be the issue. Thank you. VERY much.:D

---

