---
title: "Boot failure after installing 10.04 beta"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by opossumjack on 2010-04-05
Hi folks. I just installed Ubuntu 10.04 beta 1. Everything went fine, no errors at all (even the live CD worked flawlessly all the afternoon, I'm writing from it...)

But when I reboot after installation it says "No boot devices available"

What can I do? I also tried to look for GRUB using the terminal from live CD. It says no GRUB installed...

Any suggestion?    ](*,)

Thanks in advance

---

### Post by Mark Phelps on 2010-04-05
Issues and problems related to 10.04 need to be posted to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.

Will be asking the Mods to move this thread there for you.  Please look there for replies.

---

### Post by opossumjack on 2010-04-05
Ok...thanks a lot! I did not notice that post..

Hope someone will help me... :)

again, thanks.

---

### Post by opossumjack on 2010-04-06
Ok.. I solved this stupid problem... ;)

I think it was my fault.. 
I have 2 hard disks. I made this partitions

DISK 1
1. Main partition (mountpoint "/" )
2. Swap partition
3. Home partition (mountpoint "/home" )

DISK 2
1. Documents and datas partition (mountpoint "/home/archive" )

I don't know why, but I think that "/home" directory subfolder on the second Hard Disk somehow messed up my boot files...

I'm not sure about that. Is there someone who could just tell me if I'm right?

Now, everything installed fine when I removed the partition from second hard disk.

I'll keep you informed if anything happens again.

---

