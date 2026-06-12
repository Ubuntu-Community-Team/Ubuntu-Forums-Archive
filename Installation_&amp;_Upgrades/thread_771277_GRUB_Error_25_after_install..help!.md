---
title: "GRUB Error 25 after install..help!"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by hardergj on 2008-04-27
Hi,

I've just finished installing 8.04.  Upon reboot, when GRUB is loading, I get an error 25.

I've installed a dual-boot setup - ubuntu on a separate drive (slave), while XP is on the master HD.

I have no idea what to do to fix this.  Does anybody have any suggestions??

Thanks,

Greg

---

### Post by Pumalite on 2008-04-27
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)

---

### Post by hardergj on 2008-04-27
> **Pumalite said:**
> This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)

I tried setting the HD's to LBA; this doesn't fix the issue.

If nobody knows what the issue is, that's okay.  The biggest problem is that I can't even boot into Windows now (not even from the option on the CD).  Help!

Greg

---

### Post by Pumalite on 2008-04-27
You can fix your Windows MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by hardergj on 2008-04-27
Thanks for the quick replies.  I am obviously in over my head here, and need some time to figure this out.

In the meantime, what is the best way to just be able to boot into Windows?  My desktop is pretty much stuck until I figure the problem out.

Thanks,

Greg

---

### Post by Pumalite on 2008-04-27
Fixing your Windows MBR is your only way for the moment.

---

### Post by hardergj on 2008-04-28
Hey,

Just FYI - I re-installed Ubuntu onto a separate partition on my primary HD, rather than on it's own HD.  Everything is working out great now (at least with respect to the install...).

Now once I get my MX5000 keyboard working properly, I'll be happy!

---

### Post by Pumalite on 2008-04-28
Congrats.

---

### Post by Macdelaney on 2008-04-28
i had a similar problema regarding vista, i think i messed up when i formatted the ubuntu partition (where XP used to be) as Primary partition, should this have been a logical partition?
i also tried booting with the vista cd, going to the command prompt, and typing "fixmbr", but an error pops up.
Any ideas regarding this? Please, i need my windows set up for work, and cant really get it to boot right now

---

### Post by Macdelaney on 2008-04-28
i had a similar problema regarding vista, i think i messed up when i formatted the ubuntu partition (where XP used to be) as Primary partition, should this have been a logical partition?
i also tried booting with the vista cd, going to the command prompt, and typing "fixmbr", but an error pops up.
Any ideas regarding this? Please, i need my windows set up for work, and cant really get it to boot right now
Also, Vista's partition is /dev/sda3, when i edit grub, i should put (hd0,2) right? i've also tried with (sd0,2) but nothing seems to work

---

### Post by Pumalite on 2008-04-28
If you had Vista, you should have partitioned with the Vista partitioner. Beyond that, Ubuntu works great in a logical partition. So, after you make the unallocated space, you can make an extended partition and stick inside as many logicals as you want. Don't forget that 4 primaries is the maximum you can have in a HDD.

---

### Post by Macdelaney on 2008-04-28
i did partitioned with the vista partitioner, but i reformat (from within the Ubuntu Instal) the one where XP was, formateted as Primary and tossed Ubuntu in there . Might this be the problem?

---

### Post by Pumalite on 2008-04-28
The only problem that I can see from here is the 4 primary limit. If all you had was one primary left, Ubuntu couldn't install there because it needs 2 partitions: '/' and /swap.

---

### Post by Macdelaney on 2008-04-28
i also created a swap partition, just 4gb, is that too little? i've been trying everything that comes to my mind but im lost here

---

### Post by Pumalite on 2008-04-29
If you have 2 GB of memory; 1 GB for /swap is more than enough.

---

### Post by Macdelaney on 2008-04-29
i have 4 GB of memory, so 4GB would be more that enoght.
i reinstalled ubuntu into the same partition hopping it will detect Vista but it sure does not. I think what i have to do is add manually Windows to the menu.lst, but cant seem to get it right. 

UPDATE: Now i cant even see the windows partition from within linux. Might be because before reinstalling ubuntu, i installed vista again ontop of the ubuntu partition to see if the boot loader would fix everything. :S
I'm in a pretty messy point right now, any help?

Edit: I managed to mount it in a folder, the whole partition is in /dev/sda3
this would mean i have to add this to menu.lst?

title Windows Vista
root (hd0,2)
savedefault
makeactive
chainloader +1

Edit2: I've tryed adding that, but i get the same "NTLDR.exe is missing" error, any ideas would be much appreciated.

---

