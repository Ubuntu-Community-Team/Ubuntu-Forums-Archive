---
title: "how can make ubuntu the default now?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by couldbbetter on 2011-10-15
hey everyone, just installed 11.10, and by god youve finally done it ubuntu 11.10 is best faster then xp for me!!!. after literally getting a BSOD while multi tasking in xp just now, ive taken the plunge and decided to make ubuntu the default

ive deleted my xp partition, its gone, now just ubuntu on my computer! 

my problem is now one of partitions, 

i now have unallocated 124.01 gb partition that use to be xp (SDA1) now my partitions look like this

[B]unallocated - 124.01 gb
/dev/sda2 extended - 174.08gb
     sda6 ext4 - 92.96gb
     sda7 linux swap - 3 gb
     unallocated 2.64 MB
     sda5 ntfs - 78.12 gb (my backup partition, how it got moved into the ubuntu area i dont <snip> know!!)
unallocated 2.95 gb
[/B]
as you can see, im ready to use ubuntu full time.

ive downloaded gparted, and i dont seem to be able to do anything

i want to get that xp unallocated space into my SDA2 so i can use all my harddrive..

i couldent do anything so i figured its cause ubuntu is mounted right now so i boot into the live cd, gparted - same result

what the hell do i do now? i just installed ubuntu, i dont want to format and recreate my partitions, moreover how do i make my backup partition a logical partition again? i dont want it to have anything to do with ubuntu!

thanks!!!

---

### Post by CraigGB on 2011-10-15
have you tried right clicking every partition in gparted and clicking unmount?, the live CD automatically mounts every partition at startup

---

### Post by couldbbetter on 2011-10-15
thanks for the reply, ya man as soon as i swapoff the swap i can do w/e i want, but it seems that i might as well just format and reisntall fresh, because im going to have to eend up screwing around with grub, and it still says XP in my grub bootloader menu

so i guess i should just format :P

doubt theres a "clean" workout seeing as its a fresh install i wont lose much

thanks brew

---

### Post by raja.genupula on 2011-10-15
have you tried with disk utility in Ubuntu menu? 

you have removed your xp right then do this by opening your terminal to eliminate xp entry from grub menu

```
sudo update-grub
```

all the best

---

