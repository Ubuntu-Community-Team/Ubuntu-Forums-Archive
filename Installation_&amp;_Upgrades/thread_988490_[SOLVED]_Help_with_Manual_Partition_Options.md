---
title: "[SOLVED] Help with Manual Partition Options"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by nickyoung on 2008-11-20
In the middle of installation right now...I read up on this but I can't afford to mess this one up and I haven't done it before.  Am I doing this right?

**What I want...**
[LIST]
[*]I want to Dual Boot - Windows XP Pro / Ubuntu 8.10
[*]No need for hibernation feature (swap)
[*]No need for maintaining settings for quick reinstall (home)
[/LIST]

**Process so far...**
[LIST]
[*]Burnt ISO to DVD
[*]Booted up
[*]Checked disc for errors > passed.
[*]Went through basic setup screens.
[/LIST]

**My Partition Options**
I have 1 drive partitioned as follows (all partitions are already formatted as ntfs):
[LIST]
[*]/sda1 ntfs - 38074 MB - win xp pro + software
[*]/sda5 ntfs - 10487 MB - files + documents
[*]/sda6 ntfs - 10487 MB - files + documents
[*]/sda7 ntfs - 10487 MB - files + documents
[*]**[COLOR="Green"]/sda8 ntfs - 10478 MB - i want Ubuntu on this[/COLOR]**
[*]free space - 8mb
[/LIST]

**[COLOR="Green"]I click Edit Partition for sda8, then what?[/COLOR]**
[LIST]
[*]Use As = Ext3 ???
[*]Format Partition = Yes ???
[*]Mount Point = / ???
[/LIST]

Any help appreciated thanks.
-Nick

---

### Post by mikewhatever on 2008-11-20
>     * Use As = Ext3 ???
    * Format Partition = Yes ???
    * Mount Point = / ???


Yes to all three.

---

### Post by Idefix82 on 2008-11-20
> **nickyoung said:**
> 
**[COLOR="Green"]I click Edit Partition for sda8, then what?[/COLOR]**
[LIST]
[*]Use As = Ext3 ???
[*]Format Partition = Yes ???
[*]Mount Point = / ???
[/LIST]


Exactly!

---

### Post by nickyoung on 2008-11-20
THANK GOD FOR THE INTERNET. :) problem solved in 15 minutes...hahaha..now to continue loading ubuntu!

---

