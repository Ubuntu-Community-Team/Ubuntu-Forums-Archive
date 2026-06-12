---
title: "Reinstall Taking Forever"
date: 2020-01-27
forum: Installation &amp; Upgrades
---

### Post by jcarr12 on 2020-01-27
Hello all,

I have been working with ubuntu for a while now and done several installs/ upgrades to various versions. Though I would not consider my self an expert by any means. 

I upgraded my work desktop to Ubuntu 18.04 a while ago and everything was working excellently. However, recently the computer crashed and my cursor became invisible but I could still click everything. I spent several days trouble shooting and following every suggestion I could find, to no avail. So I decided to reinstall Ubuntu 18.04, without reformatting the drives. I redownloaded the Ubunto 18.04 ISO file and formatted a live USB using rufus. I booted up in it an reinstalled. My first reinstall got hung up on the 'Starting Cleanup of Temporary Directories.' line for 2 days. I have since reformatted the drive again and attempt to reinstall again. This time it appears to be running but has been running the 'ubuntu CRON[11879]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)' for 3 hours now. 

In my prior experience reinstalling and upgrading has not been any trouble. Is there any thing that I may be missing or any advice that someone can suggest? 

Thanks for all of your help!

As a note: my ubuntu machine is still reinstalling and there don't appear to be any error messages, though I cannot use the machine...

jcarr12

---

### Post by CatKiller on 2020-01-27
Something is broken.

A fresh install, if you read all the screens, takes about 20 minutes.

My initial suspicion is that your hard drive is dying.

---

### Post by jcarr12 on 2020-01-28
Hello, 

Thanks for the comment! MY system eventually updated to 19.04; However, now it hangs on a purple screen after booting.
 I ran a thorough system test from the boot manager and all hardware passed. So I don't think my hard drives are failing. 

Do you have any other suggestions of what else may be an issue?

Thanks!

---

### Post by CelticWarrior on 2020-01-28
> recently the computer crashed and my cursor became invisible

This suggests hardware issues but not necessarily in the drives. My first guess would be something in the graphics but without further troubleshooting I can't tell it's hardware or software (drivers).

Please post your hardware specifications, particularly the graphics.

---

### Post by jcarr12 on 2020-01-28
Update: I gave up after trying most of the fixes online and having them do nothing. I just did a complete reinstall of 18.04 and erased all previous data. Incredibly inconvenient but I can now see my mouse and everything runs as it should...

Thanks for your suggestions though!

---

### Post by CelticWarrior on 2020-01-28
You're welcome.

That said, a few things you should keep in mind.

First is that the first hypotheses seems to have been confirmed, not the part of physical errors on the the drive you were installing Ubuntu to but other errors like a corrupted file system that were the root cause of the problem with the first attempt at reinstalling while keeping the same partitions. In the second attempt all went well because the partitions were formatted and that was what corrected the error.

Second is that my hypotheses was wrong, obviously. However, when asking for help and having any suspicion that it can be hardware related - not necessarily a suspicion about faulty hardware but also about what specific hardware need to work properly in terms of drivers and other software - always post the hardware specifications.

---

