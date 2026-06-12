---
title: "Problem with partitions"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2006-06-01
OK, I see that everyone is busy exploring the wonders of Ubuntu... But some people have problems with the installation :(
Here is my story: I dualboot WindowsXP and Breezy. Now that I have a CD with Dapper I want to remove Breezy and install Dapper, while keeping Windows untouched.
But what should I do with the partition manager during the installation? 
The current configuration for 80GB HDD (just after passing step 4):

/dev/hde1, ntfs, 20GB, boot (untouched - for Windows)
/dev/hde2:extended, 56.33GB, lba
/dev/hde5, ntfs, 30GB (untouched - Windows data)

Now here follows the new partitions:
New partition Nr1. ext3 23.44GB (here I want Dapper to go!)
New partition Nr2. swap, 509MB
New partition N3. fat32, 2.14GB (for swapping data between OS's)

After applying the changes I get a very confisuing window - where should be the mount point? The listboxes are confisung. Help me.

---

### Post by Zdravko on 2006-06-01
Ok, I have an idea:
On the first mountpoint I select '/'. Then I choose partition 6 - hde6. The label shows 23GB. Then I check 'Format'.
Next I select 'swap', with partition 7 - hde7 accordingly. Here the label shows 510MB. Again 'Format' is checked.

Is this OK? Should I go further?

---

### Post by johnc4510 on 2006-06-01
You've got the idea, I would however suggest a /home partion. By doing this, the next time Ubuntu put out a release, you can just put it on the / partion and your personal data on the /home partion remains untouched and ready to use.

---

