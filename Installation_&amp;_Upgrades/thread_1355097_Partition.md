---
title: "Partition ?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by _Rich on 2009-12-14
Hello Ubuntu :)
I would like make another partition on my 64 bit Windows 7 laptop.
Can someone tell how much space is needed for the 64 bit Ubuntu 9.10 ?
Thanks
Rich

---

### Post by darkod on 2009-12-14
You should dedicate at least 25GB, and that's assuming you won't fill your ubuntu with music/videos/pics with large size. If you plan on putting large files, adjust that number depending what your plans are.
Shrink the win7 partition with the windows Disk Management, after that boot win7 few times to do its disk checks and to make sure it's happy with the shrink. Then boot with ubuntu cd, Install Ubuntu option, and tell it to use unallocated space you created.
Unless you prefer creating your own partitions in which case you select manual partitioning but read about partitioning for linux if you're new to the topic.

---

### Post by _Rich on 2009-12-14
Thank you darkod!
I have Ubuntu up and running. I did have some problems getting a Internet connection for a little while. I have a broadband air card in my laptop that I took out of the USB port and put back in. I think maybe that did the trick. When I setup the connection at first, it was not giving me a connection. I did try and reboot a couple of times but that did not work either. Oh well at least it is working now :D  I made a 30 GB partition in Windows 7, and I put Ubuntu in the unallocated space like you said.
Thanks again
Rich

---

### Post by _Rich on 2009-12-15
Hello darkod
I was wondering if you might be able to tell me if this is a bug in the grub loader or not?
When I boot up the computer I will get the Grub menu. If you look at it, you will see that the Ubuntu generic and the recovery mode is duplicated.

Is this normal?
Thanks
Rich

Ubuntu, Linux 2.6.31-16-generic **[COLOR=Red]<----[/COLOR]**
Ubuntu, Linux 2.6.31-16-generic(recovery mode) [COLOR=Red]<------[/COLOR]
Ubuntu, Linux 2.6.31-16-generic [COLOR=Red]<-----[/COLOR]
Ubuntu, Linux 2.6.31-16-generic(recovery mode [COLOR=Red]<------[/COLOR]
Memory test(memtest86+)
Memory test(memtest86+, serial console )[COLOR=Red]<--- left out the serial number in case it was personal information that I should not give out [/COLOR](I don't know I am a newbie to Ubuntu :D)
Windows 7(loader)(on/dev/sda1)

---

### Post by audiomick on 2009-12-15
Hallo.
It could be that the entries have just been duplicated somehow.
It isn't normal, I think. I also think it is not dangerous, so take your time looking into it. Hasty and ill-considered messing around in the grub menus is not such a good idea.

work your way through this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

then go into the files mentioned in the "file structure" section and see if the entries are pointing to the same instance or two different ones.

---

### Post by darkod on 2009-12-15
It's normal to have a separate recovery mode entry, in addition to the "normal" mode. But if you typed it correctly, your shouldn't have two 31-16 kernels. Are you sure one of them isn't 31-14 or 31-15?
If it is, that would be normal. You would have for example:
31-16
31-16 recovery
31-15
31-15 recovery
etc

---

### Post by _Rich on 2009-12-15
I'm sorry, I have been on the computer to long :(
You are right darkod, one is 31-16 and the other is 31-14.
When I saw 2 of them I overlook the numbers showing. #-o

Thanks audiomick and darkod, I appreciate the help.

---

