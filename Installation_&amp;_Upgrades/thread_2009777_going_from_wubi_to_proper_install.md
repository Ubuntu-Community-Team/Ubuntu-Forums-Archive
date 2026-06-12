---
title: "going from wubi to proper install"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by emonti on 2012-06-24
Hi,

I installed the windows installer, not knowing that it is only a trial feature.

Now I want to install the real thing. I created a boot usb and booted the machine from it.

The 3 options which appear are somewhat unclear to me. (1. sounds like an inside windows install i.e. the demo/trial, 2. sounds like removing all trace of the windows partition and 3. sounds like a 'going it alone' option) 

Anyway when I (resize? shrink?) the windows partition, choosing the 3rd option, it says the remaining space on my 750Gb drive, which was formerly NTFS, is 'unusable'. The screen doesn't allow me to format the space. I can't create a partition in that space. It seems it won't allow me to do anything useful.

Help! If I could wind back the clock, I wouldn't have bothered with the windows installer but it sounded to me as though it was a new way to do a proper install... from within windows. Now I realise that is not the case and it is just a trial thing. (it really isn't very clear on the desktop install page on ubuntu.com).

I have 1 day to do a proper install before I lose my internet connection for a few weeks.

Any advice would be much appreciated.

---

### Post by raja.genupula on 2012-06-24
> Anyway when I (resize? shrink?) the windows partition, choosing the 3rd  option, it says the remaining space on my 750Gb drive, which was  formerly NTFS, is 'unusable'. The screen doesn't allow me to format the  space. I can't create a partition in that space. It seems it won't allow  me to do anything useful.


Actually System allow us for limited number of primary partitions(4) . I think you already have created more than that . thats why your PC not allowing you to create more .

---

### Post by Bucky Ball on 2012-06-24
Yea, four primary the max. You need to delete one and make an extended partition in its place. You can then put as many logical partitions inside that as, theoretically, your hardware can handle. 

Ubuntu happy to live on logical partition inside an extended. Win not; likes first partition, first drive. ;)

---

### Post by emonti on 2012-06-25
Thanks, guys for your advice.

I want to be careful of what I do here and I'm not experienced with this.

I can upload a few screen shots and maybe you can help me to make the right changes.

---

### Post by raja.genupula on 2012-06-25
Among the 4 NTFS partitions make any one as free & Delete that partition .

Now , the free space will add up with new deleted partition .Here you have to convert this entire space into a extended partition then you can install Ubuntu there by making a partition with 20-30 GB (thats more than enough in my case , you can give you as your wish ) and you can make the remaining space into few other partitions and you can use  them for your needs .

---

### Post by emonti on 2012-06-25
Okay, I've selected the hptools partition to reformat and use as the primary linux partition. 

Should I install first and then come back to claim that 600-dd gb of space for linux? Or do I have to claim it first, before the install?

---

### Post by Bucky Ball on 2012-06-25
You need to install to it, as previously described. You will need:

/ = root, 20Gb fine;
/home = your personal data, big as you like;
/swap = 2Gb fine.

Choose 'Something Else' in the partitioning section of the install and set this up. You will see the free space there; create an extended partition with it then create the partitions I've mentioned as logical partitions inside that extended one.

---

### Post by oldfred on 2012-06-26
+1 on    	Bucky Ball's suggestion.

But if you are going to dual boot Windows you may want to share some data. Ubuntu will read & write NTFS partitions just fine, but Windows does not like lots of data written into it from foreign systems. It may be just that Ubuntu shows all the hidden Windows files & folders that Windows normally hides and makes it too easy for a user to accidentally damage something. 

I prefer to make the Windows system partition read only and create one more NTFS shared data partition. I have all photos for Picasa, and Firefox profile, & Thunderbird profiles in my shared NTFS (still) even though I rarely boot XP anymore. Then the Windows applications & Ubuntu applications all have the same data.

---

### Post by Bucky Ball on 2012-06-26
+1. I have a 30Gb partition called 'Misc' for anything that needs to be shared between the two. Thing is, I never use the Win partition and when I do I use programs that create files which couldn't be used in Ubuntu anyway! ;)

---

### Post by emonti on 2012-09-29
Hi,

I'm finally coming back to this thread after I failed to get things sorted out last time... I lost my internet connection before I could follow up om the advice offered. Now I'm back, albeit with limited(capped) connectivity. So here goes...

I have deleted sufficient number of partitions to create the suggested extended linux partition but when I mount that partition I get the following message appearing in Disk Utility(for the new partition):

 > "Warning: The partition is misaligned by 512 bytes. This may result in very poor performance. Repartitioning is suggested."
I can store data on the partition but would like to know what the above message means. I did try deleting and re-creating the partition, twice, but it made no difference to the presence of the warning message.

Any advice would be much appreciated.

---

### Post by Bucky Ball on 2012-10-01
You can store data in the extended partition??? You shouldn't be able to unless you have made logical drives which live inside it and are storing data on one of them. Is this what you mean?

As for the 512 misalignment don't know ... hopefully someone else will but this bumps your thread at least ...

---

