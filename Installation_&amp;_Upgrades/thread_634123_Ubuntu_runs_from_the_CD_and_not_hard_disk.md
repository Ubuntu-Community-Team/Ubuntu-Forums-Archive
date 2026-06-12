---
title: "Ubuntu runs from the CD and not hard disk"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by punjabDaMunda on 2007-12-07
I have a 700 MHz processor, 384 MB RAM, 8 GB Hard disk old pc. It has 2 partitions Partition 1 is 2GB. Partition 2 is 6 GB. Both the partitions have XP Media Center installed (Please do not ask me why). I want to get rid of Windows on this box and just install Ubuntu.

I tried to install Ubuntu 7.04 yesterday on this machine. First I checked integrity of the CD. Which went through fine. Then I chose option 1 “start or install Ubuntu”. Everything went fine. I could see Ubuntu up and running within few minutes. 

I was surprised to see that it did not ask anything about formatting disk etc. Anyways… I was happy that it is up and running.

However, I realized later that it is actually running from the installation CD. When I take that CD out, it stops working.

What did I do wrong? Where should I specify that I want to wipe off my hard disk contents and install ubuntu.?

Please note that most of 2GB and 6 GB partitions, are full. So, there is not much HD space remaining. But that should not be a problem I guess, because my intention is to let ubuntu wipe out any existing data.

Please help. Thanks a million

---

### Post by Pumalite on 2007-12-07
You have to double click 'Install' icon on the top left corner.

---

### Post by punjabDaMunda on 2007-12-07
Wow, thanks for quick reply.

So, if i double click on that icon, i will have an option to wipe out my disk?

Another question I have is.. When it ran from CD, the PC was extremely slow. Is it because the CD drive is slow (8X I guess). So, will it be running faster after I install ubuntu on hard disk? Is 700 MHz fast enough for Ubuntu?

---

### Post by Pumalite on 2007-12-07
Post your complete specs.

---

### Post by .nedberg on 2007-12-07
Yes, running from CD is SLOW!

When you install it will be faster.

You will have an option "Guided, use entire disk" or somthing like that. This will erase the entire disk and install Ubuntu

---

### Post by lha on 2007-12-07
> **punjabDaMunda said:**
> 
Another question I have is.. When it ran from CD, the PC was extremely slow. Is it because the CD drive is slow (8X I guess). So, will it be running faster after I install ubuntu on hard disk? Is 700 MHz fast enough for Ubuntu?

As stated in an earlier post, Ubuntu runs faster from hard drive than cd. 700 MHz processor and 384 MB RAM is enough; I occasionally use a computer with 600 MHz CPU and 384 MB ram, and it's speed is acceptable. Not fast, but definitely usable. Your 8 GB hard drive is, however, a bit small. On the other hand, it is small for Windows, too...

---

### Post by Pumalite on 2007-12-07
With less than 512 MB, you cannot boot a Live CD, unless you make a 500 MB /swap partition ahead of time. You can use Gparted Live CD for that.

---

