---
title: "Fresh install 10.10 error: File not Found"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by 1angel on 2011-03-31
Hi There,

I did a fresh bare metal install of Ubuntu 10.10 64bits on my Dell Latitude E6410 8GB RAM and 160GB disk and everything works like a charm.
I upgraded to a 750GB disk and after installation I get:

error: File not Found
grub rescue>

I've been searching, trying to install GRUB2, but most results are for dual-boot, I don't want dual-boot, single OS, I'll use VirtualBox for other OSes.

Is something wrong with the 750GB disk? do I need to partition? that would be a bummer.

the funny part is that sometimes it boots and sometimes it doesn't, at some point I started installing the updates..... unfortunately I can't reproduce the "boot" sequence.... 
I'm stuck.

---

### Post by linuxn3wbie on 2011-03-31
I also have had an 'error 15: file not found' GRUB error, trying to install the very same version (10.10 - 64 bits on a 5 GB RAM / 1 TB HDD machine) for the very first time, and felt quite upset (seeing as I read everywhere that Ubuntu was one of the easiest to install Linux distros). I was searching around for answers on the wide web, but found nothing interesting either.

Actually, the solutions I came across messed it up more than it already was. I even got to the point that it'd show me another error (error 8: the kernel should be loaded before booting, or something like that :confused:)

I tried 2-3 times and failed every time. The fourth time, I tried again, this time armed with a CD with 'Rescatux' on it, and I performed the same steps as I did with the prior failed attempts. If it would have failed again, I would've tried Rescatux. For no known reason,  it suddenly worked, so I don't really know what the problem might be. I'd just advice to try again once more. If it then fails again, you could try to unleash [Rescatux](http://www.supergrubdisk.org/rescatux) on it.

Rescatux is known to fix GRUB errors, by reinstalling a fresh GRUB to the MBR. I didn't get to try it since Ubuntu magically installed on the fourth attempt, but I'd suggest this if things don't work out, as it does look promising.

---

### Post by IWantFroyo on 2011-03-31
Burning a new iso would be advisable.

---

### Post by 1angel on 2011-03-31
Well, I tried and tried mixing things, (I'm installing from a Live USB) and as I mentioned it worked like a charm on the 160GB disk, it worked the first time on the 750GB, but nothing worked, I did a manual isntall of GRUB and tried other "fixes" to no success.

I am swapping OpenSolaris as my main OS for Ubuntu, so I need to make it work, pronto! this is my main Work tool and I am trying really really really hard to avoid touching the windows system I got a spare.

So my fix was:

Create 3 partitions
#1 - Primary for Linux 100GB
#2 - Extended 25GB
#3 - Primary for /home 675GB

I hate to partition that way as I feel I'm leaving a lot of space sitting there waiting for nothing, I'll prefer to have one single big partition for Ubuntu + /home, so if you guys come across a solution, let me know.
I'll continue browsing for answers.
thx,

---

