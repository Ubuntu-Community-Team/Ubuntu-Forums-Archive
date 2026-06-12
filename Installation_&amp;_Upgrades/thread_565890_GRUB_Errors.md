---
title: "GRUB Errors"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by ruz322 on 2007-10-02
Hey everyone,
I used to have Windows and Ubuntu Feisty dual booting on my laptop. I recently deleted all the ubuntu partitions because I now have two separate laptops, one windows, and one ubuntu. I deleted the partitions using Windows Partition manager via right clicking my computer and clicking manage. Now grub is giving me errors on bootup. I tried using the gparted live cd editor but I couldn't figure anything out. Any ideas of how to get it back to booting straight to the windows partition properly without having to reformat? I have a lot of data on it!

---

### Post by Pumalite on 2007-10-02
Use your XP install CD to restore MBR
Boot from it>hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by Pumalite on 2007-10-02
If you erased the Windows partition, maybe you erased where Grub was installed. Could you clarify what you did in what computer?

---

### Post by ruz322 on 2007-10-03
I didn't erase the Windows partition. I just erased the Linux and linux swap partitions. I still have the Windows partition. The problem with that solution is that I don't have  recovery disc. It's windows vista and they gave me this gay little anytime upgrade disc which I don't know if it does the same thing or not. I'll try this afternoon though.

---

### Post by ljonesj on 2007-10-03
well i was doing the same thing on my xp laptop but i finaly bought myself a cheap laptop. an acer 3680-2682 which had vista basic on it wipped it out and put fiesy on it love this computer. my other laptop i have to redoi it as its screwed up again. the new laptop does the main job of surfing the internet and my media playback but my windows home laptop will do my games still and some internet stuff

---

### Post by confused57 on 2007-10-03
> **ruz322 said:**
> I didn't erase the Windows partition. I just erased the Linux and linux swap partitions. I still have the Windows partition. The problem with that solution is that I don't have  recovery disc. It's windows vista and they gave me this gay little anytime upgrade disc which I don't know if it does the same thing or not. I'll try this afternoon though.

You could try the Super Grub Disk to restore Vista's IPL to the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If this doesn't work, you could try reinstalling Ubuntu to a small partition temporarily & if you're able to boot into Vista, you could use this utility:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by ruz322 on 2007-10-03
> **confused57 said:**
> You could try the Super Grub Disk to restore Vista's IPL to the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If this doesn't work, you could try reinstalling Ubuntu to a small partition temporarily & if you're able to boot into Vista, you could use this utility:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Thanks a lot! That seems like it is going to work. I just need to be able to boot into my Vista partition at least one time and do the MBR fix. Thanks for your help!

---

