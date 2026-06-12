---
title: "Installing Ubuntu on a 500GB HDD"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by urbentom on 2011-07-06
Hello 
im currently running windows 7 on my 2TB hard drive and i wanted to install ubuntu on my 500gb internal hdd. Can anyone take me through how much memory i should use for the / , /Boot , /Home and swapt parts of my hard drive?

---

### Post by snowpine on 2011-07-06
> **urbentom said:**
> Hello 
im currently running windows 7 on my 2TB hard drive and i wanted to install ubuntu on my 500gb internal hdd. Can anyone take me through how much memory i should use for the / , /Boot , /Home and swapt parts of my hard drive?

The Ubuntu installer will automatically choose the optimum partition scheme for you.

If you want to do it yourself then a good rule of thumb is:

10-20gb for /
twice your RAM for swap
the rest for /home

/boot is gnerally not considered necessary for Ubuntu.

Good luck! :)

---

### Post by wkulecz on 2011-07-06
These days partitioning is way more trouble than its worth.  You need a swap partition, twice your physical RAM is plenty, make the rest be /

Anything else requires clairvoyance as to what will fill up first.

---

### Post by urbentom on 2011-07-06
cheers this has helped me alot :) i didnt want to mess up and have to start again of even worse mess up my PC side of my computer

---

### Post by oldfred on 2011-07-06
You want to keep Ubuntu separate from Windows. I also prefer some partitioning, but you do not have to add any.

But you do want to use manual install (Something Else in Natty) to let you choose to install grub2's boot loader into the MBR of your 500GB drive. It normally defaults to install grub's boot loader to sda which usually is the windows drive unless you tell it to install to sdb.

With manual install you have to then at least define / (root) & swap partitions.

Lots of info, not as difficult as it may seem since many details/explanations included.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

