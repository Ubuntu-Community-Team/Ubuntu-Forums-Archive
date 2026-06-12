---
title: "where is my memory in lucid?!"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DLGandalf on 2010-04-07
due to circumstances, I temporarily have only 1GB of memory in my desktop. Now normally this isn't an issu and used Karmic for 2 months this way until I upgraded to Lucid, the system is ridiculously slow, top shows a freemem of 52MB and often no more than 100MB cached, swap is used first time in my life above 100MB currently at 400MB. Every action is invoking massive swapping. I've summed all the resident memory amounts and come no higher than about 350MB of programs in memory. I know there is a little overhead, but where the hell is the rest of my 1GB.

I used the following command to give an indication for programs in memory  + the sum
ps aux |awk '{sum+= $6; print sum"\t"$6"\t"$11 }'

If this is not a valid way to calculate memory usage, fine, but there is definitely wrong because the swapping is unbearable. I can't use it as a desktop under ubuntu, but I can play supcom2 under windows7 perfectly.

Some recommendations to check some paramaters?

---

### Post by ShadowDragon on 2010-04-07
Is it every boot the same story? Because I only know that ureadahead has an [issue](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715) that after installing a program, it does a reprofile and the trace buffer takes a bite of your memory. A reboot solves that...

But if ureadahead isn't reprofiling I have no direct idea what the issue could be...

---

### Post by Lollerke on 2010-04-07
You should do a clean install.

---

### Post by DLGandalf on 2010-04-07
reinstalls are for windows, and is the easy way out, besides my issue could be a serious bug in lucid and/or upgraders.

---

### Post by cariboo on 2010-04-07
Run top in a terminal, to see if there is anything running with a memory leak. Typically my system uses just over 400Mb on a fresh boot. After running for a couple of hours it's using just over 750Mb. I'm running the 64 bit version so if you're running 32 bit it should be quit a bit lower. 

I just checked my netbook running Lucid UNE, it's using just over 200Mb ram.

---

### Post by Didius Falco on 2010-04-07
Try running

```
sudo swapon -s
```

Look at the results and see if there is a "/dev/Ramzswap0" listed.

My pc tends to decide it needs to do that occasionally, particularly when I get a new kernel, even though I have 4 Gigs of ram and another 4 gig swap partition that has rarely, if ever, been used.

If it does show up, it's an easy fix, and to save time, I'll post how to do it now:

You need to delete 
```
 /usr/share/initramsf-tools/conf.d/compcache
```

You'll need sudo privileges to do so. Then run 
```
sudo update-initramfs -u
```

and reboot. After rebooting, you can run 
```
sudo swapon -s
```

to make sure you drove a stake through the heart of that memory vampire.

BTW, if you are running more than one kernel, you'll need to boot into each one and do the initramfs update.

Regards,

Didius

---

### Post by Longinus00 on 2010-04-07
top reports both resident and cached memory together. Use free to get an accurate report of "real" memory usage.

---

### Post by cariboo on 2010-04-07
Top will display what ram  individual processes are using, whereas free only gives you total ram usage.

---

### Post by DLGandalf on 2010-04-07
Ok it's ureadahead's fault, rebooting an extra time after a ureadahead profile is needed to release memory which isn't registered anywhere in apps like top.

btw Didius Falco, if you need initramfs to update all your kernels use the '-k all' parameter.

---

### Post by emarkay on 2010-04-07
```
top - 20:00:52 up  1:05,  2 users,  load average: 0.37, 0.26, 0.23
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.8%us,  5.9%sy,  0.0%ni, 72.6%id,  0.7%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   2061648k total,   973900k used,  1087748k free,    52500k buffers
Swap:  2104504k total,        0k used,  2104504k free,   624460k cached
```

Clean boot, just FF and Thunderbird run in this time.
Been having issues with CPU use and overheating, but presume this is Beta problems..

---

### Post by lavinog on 2010-04-08
I added a comment to the bug report to show how to free your memory after a profile.
I am going to work on a script that will do this automatically until this is fixed.

---

### Post by Longinus00 on 2010-04-08
> **cariboo907 said:**
> Top will display what ram  individual processes are using, whereas free only gives you total ram usage.

Yes I know the difference but many people do not realize the difference between the different types of memory usage. This makes free more "user friendly" in figuring out total memory usage. top is better at figuring out what processes are being the largest hogs.

> **emarkay said:**
> ```
top - 20:00:52 up  1:05,  2 users,  load average: 0.37, 0.26, 0.23
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.8%us,  5.9%sy,  0.0%ni, 72.6%id,  0.7%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   2061648k total,   973900k used,  1087748k free,    52500k buffers
Swap:  2104504k total,        0k used,  2104504k free,   624460k cached
```

Clean boot, just FF and Thunderbird run in this time.
Been having issues with CPU use and overheating, but presume this is Beta problems..

See my comment about using free and not top, you have over 1650MB of free memory.

---

