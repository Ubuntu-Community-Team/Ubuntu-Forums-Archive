---
title: "RAID5 install"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by ingo on 2006-11-07
Hi,

I fancy trying out a RAID 5 install, but am not quite sure how to go about it (apart from the alternate CD). First hurdle would be the partitioning (I've got an hda and an sda, both with ample space), second the install itself and three all the pitfalls which you may have encountered. 

Nevertheless the security and speed of it all intrigues me :) 

Any hints, general advice would be much welcomed:KS

---

### Post by kidders on 2006-11-07
Hi there,

How to go about setting this up depends on whether you want your entire system running off RAID. I use RAID quite a bit, but personally, I always consider my base system itself to be expendable, and only mount things like /home on RAID devices.

What did you have in mind?

---

### Post by ingo on 2006-11-07
I'd probably want to have / and /usr and /home on separate partitions 'cos of the different file shelve lifes. Might as well have RAID5 for them all (and just for fun a normal install to see whether there is any difference in speed).

Is that enough info? Thing is I read the wikipedia article on RAID, but that is just about as incromprehensible as they come :(

---

### Post by kidders on 2006-11-07
Since you're just experimenting, you might as well take things in stages. That way, you won't have to know *everything* right from the word go, and you won't have to risk ruining your system. Assuming you're planning on using software RAID, here's what I would do...

[LIST]
[*]Since you've your sights fixed on RAID 5, create three identical partitions on three different physical disks. This is _absolutely essential_ (but you probably already know that). Let's call them /dev/sda3, /dev/sdb3, /dev/sdc3. Between them, they should be at least 33% bigger than you think would be useful.
[*]Many HOWTOs involve using the **mkraid** utility to set up the RAID devices, although this is just a convenience tool. **mdadm** is the *real* master of software RAID. Set up a /dev/md0 for yourself, and do a **cat /proc/mdstat** to convince yourself it's alive.
[*]Now, format and mount it as you would any other block device. (When choosing a filesystem, bear in mind that your choice will have a significant impact on performance.) Let's say you've mounted it to /mnt/test.
[*]Next, I would copy a movie or something onto it, and experiment with disaster recovery. The first time I used RAID, it was all very new to me, and I felt a little unsure of myself. This helps :-) Try screwing around with the array, and watch it put itself back together again when you give it its disks back. Just be careful not to foul up more than _one_ disk at a time!
[*]Now add a line to /etc/fstab to have /dev/md0 mounted at /mnt/test, and reboot. With luck, your system will magically figure all the rest out on its own.
[*]Once you're this far, it's time to move /home, say, onto it. If you need help, I'd be happy to talk you through it. Then, you can do it all over again for /usr, and finally for / itself.
[/LIST]

Since your stroll through Wikipedia seems to have been fruitless, let me know if you have questions ... PM me or post them here :-)

---

### Post by ingo on 2006-11-25
Right kidders, just noticed your detailed mail (a little late, I know). Have installed Kubuntu but am perfectly willing to give it another go (got enough disk space after all) following your info. Will be away from home for a while but will take you up on your offer when I back :)

Cheers

---

### Post by kidders on 2006-11-25
Sounds good :-)

---

