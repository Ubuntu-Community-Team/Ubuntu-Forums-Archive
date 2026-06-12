---
title: "Newbie questions: I'm totally new to Ubuntu"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by frhong on 2006-08-07
First of all, I have to state that this is my first time I use Linux ever, so as ubuntu. I choice it because a few of my friends are using it and, more importantly, it has a huge user community here. 

OK, here comes my questions.

I have a 30G hard drive divided into three FAT format partitions, C: D: E: . I had installed XP in C:, but it's not working now (that's also why I start ubuntu).  D: and E: are used for installing software and storing musics.

I am in the middle of installing ubuntu i386 desktop right now. It shows three options in "prepare disk space", listed as follow:

1. Erase entire disk: IDE1 master (hda) - 30.0GB IC25N030ATCS04-0
2. Use the largest continuous free space (I did a space partitioning before)
3. Manually edit partition table

What I want is keeping all the data in D: and E: safely and install ubuntu in C:. I will format C: if it's really necessary. 

Is this possible to achieve? I am not sure my way of thinking is correct or not, that's why I am here asking help. Hope somebody can help me.

Thank you very much!

---

### Post by scxtt on 2006-08-07
choose option 3, to manually edit the table - you should see your separate partitions (you won't see C:, D:, and E: -- you'll see hda1, hda2, hda3) ... so you should delete the hda1 (it'll show up again as "free space") and repartition it into 2 parts (1 for installing ubuntu and 1 for swap space) ... this won't touch your 'D:' and 'E:' partitions ... you'll probably be left w/ hda1 (ubuntu), hda2 (D:), hda3 (E:), and hda4 (swap) ...

---

### Post by greybirds on 2006-08-07
EDIT: Woops... scxtt and I overlapped on that one :) 

If you choose option 1, then it will erase all three partitions and use the combined space for the install, so that's not the option you want.

Option 2 will find and use any unpartitioned space and use it. I'm assuming you've divided the entire hard disk between your three partitions, so this option won't work.

Option 3 will show you the paritions that are currently on the disk and let you add, modify, and delete them. It sounds like this is the option you want.

It's important to realize that the C,D,E labels are only how Windows names partitions. You'll need to be able to recognize the partitions some other way (I find the partition size useful).

Also, in almost all cases you will want to create two partitions for linux: one for the file system and one for a swap file (used to make more efficient use of your computer's memory). What size that swap file should be and whether you even need one are addressed in other threads. I know a bit, but don't want to mislead you, so it's best to find out from more knowledgeable sources. 

If you decide a swap partition is needed, you'll want to delete the partition Windows was installed on and create the two partitions in it's place. The installer will detect your two existing partitions and add them into the file system so you can access your files.

---

### Post by frhong on 2006-08-07
Thanks to scxtt and greybirds' quick respond, I am getting a little bit more knowledge about ubuntu now.

Right, I click option 3, and it shows up as below:

[HTML]
Partition       Filsystem          Size           Flags
 /dev/hda1        fat32           9.77GB         boot lba
 /dev/hda2        extended        18.18GB           lba
   /dev/hda5      fat32           6.96GB        
   unallocated    unallocated     2.81GB
   /dev/hda6      fat32           8.41GB
[/HTML]

It looks like hda1 is C: and hda5 and hda6 is D: and E:. So in this case, should I choose hda1?

---

### Post by frhong on 2006-08-07
I came to step 5/6 where i need to prepare mount points. I don't quite get the "mount points" meaning.

I've got three options here, how as below:
[html]
Mount Point    Size         Partition             
/              10G    Partition 1 Disc IDE/ATA 1 (Primary) [hda1] 
/media/hda5    7G     Partition 5 Disc IDE/ATA 1 (Logical) [hda5]
/media/hda6    8G     Partition 6 Disc IDE/ATA 1 (Logical) [hda6]
[/HTML]

There is a "reformat" option follow each one.

I marked the Mount point of that 10Gb one "/", but it came a error message saying that "Invalid file system for this mount point". 

Do I need to reformat the 10Gb one?

---

### Post by confused57 on 2006-08-07
Here's a guide for installing with the desktop cd:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

