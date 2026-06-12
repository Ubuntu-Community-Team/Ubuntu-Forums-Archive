---
title: "Ubuntu + Win7 Dualboot on 64GB SSD - how to partition"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2011-04-02
Hey guys!

I just got myself a shiny powerful new PC, and I want to dual-boot Windows 7 Home Premium 64 bit and Ubuntu (all future versions) from the same 64 GB SSD drive.

The actual space I have available on the SSD is ~60 GB, and I'm really on the fence about how to partition. I was thinking something like this:

- 45 GB for Windows
- 15 GB for Ubuntu

Now, I know that Windows needs 20 GB for a basic installation and 12 GB for the pagefile (I have 8 GB RAM, times 1.5, that's 12). There goes 32 GB right there, and that's without Service Pack and any of that jazz installed.

Here are my questions...

[LIST]
[*]How does the Swap area work in Ubuntu? How much of it should I set up with 8 GB RAM installed?
[*]Will I lose a lot of performance if I put both my Windows pagefile and the Linux swap area on my traditional 500 GB hard disk, as opposed to the fast SDD?
[/LIST]

Hope you can shed some light! Thanks :-)
Matt.

---

### Post by cbowman57 on 2011-04-02
With 8 GB RAM I wouldn't worry very much about it unless you do extremely heavy graphics or movie editing.  Ubuntu will likely never use the swap with that much memory available, but I think the old rule was 1/2 of physical RAM, which I don't really think applies any more.  

Not sure about Windows but based on your normal use do you think you will actually have a need for 12 GB virtual memory? 

You won't lose performance with Ubuntu but if memory serves me correctly Windows will always swap some out if it's available, which will affect it's performance.

To assure that Ubuntu stays in RAM, unless it's really pushed hard, add this to the end of your /etc/sysctl.conf file: vm.swappiness=1

---

### Post by The Bright Side on 2011-04-02
Thanks Chuck.

I think actually the old rule was even "amount of physical RAM x2". But yeah, it really looks like in Win7, you shouldn't actually give more than your actual amount of RAM to the page file, and it's already included in the 20 GB when you install Windows.

Even better, I can free up 6 GB of hard disk space in Windows by turning off Hibernation, which I never use. That way, the huge hiberfil.sys gets deleted, shrinking my basic Widnows installation down to 13-14 GB. Still a good idea to leave the pagefile where it is, i.e. on the SSD drive, since it seems an integral part of Windows' operations while Ubuntu completely ignores its swap space unless physical RAM is full.

I will give Ubuntu 4 GB swap to be on the absolute safe side, though the heaviest I do is retouch photos (10 megapixels) with GIMP. I will put that swap space on the non-SSD drive though, since I really don't expect Ubuntu to ever use it anyway. That way, I get plenty of SSD drive space to use for both Windows' and Ubuntu's system files. For Ubuntu, "Home" and "Swap" will go on the 500 GB disk, and so will most of my games in Windows.

I only keep Windows around to play games to begin with, what with Duke Nukem Forever and some other treats coming out.

Thanks again!

---

### Post by cbowman57 on 2011-04-02
I think you're right, Windows was x2 and Linux is 1/2 or equal to actual RAM.  That vm.swappiness=1 will keep ubuntu from using swap unless it becomes critical.  I only have 2 GB and with that setting on my machine the swap never gets used.

I really think the old rules for swap size need to be revamped for modern hardware.

---

