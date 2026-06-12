---
title: "[SOLVED] Newbie - Recovery failure"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by luangwa on 2008-08-03
I am a newbie with just enough windows computer knowledge to get me in trouble. I installed Ubuntu 7.04 on my Dell 8250 with a dual boot to XP pro. I installed all the files that Ubuntu prompted me to install. I then tried to update to 7.10 and let it run over night to install. In the morning it was stall in "Auto....". Nothing appeared to be happening. No working sounds from the computer and no response from the mouse or keyboard. So I shut it off and rebooted. The screen gave me 4 choices. I started with the first and a window popped up that it didn't recognize something and would be running in VGA mode. I clicked continue and logged on. All I got was a tan colored screen with a larger mouse arrow. The screen stayed the same even though I gave it 2 hours to finish..nothing. I get the same response in the other 3 choices including the recovery mode. Is there any way that I can fixed this using Ubuntu 7.04 CD? I would prefer not having to do the old Windose Two step...format and reload.

Thanks for your anticipated assistance.

---

### Post by Rocket2DMn on 2008-08-03
I think your best bet is to just reinstall the Ubuntu part of your dual boot, but use the latest version of Ubuntu - 8.04 Hardy Heron.  During the install process, you need to make sure you tell it to overwrite the existing partition rather than using the default which will create a new partition for this install (you don't want a triple boot).  This may require you to use the manual partitioning feature.

---

### Post by zvacet on 2008-08-03
As **Rocket2DMn** suggested best way is to install Hardy heron 8.04.In installing process select manual way and then **delete **Ubuntu partition and on that **free space** install Hardy.You can keep your swap and if you didn´t have separate home before make one now.Give ~10GB to the root partition (mountpoint /) and rest for home (mountpoint /home).You allready know size of your swap.

---

### Post by jmg on 2008-08-03
Same thing happened to me.  After receiving the cd in the mail, I waited 6-8 months before installing because I was afraid of the partitioning process.  I finally decided to go ahead.  I had the same problem.  Everything hung up during the boot.  This is not the end of everything.  The main thing now is to get up and going on ubuntu - no matter which version.  The version can be upgraded later.  Even if you have 3 or 4 partitions after you get going, it can be fixed. (I ended up with 3 and decided to keep it that way.  1 with 7.1- 1 with 8.04- and 1 with xp).  Just get back up and repost with new questions.  These people on this forum are the best and very patient.

---

### Post by luangwa on 2008-08-03
Won't this install another partition in the boot portion of the disk?

---

### Post by luangwa on 2008-08-03
You make it sound so easy...the trouble is I don't have the technical know how to accomplish the task. I would probably wind up formatting and reloading...don't want to do that. I am afraid I need a step by step method of erasing the faulty install and then install 8.04 from a cd.

---

### Post by luangwa on 2008-08-03
Thanks for your suggestion but I want to remove the faulty install first and then install 8.04.

---

### Post by obrecht72 on 2008-08-03
Your not alone luangwa. I did the same thing.
But, I have files saved on the current messed up part I don't want to loose.

Dear more experienced Ubu'ters,
Am I going to have to backup these files on external HD or is there a way to just overwrite to new 8. ver with disk and hope the files are still there?

Thanks,
Obrecht out...

---

### Post by luangwa on 2008-08-04
Thanks to all for your help.

---

