---
title: "My server is trashed!"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by ledlincoln on 2007-09-09
I've been a very satisfied user of Ubuntu 6.10 server.  Last night, pretty much on a whim, I decided it was time to upgrade, so I ran apt-get dist-upgrade.  Well, it successfully downloaded a few hundred new packages, removed all the old ones, and QUIT, leaving me with an empty shell of a server.  My first clue was when I tried to restart and found that the shutdown command no longer existed on the server, and indeed, the /sbin directory is missing most commands including the init script, and most of the distro is gone.  As you might expect, it will no longer boot, leaving me at an initramfs prompt.

This is not intended to be a rant; I just want to know how I can restore the server without losing my data and settings.  The important stuff is in /var/www and some mysql dbs.

---

### Post by GMachine_24 on 2007-09-09
Hi:

Sorry to hear about your problems. I have not attempted an Ubuntu "upgrade" since my first one ended with a disaster such as the one you are describing.

Here, again, as always, the crucial question: do you have your data (at least) backed up? Please, say yes.

If not, try loading one of the live versions of Linux - Knoppix, even Ubuntu, etc. - where you are essentially running the computer from the CD - kind of, anyway.

Then, see if your hard drive is recognized (Knoppix is pretty good for this). If it is and you can retrieve your data files, do that (copy them to another, clean, hard drive).

Then do a completely fresh install of Ubuntu, copy back your data and never, ever attempt another upgrade the way you did. At least until Ubuntu solves its dist-upgrade problems.

If these things are impossible, there might be some utilities that can pull data from a corrupted drive - however, I've never used them (at least not in Linux) so am not familiar with them. Others here, I'm sure, are.

Best of luck.

--gm

P.S. It is also my experience that doing ANYTHING with a computer, especially something as serious as an upgrade, on a whim is a very bad idea. Picture in your head all the things that can go wrong and then ask yourself if it's really worth it.

---

### Post by ledlincoln on 2007-09-09
Thanks for your good advice about upgrading, which I will heed in the future.  My desktop upgrade went so well, that I had a bit too much trust in the process.

I believe that the partitions are not actually corrupted, and my data is still there; I just want to take the least painful path toward restoring the server.  I've had good luck with Knoppix, so I'll give that a try first.

---

