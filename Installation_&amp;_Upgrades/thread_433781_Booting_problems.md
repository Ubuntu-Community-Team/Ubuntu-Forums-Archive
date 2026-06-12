---
title: "Booting problems"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Micieri on 2007-05-05
Well, 4 days ago my friend gave me a LiveCD that he requested a while back (Ubuntu 6.06). On that same day I installed Ubuntu with the CD, downloaded all the security updates, downloaded all the programs that I thought I would need, and it was all running perfect. My setup is: 2 HD's, one for WinXP, one for Ubuntu (both internal) I don't have a half bad computer either.. Pentium 4 3.12GHZ, 1GB RAM, GeForce 5600, but anyway back to the problem. It was running fine for the past 3 days, except yesterday I tried to boot from my second HD (Ubuntu) and it said something about 'no inittab file found', as instinct, I rebooted. Same happened again, 'no inittab file found', so I booted from WinXP, headed over to some unofficial Linux channels on IRC, and they told me to re-install Ubuntu. (I didn't think I needed the LiveCD anymore as it was installed, so I gave it away) The supporters told me to head over to Ubuntu.com, and download 7.04, so I did, and burned the ISO image to a CD, then when I booted from that CD -EDIT- after clicking Install/run Ubuntu -EDIT-, it said:
crc error
-
System halted
(I had no other choice but to reboot, and try again) So that didn't work either.. I headed back to the unofficial channels, they said it was beyond their knowledge now, and to head over to the official channel. So here I am today, I asked in the channel if anyone could help.. some tried to, but that just ended up failing too. I was then told to download the text version installer, so I did that, booted, and it worked fine! Except it kept freezing on Installing Boot Packages(I think?) I left it for a whole hour on end.. and it was stuck on 33%, so again, rebooted, and the same problem happened, but stuck on 31% this time. I rebooted ONE last time from it, and went to check CD for defects, and it said the CD was fine.. So what now? I've done everything I was told to do, looked through some help guides I found.. and it seems nothing has solved my problem.

---

### Post by zvacet on 2007-05-05
Maybe you can try to burn it very slow.I know that you allready doing install on two HD but look this page if it is any help for you

[http://ubuntuforums.org/showthread.php?t=275728&highlight=vista]("http://ubuntuforums.org/showthread.php?t=275728&highlight=vista")

---

### Post by Micieri on 2007-05-05
Sorry I forgot to mention my burning info.. I burned at maximum, 40x, 2x, 1x, and 3x, all with the same result

---

### Post by phidia on 2007-05-05
If you did the check cd for defects and the status of that was ok I think we can rule that out as the problem.
How are you partitioning and formatting the drive prior to begining the install?
I ask that because sometimes if you try to install over a previous install without formatting the partition where the system "/" will be you end up with these issues.

---

### Post by Micieri on 2007-05-05
I'm letting it format itself.. it gives me all the options, and I go to format.. just now though I used PartitionMagic and made a partition for linux.. maybe that'll get me somewhere?And maybe the text based installer won't freeze now :/

---

