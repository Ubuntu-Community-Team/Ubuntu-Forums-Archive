---
title: "installation and partition trouble with 8.04"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by neilm327 on 2008-05-20
Hi all!!
I have a problem.
I am trying to install Ubuntu 8.04 on my Inspiron 8500 laptop.
I currently dual boot Windows xp pro and Ubuntu 7.04.
My plan was to leave the windows partition 100% intact and install 8.04 over the old Ubuntu partition.
When I fired up 8.04, I reached the partition section, and I was afraid to proceed, as it was only displaying 7.04. No windows.
I considered just going ahead with installing 7.04 and 8.04 side by side, and then manually deleting the 7.04 partition afterwards. (probably not a good idea right?)
Can anyone suggest a safe way to cleanly install 8.04, and not harm my windows partition? 
I would appreciate any help offered, and look forward to your replies.
Many thanks,

nEIL

---

### Post by iaculallad on 2008-05-20
No windoze? In the partition option of your Ubuntu LiveCD  installation, does it show any  NTFS partition?

---

### Post by neilm327 on 2008-05-20
Thanks for a quick reply.
There is no ntfs partition on the first option (guided partition) of the installer. It is asking me to resize my 7.04 install to make room for the 8.04 install. Judging by the space available between 7.04 and 8.04(not installed yet), it is only looking at my linux partition. (with the slider etc)
I dared to see what the manual partition option offered, and it shows me my swap partition, my 7.04 and my xp partition. However I am quivering in fear at the prospect of manually partitioning the drive.

---

### Post by iaculallad on 2008-05-21
Just select the manual partition method. But be very careful not to check the checkbox which says "format" within you xp partition.

With the manual partition, you will either see: Swap,/, and /home. Try deleting this partitions and recreate the partitions again. (Swap,/, and /home).

---

### Post by Healey on 2008-05-21
Hi

I want to do the same thing and would like to know the official way to do this.

How is it going ??

Regards

Healey

---

### Post by iaculallad on 2008-05-21
> **Healey said:**
> Hi

I want to do the same thing and would like to know the official way to do this.

How is it going ??

Regards

Healey


Try this official Ubuntu help on [Partitioning]("https://help.ubuntu.com/community/HowtoPartition").

---

### Post by neilm327 on 2008-05-21
So you suggest deleting my swap and original ubuntu partition and creating all new swap and Ubuntu partitions?(all i need is my swap partition, and Ubuntu partition...is it good practice to also create a "/home" partition?) 
 
I will back up my xp, and go ahead with the manual partition. I guess I needed some encouragement and reassurance(thanks).
And just to be absolutely sure, with manual partition, once the xp partition (or any other partition for that matter) is not selected, there is no danger of any harm coming to it?
Also creating a NEW partition would not affect windows in any way? (I'm just too aware of window's legendary flakyness)

Anyway,
Thanks very much again. I was really surprised at how quickly I recieved assistance, and on top of that you've been really great. Sorry if my questions lead to more questions :S

(I will have to continue tomorrow)

---

### Post by neilm327 on 2008-05-21
> **iaculallad said:**
> Try this official Ubuntu help on [Partitioning]("https://help.ubuntu.com/community/HowtoPartition").

I replied before seeing this. I will check the guide out when installing tomorrow.
Thanks for all your help.

---

### Post by iaculallad on 2008-05-21
> **neilm327 said:**
> So you suggest deleting my swap and original ubuntu partition and creating all new swap and Ubuntu partitions?(all i need is my swap partition, and Ubuntu partition...is it good practice to also create a "/home" partition?) 
 
I will back up my xp, and go ahead with the manual partition. I guess I needed some encouragement and reassurance(thanks).
And just to be absolutely sure, with manual partition, once the xp partition (or any other partition for that matter) is not selected, there is no danger of any harm coming to it?
Also creating a NEW partition would not affect windows in any way? (I'm just too aware of window's legendary flakyness)

Anyway,
Thanks very much again. I was really surprised at how quickly I recieved assistance, and on top of that you've been really great. Sorry if my questions lead to more questions :S

(I will have to continue tomorrow)

You have the option of not deleting your existing SWAP partition if you have an existing one or you still have the option of not deleting all your existing linux partition. Just be sure to corrent the mount-point (/ and /home) and check the format box.
There's no danger that this pose when you don't check on NTFS checkbox once inside the partition manager.
There's no threat when you decide to add/create a new partition.

---

