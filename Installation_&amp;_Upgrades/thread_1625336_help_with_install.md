---
title: "help with install"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by rcg40 on 2010-11-18
On October 9, I had a Dell GXS260 1Gig memory 80 gig HD, running XP-pro and Ubuntu 10.4.
I downloaded and burnt ISO's for Desktop and Netbook for 10.10.
the screen would get purple and blink 5 dots at me and then kill the keyboard and keep blinking the dots until it did it 15 times and then just get real quiet and just quit.

After looking at articles on installing, I have run the memtest and the disk check and I have burnt the ISO's at 4x rather that 32x.

I can boot back to XP (where I am now) and I can run Knoppix. Knoppix is a good way to look at /var/log/  for whatever that's worth.

Why the trial run does not work for UBUNTU is a complete mystery since KNOPPIX runs.

For future releases, I suggest that rather than five stinking, blinking dots, two number show up as in 38/657
meaning that we have finished step 38 of the 657 steps.

My questions: Should I delete the whole Linux partition?
 Is there something that I can rename or delete in the root directory that would alert the installer to try harder.
It seems that the installer goes so far and then just rolls over and does nothing. (fifteen minutes of nothing is nothing)

Is there a log of how far the live-CD has gone before it quits?

Why does GRUB use 10.10 on all of the 20+ options that he shows? I have been running Ubuntu Linux for about four years now and I think the earlier versions left the GRUB version intact. Not that I ever booted into an earlier one. 

I am losing interest in installing 10.10  or even trying to make the live-CD run.

Any help would be appreciated...

---

### Post by Zookalicious on 2010-11-19
Hi rcg40, sometimes on older computers, liveCD's can take a really rediculously long time to load up. With that said, if you are doing an upgrade, you do not need to use the live-cd. You can update your system to 10.10 by running the Update Manager and choosing to upgrade your version of Ubuntu. You might need to change your update settings if you do not see an option to upgrade to 10.10 (let me know if you want me to explain that). 

If you would like to do a fresh install with the CD, I would suggest doing a full backup of your files, then formatting your Ubuntu partition before trying the installation from the disk again. 

Let me know if you have any questions and good luck!

---

