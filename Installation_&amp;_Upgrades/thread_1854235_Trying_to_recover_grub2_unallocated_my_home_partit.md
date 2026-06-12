---
title: "Trying to recover grub2 unallocated my /home partition!"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by espartano on 2011-10-04
Hello everyone!

I have Ubuntu 11.04 on my Dell Vostro 1400. I always have a / partition and a /home partition. 

I installed Windows 8 on a separated partition (that belonged to Windows 7) to give it a shot.

Ok, tested, now I had to recover my Grub2. I used the following commands:

sudo -i
mount /dev/sda3 /mnt (sda3 is my / partition)
grub-install --root-directory=/mnt/ /dev/sda

It gave a strange warning about my sector50 being used by NetFlix (that had never happened before). I thought, ok, strange, better back everything up - but it was  too late. My sda4 (/home) was UNALLOCATED. I lost a lot of stuff. 

Is there a way to even try to recover whatever files I can? Or everything is forever lost?

Thanks everyone!

---

### Post by espartano on 2011-10-04
Found a solution! This link ( [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) ) has everything I might ever need to recover files or partitions.

I was able to use testdisk to recover the lost partition. 

Thanks!

---

