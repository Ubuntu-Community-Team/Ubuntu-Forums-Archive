---
title: "Your opinion on installing ubuntu feisty fawn."
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by StevenEpic on 2007-08-14
ok so lately my wp was been acting up with spyware and stuff. and i fixed it two days ago. no more spyware. my system is looking sleek at the moment. no hangups, no nothing. but i wanted to install ubuntu. i want both os'es, because my brother uses windows and is more loyal to it than anything else.

i know that you can make partitions, and install ubuntu on one of them. so heres the deal. i have 149 GB on my harddrive. free space i have 85.55 gb left. i have a Pentium 4 CPU at 2.80 GHz. 3.11 GHz, 1.62 of RAM. i want to do this easily.

i have Acronis Disk Director Suite, and i know you can make partitions there. i only have one harddrive.

i want to know what your opinion is, the amount of space i should partition from my harddrive, to have a good looking ubuntu kinda like [[COLOR="DarkRed"]this[/COLOR]]("http://youtube.com/watch?v=xC5uEe5OzNQ"), [[COLOR="DarkRed"]this[/COLOR]]("http://youtube.com/watch?v=E4Fbk52Mk1w"), maybe [[COLOR="DarkRed"]this[/COLOR]]("http://youtube.com/watch?v=YcsoJb_hjQU"), but mainly like [[COLOR="DarkRed"]this[/COLOR]]("http://youtube.com/watch?v=4JYokZ4rv-0").

i really want to install ubuntu, having a good amount of space to make it look that good, and still have a good amount of memory in my windows.

oh one question, if i make a partition, can the ubuntu partition write to the windows partition?



please tell me what you think. :]

---

### Post by merlinus on 2007-08-14
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would not let acronis or anything else but ubuntu or gparted live cd do the partitioning, unless you are running vista.

-merlin

---

### Post by StevenEpic on 2007-08-14
may i wask why not? sorry im like, curious :)

---

### Post by merlinus on 2007-08-14
My opinion is based upon my experience using partitioners such as Norton Partition Magic and other third-party, non-open-source products.

That is why I switched to ubuntu in the first place.

ymmv....

-merlin

---

### Post by StevenEpic on 2007-08-14
ok then :]

would you recommend this partitioning scheme?
[IMG]http://img379.imageshack.us/img379/6626/partitioning4mz5.png[/IMG]

---

### Post by merlinus on 2007-08-14
You might want to create a separate /home partition, which stores configurations and preferences.  It will make upgrading and/or reinstalling much easier.

Good info here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Also, there is no need to use fat anything -- they are inferior filesystems.  With the correct drivers installed, ubuntu can read-write ntfs, and windows can read-write ext3.

-merlin

---

### Post by StevenEpic on 2007-08-14
but, on that article or whatever, it says they cant. :?

---

### Post by merlinus on 2007-08-14
Really???  I just looked at it!

asiu specifically mentions ntfs-3g and fs-driver toward the bottom of the page.

"This last dual-boot scenario is my favorite now that I know about [FS-Drive]("http://www.fs-driver.org/"), which is a small program that allows Windows to read from and write to Ext3 partitions. So FAT32 can go out the window&#8212;one less partition to worry about and none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB)."

-merlin

---

### Post by StevenEpic on 2007-08-14
oh pardon me :]

so that is a driver? so if, lets just say, i want to install the ubuntu os ti the minimum space needed, i can save ubuntu program files like beryl, saved on my windows partition?

and will that make 4 partitions, windows, ubuntu, home, and swap?

---

### Post by merlinus on 2007-08-14
Beryl is a linux program, and therefore runs on a linux filesystem.

You can share data between the two os'es using either ntfs or ext3, not programs.

-merlin

---

### Post by StevenEpic on 2007-08-14
so my partition can look a bit like this? 
[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

with my windows partition being the biggest one?

so lets say i want the whole ubuntu and /home partitions to not eat up my whole hard drive. to take up, about, 35 gb.

will that be ok?

look here is my harddrive measurements
[IMG]http://img505.imageshack.us/img505/9382/untitledph8.png[/IMG]

will that be ok?

---

### Post by merlinus on 2007-08-14
No, /home should be a separate partition, and shared data separate as well.

With some 80G free, you might want something like this:

/ = 20G
/home = 5G
/swap = 1.5G
shared partition (formatted as ntfs or ext3} = whatever is left

I would also leave xp in a primary partition, and then create an extended partition for the rest.

-merlin

---

### Post by StevenEpic on 2007-08-14
is the shared partition really neccesary?

and "/" is the ubuntu os right? does it really take 20g's?

and if i want my wondows partition to be the biggest one, can i do that?

sorry for all the questions :?

---

### Post by StevenEpic on 2007-08-14
oh oh! and creating an extended partition, for EACH other partition? meaning extended partitions for /, /home, and swap?

---

### Post by merlinus on 2007-08-14
You can reduce or increase as desired.  If you will not be installing many linux apps, then / can be 10G.

I would keep /home separate from the shared partition.  You can reduce it to 2-3G.

And is xp not already the largest?  Looks that way from your pie chart.

An extended partition can contain oodles of logical partitions, whilst you can only have four primary.  The extended takes up no room on its own, but makes space in which to create logicals.

So /, /home, /swap and shared data can be logical partitions.

-merlin

---

### Post by StevenEpic on 2007-08-14
so the shared partition is needed?

after install, my hard drive measurements would look a bit like this?

[IMG]http://i12.tinypic.com/53uic1c.png[/IMG]

and i beleve ubuntu comes with a dual boot thingy, is that right?

---

### Post by merlinus on 2007-08-14
Yes, but what is the blue unused space?

Info here on dual-booting:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Also, with xp, before installing ubuntu --

Delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after installing), and defrag several times.

-merlin

---

### Post by StevenEpic on 2007-08-14
> **merlinus said:**
> Yes, but what is the blue unused space?

its the space already used. :]

ok then. im gonna take a show at it.

how do i set virtual paging to zero?

and inst deleting the temp folder bad?

thanks again for the help mate :]

---

### Post by merlinus on 2007-08-14
The space already used by windows?

Do not delete the temp folder, only the files within it.

Use the Help feature to find virtual paging, but it is probably somewhere under System Tools.

Remember to back up important data, and defrag several times after setting virtual paging to zero.

-merlin

---

### Post by StevenEpic on 2007-08-14
no, the files that i have stored in my harddrive

like my music and pictures and stuff.

and i am, :]

---

### Post by StevenEpic on 2007-08-14
ok, so, how do i create a good planned partition change? i want to know how to make the partitions, leaving 20 extra gigs for the windows one, 20 for the ubuntu, and the rest, for /home, swap, and shared. and is the shared really really necessary.

please give me your opinion on a good partition plan :]

---

### Post by merlinus on 2007-08-14
Read this:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

-merlin

---

