---
title: "Disk check more frequently after I install Arch"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by oppih on 2010-03-13
Recently I installed Arch on my computer. There are now three systems on it:XP,Ubuntu,Arch.I choose to share the same disk space for swap and /home in the two systems.The installation went well except some problems with Grub, and I managed to made it work. 

These days,when I start my computer and choose Ubuntu,there always displays a short message about /home disk checking or some problems about fstab. I don't know why. When I login to the system, it works well all the time.

Anybody knows there is a problem or it doesn't matter at all?

---

### Post by mikewhatever on 2010-03-13
What do the massages say? You could probably look through the system log for full text, and if that is in Chinese, then a more comprehensive translation is in order.

---

### Post by oppih on 2010-03-13
> **mikewhatever said:**
> What do the massages say? You could probably look through the system log for full text, and if that is in Chinese, then a more comprehensive translation is in order.

The log files on my pC are in English...
I cannot decide which file in /var/log is the right one I should refer...

---

### Post by mcduck on 2010-03-13
> **oppih said:**
> Recently I installed Arch on my computer. There are now three systems on it:XP,Ubuntu,Arch.I choose to share the same disk space for swap and /home in the two systems.The installation went well except some problems with Grub, and I managed to made it work. 

These days,when I start my computer and choose Ubuntu,there always displays a short message about /home disk checking or some problems about fstab. I don't know why. When I login to the system, it works well all the time.

Anybody knows there is a problem or it doesn't matter at all?

When you installed Arch you most likely edited your partitions in some way or other, and that causes the UUID of any edited partition to change. On the other hand you Ubuntu install's /etc/fstab file still has the old UUIDs and it tries to access & check partitions based on those UUIDs. Since they don't actually exist any longer you get error message.

The fix is simple, run "blkid" to get the correct UUIDs for all your partitions and then edit /etc/fstab accordingly.

---

### Post by oppih on 2010-03-13
I have used blkid just now. And I'm sure the result is the same with /etc/fstab

---

### Post by mikewhatever on 2010-03-13
> **oppih said:**
> The log files on my pC are in English...
I cannot decide which file in /var/log is the right one I should refer...

dmesg, syslog ...

---

### Post by oppih on 2010-03-15
Thank you.

I readed the log files but didn't quite understand ...

---

