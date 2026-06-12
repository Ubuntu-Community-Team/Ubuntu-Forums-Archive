---
title: "Ubuntu 10.04 installations problems (partitions)"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by rajiv1096 on 2010-06-27
I have an HP computer with 4 partitions on it. 
/dev/sda1 = ntfs - SYSTEM
/dev/sda2 = ntfs
unallocated
/dev/sda3 = ntfs - RECOVERY
/dev/sd4 = fat32 - HP_TOOLS

I want to install Ubuntu 10.04, but it does not allow me since the limit to partitions is 4. What should I do? :mad: :confused:

---

### Post by krishnandu.sarkar on 2010-06-27
I'd say create a free partition from Windows and then boot from Live CD/use Wubi to install Ubuntu on that free partition.

The problem is you can't create more than 4 Primary Partition. So you need Secondary Paritition.

---

### Post by darkod on 2010-06-27
There is a procedure to create restore DVDs and then you can delete the restore partition. That will also make the space of that partition available to use.
You will also need to shrink sda2 depending how much space you want to allocate to ubuntu.

Leave the resulting space from these operation as unallocated, DON'T create partition for ubuntu from windows.

Boot with the ubuntu cd and start the installer and just tell it to use the Use Largest Available Free space option. That will install it into the unallocated space.

---

### Post by rajiv1096 on 2010-06-27
But do i really need to create restore dvd's?

---

### Post by rajiv1096 on 2010-06-27
Or can I just use Wubi to do this??

---

### Post by darkod on 2010-06-27
Wubi was not meant to be long term install, only a quick try. Sooner or later you will have problems with it. Plus, wubi is not independent of windows because it's not full dual boot.

I suggested to make the restore DVDs if you ever want to return the computer to factory state. When you delete the restore partition you will no longer be able to do that. And they didn't give you windows install disc right?

Another alternative is not to create the restore DVDs, delete the partition, and then just backup windows another way, for example clonezilla or similar. Or some windows tools.

---

### Post by krishnandu.sarkar on 2010-06-27
> **darkod said:**
> TBoot with the ubuntu cd and start the installer and just tell it to use the Use Largest Available Free space option. That will install it into the unallocated space.

Ya...that's much better option..!!

---

### Post by rajiv1096 on 2010-06-27
I think I'll try clonezilla because currently I dont have any dvd's :p lol

---

### Post by rajiv1096 on 2010-06-27
i actually deleted the HP Tools partition, but in the ubuntu isntaller, it still says i can't install ubuntu!

---

### Post by darkod on 2010-06-27
Does it say anything specific?
Boot windows and open Disk Management and check whether the disk is Basic, not Dynamic. Sometimes they ship windows with dynamic disk, linux can't work on that, not easily anyway.
And do you have enough unallocated space created? Do not use the side-by-side option to shrink windows, if you are using vista or 7 shrink it with Disk Management.

PS. You didn't create any partition in windows instead of HP Tools right?

---

### Post by rajiv1096 on 2010-06-27
I deleted the HP TOOLS partition, and then I shrunk my C drive, to about 50 Gigs. Now there are 2 unallocated partitions, and they dont combine to form a larger partition.

Once i boot into Ubuntu, i cannot install side by side or even use the largest continuous free space. Am I doing something wrong?

---

### Post by darkod on 2010-06-27
> **rajiv1096 said:**
> I deleted the HP TOOLS partition, and then I shrunk my C drive, to about 50 Gigs. Now there are 2 unallocated partitions, and they dont combine to form a larger partition.

Once i boot into Ubuntu, i cannot install side by side or even use the largest continuous free space. Am I doing something wrong?

Boot windows and in command prompt run:

chkdsk /r /f

---

### Post by rajiv1096 on 2010-06-27
I did what you said, but when i booted into Ubuntu, i could not choose a partition to install it on.

---

### Post by darkod on 2010-06-27
Are you reading what we say here? I said no partition should be created into the unallocated space, leave it as unallocated, not belonging to any partition.
What is sda4, with size of 50GB? Again you have 4 partitions, and that's the limit. You have created another partition after deleting HP Tools which beats the point.

Delete that partition (if it's newly created and empty) and the installer will show you other options too.

---

### Post by rajiv1096 on 2010-06-27
When i deleted the HP Tools Partition, it became unallocated. The size of it was about 100 mb. I wanted to increase it so i shrunk my C drive 50 gigs or so. I ran the command you gave me, but nothing seems to happened.:confused:

---

### Post by darkod on 2010-06-27
That command was only to check the C: for errors. I wrote it before you attached the screenshot.

Only shrinking sda3 would not have created sda4. Anyway, just open Gparted (System-Administration) in live mode and delete sda4. After that start the installer and use Use Largest Available Free space option.

---

### Post by rajiv1096 on 2010-06-27
Thanks!! It's installing right now!

Thank you very much :)

---

### Post by rajiv1096 on 2010-06-27
Its done installing but 1 more problem.. I know this has nothing to do with installation, but the sound isnt there! But it comes through the headphones..what should i do?

---

