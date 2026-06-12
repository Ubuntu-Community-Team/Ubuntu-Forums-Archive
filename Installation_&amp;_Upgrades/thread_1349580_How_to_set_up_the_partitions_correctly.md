---
title: "How to set up the partitions correctly?"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Borrot on 2009-12-08
Well, first of all I've to say that I'm very new in this ubuntu world. Because of this I got some questions about how to set up the partitions correctly(and yeah, I've been searching around the net but I can't find what I want).

Okey, I'll take this from the beginning. Yesterday I decided to install ubuntu. I downloaded the CD and burned it. Everything works but I just don't know how to set up the partitions. I've already created an "unallocated" partition at 140.91 GiB. I know how to create new partitions but I don't know how they should be.

Maybe you can help me with telling me some steps about how I should set everything up.

Here is some information that may help you:
[IMG]http://i48.tinypic.com/16hu3k3.png[/IMG]
*I'll create everything with ubuntu to do in the "unllocated" partition.*

I'm using the pre-installed program "GParted" to create new partitions. 

So, how many partitions do I have to create, what labels should they have, what type of partition should it be e.g.

Feel free to post some links to a thread, a youtube clip a guide or something else that can help me.

*Sorry for the bad English, I'm from Sweden.*

---

### Post by phillw on 2009-12-08
> **Borrot said:**
> Well, first of all I've to say that I'm very new in this ubuntu world. Because of this I got some questions about how to set up the partitions correctly(and yeah, I've been searching around the net but I can't find what I want).

Okey, I'll take this from the beginning. Yesterday I decided to install ubuntu. I downloaded the CD and burned it. Everything works but I just don't know how to set up the partitions. I've already created an "unallocated" partition at 140.91 GiB. I know how to create new partitions but I don't know how they should be.

Maybe you can help me with telling me some steps about how I should set everything up.

Here is some information that may help you:
[IMG]http://i48.tinypic.com/16hu3k3.png[/IMG]
*I'll create everything with ubuntu to do in the "unllocated" partition.*

I'm using the pre-installed program "GParted" to create new partitions. 

So, how many partitions do I have to create, what labels should they have, what type of partition should it be e.g.

Feel free to post some links to a thread, a youtube clip a guide or something else that can help me.

*Sorry for the bad English, I'm from Sweden.*

Hi and welcome to the forum.

Two places for you, firstly the general one --> [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And, then one that has the how-to --> [http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

Just bear in mind that some HP's are causing problems when you boot back into windows where Ubuntu 'vanishes' - If this happens, post back & we'll get it sorted.

Regards,

Phill.

---

### Post by darkod on 2009-12-08
You don't need Gparted in advance. Since you have unallocated space, during the install process it will allow to create partitions there. First make a plan how big the partitions will be. If you want separate /home partition which is good practice, you don't need more than 20-25GB for /. For swap usually it's enough same as the size of your ram, but no less than 2GB. The rest remains for /home, but calculate how much is this because it's better to create /home before swap and you need to know.
Boot with the cd and select Install Ubuntu. At step 4 select Manual partitioning. The partitioner will open.
In the unallocated space create a logical partition for /, filesystem ext4, with the size you decided. Set mount point as /.
Then create another logical partition for /home, ext4, size as much as you want, mount point /home.
Then the emaining space of the 140GB will be for swap. Create another logical partition, filesystem swap area, mount point swap.
That's it.

---

### Post by presence1960 on 2009-12-08
> **Borrot said:**
> Well, first of all I've to say that I'm very new in this ubuntu world. Because of this I got some questions about how to set up the partitions correctly(and yeah, I've been searching around the net but I can't find what I want).

Okey, I'll take this from the beginning. Yesterday I decided to install ubuntu. I downloaded the CD and burned it. Everything works but I just don't know how to set up the partitions. I've already created an "unallocated" partition at 140.91 GiB. I know how to create new partitions but I don't know how they should be.

Maybe you can help me with telling me some steps about how I should set everything up.

Here is some information that may help you:
[IMG]http://i48.tinypic.com/16hu3k3.png[/IMG]
*I'll create everything with ubuntu to do in the "unllocated" partition.*

I'm using the pre-installed program "GParted" to create new partitions. 

So, how many partitions do I have to create, what labels should they have, what type of partition should it be e.g.

Feel free to post some links to a thread, a youtube clip a guide or something else that can help me.

*Sorry for the bad English, I'm from Sweden.*

Since you are new the easiest way is to boot the Ubuntu Live Cd and when the partitioner windows appears choose "Use largest continuous free space". That will install Ubuntu to that unallocated space and it will auto create / (root) & swap partitions for you.

Or you can create an extended partition in the free space, then make 15-20 Gb logical partition for /, a swap partition equal to your installed RAM and /home with whatever you need out of remaining space. /, swap & /home are all logical partitions inside the extended partition.

---

