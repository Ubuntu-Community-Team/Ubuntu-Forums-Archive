---
title: "Question about creating partitions when more than 1 user profile will be made"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by giga+bytes on 2016-07-27
I want to create 1 user profile for main office use (encrypted) and 1 for everything else (going online for updates, research, etc.; still all office use but not the important work and data). Is it better to create a separate /home partition for each user profile, or for the 2 user profiles to share the same /home partition?

Specifics: solely Ubuntu 14.04 (no Windows at all), entire volume of an SSD will be used, will be setting to Legacy BIOS if possible.

---

### Post by papibe on 2016-07-27
Hi giga+bytes.

I think you want to create 2 different users, right? As in 'two different Ubuntu login users'? Is that it?

Or these are Firefox profiles?

Regards.

---

### Post by giga+bytes on 2016-07-27
I thought it was "user profiles", but I guess I was wrong. Oops! Yes, it is two different Ubuntu login users.

---

### Post by papibe on 2016-07-27
If you need encryption, I would encrypt a whole partition using lucks.

You need another partition, but not exactly another /home. If you have a regular user, leave it as it is.

General steps to create a new user with encrypted home partition:
[LIST]
[*]Make space and create a new partition.
[*]Encrypt it.
[*]Create a ext4 filesystem.
[*]mount it at, say, /home/cryptouser
[*]Create the new user, let's say, newuser.
[*]Move newusers' dot files to /home/cryptouser
[*]umount the encrypted partition and remount it on /home/newuser.
[*]
[/LIST]
Does that helps? Let us know how it goes.
Regards.

---

### Post by giga+bytes on 2016-08-02
I will be assembling my new PC tomorrow (if the last components arrive), but I am figuring out everything I can before I first power it on, so am revisiting this thread and starting a new thread for more specific information to get the partitioning sorted out.

I have done some research and decided to create a separate home partition for each login user (both will be me). I assume the first 2 steps you list are all I need for the partition I want to encrypt in this case?

---

