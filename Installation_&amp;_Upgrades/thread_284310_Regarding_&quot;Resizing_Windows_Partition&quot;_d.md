---
title: "Regarding &quot;Resizing Windows Partition&quot; during installation"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2006-10-25
I installed Daper on my notebook a few months back, and I'm going to install Edgy on my desktop soon.

However, I have one small question:

When I installed on my notebook, I simply used the automatic partitioner and selected to resize my windows partition.  I set to resize at 20GB (out of 60GB total)  Now, this might get confusing, so I'll try to be very clear.

What I THOUGHT I was doing was resizing the Windows partition to 20GB and leaving ~40GB for Ubuntu. In reality, however, Ubuntu is on the 20GB drive, and Windows is on the 40GB drive.  I didn't even realize this until this week, when I mounted my Windows Drive.

So, I want to clarify: if I am installing Edgy and resizing the Windows partition -- when I select a number in the installer for the size of the drive, will I be selecting how large the Windows partition will be or how large the Ubuntu partition will be?

Thanks

bg

---

### Post by happysmileman on 2006-10-25
Well I think it would be easier to partition the drives first, you can do it from the Dapper live CD so I assume you can do it from the Edgy one.

---

### Post by Kateikyoushi on 2006-10-25
Select manual partitioning then you have more control over it and can see exatcly what are you doing.

---

### Post by bg1256 on 2006-10-25
Okay, however, I did originally try the manual partitioning, and I made a huge mess, which resulted in comlpetely reformatting and using the method I just described.

If I want to dual boot XP and Edgy, it seems I would need 4 separate partitions, correct?

One for the XP drive, which would require a secod small partition partition(can't remember the name).
Which type of drive would these be?

For Ubuntu drive, I would need a / and swap, correct?
What type of drive would these be?

---

### Post by Kateikyoushi on 2006-10-25
You only need 3, One for Xp and two for ubuntu a / and a swap.
Read this guide for installation and partitioning help. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by bg1256 on 2006-10-25
Thanks much.  The link was very helpful.

One more question, however. 

My desktop has a 250 GB drive, and I want to leave 50 GB for Windows, for gaming and a few other apps I've yet to find for Ubuntu.

If I install using the manual installer and give ~200 GB to Ubuntu, will I lose all the data on my Windows partition? No biggie if I do, since it's all backed up - but the real question is, will I need to reformat and reinstall Windows on the 50 GB drive after using manual install?

---

### Post by Kateikyoushi on 2006-10-25
Defragment the drive before resizing and a backup of important data is always recommended. You won't loose data by resizing the windows partition as it will let you resize only to such size that your data remains intact this is why defragmenting is recommended.

---

### Post by bg1256 on 2006-10-25
Okay, good. I defrag'd last night, but I'll do it again before install.

---

