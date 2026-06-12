---
title: "Confused with grub2"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-10-09
I have the alpha installed on another partition and since then I have added the beta of both Ubuntu and Kubuntu on new partitions. The problem is that the existing grub on the alpha partition is still being used. I've tried running the OS prober and the update command from inside the installation where i'd like the grub config to be the primary configuration.

Today I installed Kubuntu but the grub has not been updated at all so i cannot boot it.

Also, every time I run the osprober and grub update it damages my windows 7 configuration by omitting "root (hd0,1)" and leaving only the "chainloader" command. Why does it do this?

---

### Post by rubenverweij on 2009-10-09
I can only guess grub tries to chainload grub2, and that there goes something wrong either with loading grub2 or you'll have to update the grub2 config from inside one of your beta systems. Hope this helped.

---

### Post by dino99 on 2009-10-09
i've seen some updates few minutes ago that would take care about that problem.
So, update & safe-upgrade then reboot & see.

---

### Post by ozorba on 2009-10-09
My grub list does not get updated. It has been like this for the past 4 days. I have to edit the grub.cfg manually. Grrrr!

---

### Post by ranch hand on 2009-10-09
> **ozorba said:**
> My grub list does not get updated. It has been like this for the past 4 days. I have to edit the grub.cfg manually. Grrrr!
That must be fun with all the updates we have gotten that run update grub.

You have run;
```

sudo update-grub

```
yourself?

---

### Post by ranch hand on 2009-10-09
> **sonicb00m said:**
> I have the alpha installed on another partition and since then I have added the beta of both Ubuntu and Kubuntu on new partitions. The problem is that the existing grub on the alpha partition is still being used. I've tried running the OS prober and the update command from inside the installation where i'd like the grub config to be the primary configuration.

Today I installed Kubuntu but the grub has not been updated at all so i cannot boot it.

Also, every time I run the osprober and grub update it damages my windows 7 configuration by omitting "root (hd0,1)" and leaving only the "chainloader" command. Why does it do this?
I do not understand why you can not boot to Kubuntu.  This, from what I understand, is the last OS installed.  This should have installed grub2 on the MBR from that partition.  You should be booting into Kubuntu if into nothing else.

I would look at some of the files in Kubuntu and see if they are there (/boot/grub/grub.cfg, /etc/grub.d(make sure all files there) and /etc/default/grub).  I would also double check the msd5sum on the ISO and reboot to the disk and run a disk check.

You really should build a 06_custom file in /etc/grub. so that you don't have problems with stable OS'.  Your WinWhatever would be a good place to start. 

There is some information on that here and more in the links;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

You should be able to boot to all of your Ubuntu partitions with the "generic" (sybolic) menu entry and not have to worry about up dating them at all for kernal updates.

---

