---
title: "fat32 and fat16?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by darkwoofe on 2006-07-02
I'm trying to install on a dell diminsion 2400 with Windows XP. Everything on the live disc works great and I'd really like a dual install to really try it out before I switch.
The problem is that when I when to partition my drive, there were already three partitions there. One was the Windows Nt.., one was fat32, both of which I know what they're for, however there is also a fat16 partition. It's faily small and doesn't even use most of what is there. And I have absolutely no idea what it's for, so I didn't mess with it.
I freed up some space made a partition for the ubuntu without too many problems, but since there can only be four partitions, I can't make one for the swap without changing one of the ones already there.

What I'd like to know is, if anyone can give me a guess as to what that fat16 partition is for and will changing it to swap for ubuntu cause any problems? The only thing I can think of that it *might* be from is when I was trying out development servers, in which case, I don't need it. But I'm not really sure...
Also, with the partitions made, is there still the chance of messing up my windows install? And how hard will it be to switch over completely from the dual boot, if I decide to go with ubuntu?

---

### Post by Hubbins on 2006-07-02
If the fat 16 is at the beginning of the HD then if I recall it is a dell utility partition. Used to test your hardware and stuff like that. If thats the case then you can get rid of it if you don't use it.

---

### Post by darkwoofe on 2006-07-03
That's where it is alright. Thanks for the quick answer Hubbins! You wouldn't happen to know how hard will it be to switch over completely from the dual boot, if I decide to go with ubuntu?

---

### Post by Hubbins on 2006-07-03
I wouldn't know. I just installed linux for the first time on an old comp so I can't help you there. Good luck though.

---

### Post by simul on 2006-07-04
Hi darkwoofe,
I have the same problem as yours. If you found any solution please let me know.  I'm also communicating in this thread. 

[http://www.ubuntuforums.org/showthread.php?t=208578](http://www.ubuntuforums.org/showthread.php?t=208578)

Maybe could be a help for you too.

thanks,
simul

---

### Post by darkwoofe on 2006-07-04
I just deleted the fat16 partition, which was a dell utility partition, and created a swap partition with some free space. Both my Windows install and my Ubuntu install work perfectly, so...Sorry if that doesn't help.

---

