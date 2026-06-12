---
title: "Live boot usb with persistence now hanging on boot up"
date: 2020-02-24
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2020-02-24
Hello all,

I made a live boot-able thumb drive with persistence with Xubuntu 18.04LTS on it about 3 weeks ago for a disabled friend as described in this [thread]("https://ubuntuforums.org/showthread.php?t=2435736&page=2") that I started. It has worked well for the last 3 weeks, even if the boot up time tended to be long. I still have not gotten around to putting a new hard drive in the PC, the old one is shot/failing again as described in this [thread]("https://ubuntuforums.org/showthread.php?t=2435736&page=2") 

Today, however, it just hangs on boot up at the blue Xubuntu screen, see attached picture. I timed one of these hanging periods and it was still hanging at 25 minutes, when I shut the PC off. During one of these hangs I pressed ctrl+alt+t and got a black screen with readout and took some photos that are attached. The first two photos, screen 1 and screen 2 are somewhat out of focus, but the other 5 photos are in focus. Maybe these photos will be of help in diagnosing the problem. (Since I have discovered that I can't post all 8 photos in one post, I will post the final three photos the my next post.)

Interestingly, the PC will not shut off by pushing the power button when it is hanging, I have to unplug the PC.

QUESTION: Does anybody have any suggestions? 

At this point, I am inclined to just remake another live boot-able thumb drive with persistence with Xubuntu 18.04LTS on it and order a new hard drive ASAP.  

Thanks,

Able

[ATTACH=CONFIG]285081[/ATTACH][ATTACH=CONFIG]285082[/ATTACH][ATTACH=CONFIG]285083[/ATTACH][ATTACH=CONFIG]285084[/ATTACH][ATTACH=CONFIG]285085[/ATTACH]

---

### Post by AbleTassie on 2020-02-24
Here are the remaining three screen photos during the hang, when I press ctrl + alt + t and get a black screen with a read out.

Thanks,

Able

[ATTACH=CONFIG]285086[/ATTACH][ATTACH=CONFIG]285087[/ATTACH][ATTACH=CONFIG]285088[/ATTACH]

---

### Post by yancek on 2020-02-24
The images you posted show a failure to start some very basic programs.  The fact that you need to 'pull the plug' to stop the computer is unusual.  Could be  a hardware problem, could be a corrupt filesystem from an improper shutdown.  If it's a vfat filesystem on the usb, you can run the command suggested at the link below, explanation of the various options explained also.

[https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system](https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system)

---

### Post by AbleTassie on 2020-02-26
> **yancek said:**
> The images you posted show a failure to start some very basic programs.  The fact that you need to 'pull the plug' to stop the computer is unusual.  Could be  a hardware problem, could be a corrupt filesystem from an improper shutdown.  If it's a vfat filesystem on the usb, you can run the command suggested at the link below, explanation of the various options explained also.

[https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system](https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system)

Thanks Yancek,

I tried the solution at the link above. I ran the utility on each partition. It did seem to repair or attempt to repair each partition and gave an output for each partition. It seemed to give the longest output for the boot partition.

But it still had the problem of being unable to boot up with two different PCs. So I made a new live boot Xubuntu with persistence on the same thumb drive and this new drive boots up fine.

I will mark this thread as SOLVED.

Thanks,

Able

---

