---
title: "cpu usage 100 %"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by chad_jensen on 2006-10-28
I upgraded from 6.06 last night via network. I now have a problem. The cpu usage is at 100% when the computer is idle. I used the top command and the total cpu usage by the processes didn't amount to more than 7 or 8 percent. I also used the system monitor with the same results. I tried the swap space solution swapon -a and it said the resource was busy. But it had 0 on the system monitor for swap usage. If I remember right the swap is used slightly even if there is enough memory. (Think I remember that) I am at a loss any help be appreciated.
Thanks
Chad

---

### Post by vibestriton on 2006-10-28
If you open System->Pref...->Power Management and ask it to do nothing when idle, does this still happen?

---

### Post by Shay Stephens on 2006-10-28
I was getting high cpu usage too and it turned out to be fsck doing a disk check that never ends...ever.  Only happened in edgy.

---

### Post by chad_jensen on 2006-10-28
The power management already is set at do nothing. and it could be the hasrd drive stuck in endless loop. the light flashes even when at idle. how did you correct it?
Thanks
Chad

---

### Post by reubano on 2006-11-03
> **Shay Stephens said:**
> I was getting high cpu usage too and it turned out to be fsck doing a disk check that never ends...ever.  Only happened in edgy.

same thing happens to me. How do I check to see if I have the same cause as you? and how do I fix it if this is the case?

---

### Post by Shay Stephens on 2006-11-03
You can turn off disk checking (probably not recommended) in /etc/fstab by making the last number a zero:
UUID=05caa451-a16e-42ac-a57a-82af85213937 /               ext3    defaults,errors=remount-ro 0       [COLOR="Red"]1[/COLOR]

The example above has it turned on, if I wanted it off, I would make that 1 (in red) a zero.

The other option that also worked for me and the one I am using now, was simply to reformat the drive.  It was fat32 and I made it ext3.  I don't know if that was the fix or just the fact that it was cleaned and formatted of something that may have been corrupt.

I discovered which of the three drive I had was causing the problem by, one by one, turning the disk check off, reboot and see what happens, then turning it back on and moving to the next drive until I find the drive having trouble.

---

### Post by reubano on 2006-11-03
> **Shay Stephens said:**
> You can turn off disk checking (probably not recommended) in /etc/fstab by making the last number a zero:
UUID=05caa451-a16e-42ac-a57a-82af85213937 /               ext3    defaults,errors=remount-ro 0       [COLOR="Red"]1[/COLOR]

The example above has it turned on, if I wanted it off, I would make that 1 (in red) a zero.

The other option that also worked for me and the one I am using now, was simply to reformat the drive.  It was fat32 and I made it ext3.  I don't know if that was the fix or just the fact that it was cleaned and formatted of something that may have been corrupt.

I discovered which of the three drive I had was causing the problem by, one by one, turning the disk check off, reboot and see what happens, then turning it back on and moving to the next drive until I find the drive having trouble.

Thanks. I fixed it but that wasn't the issue. It turned out to be acroread. I simply killed the process and I have been back to normal since. I also read in a few other threads and there seems to be a bug in the beagled deamon. So check that too if neone is still having problems. If that is the cause, be sure to disable the beagled startup program in the sessions menu in addition to killing the process.

---

