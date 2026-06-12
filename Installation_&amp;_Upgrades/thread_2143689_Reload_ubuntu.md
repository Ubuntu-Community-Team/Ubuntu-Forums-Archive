---
title: "Reload ubuntu"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by DawgMan on 2013-05-09
I made a mistake.  I switched to Linux Mint in January and now I want to switch back.  I did one smart thing when I moved to mint.  I created 3 partitions on my 1 TB Hard drive.  I have a 50GB partition for / (/dev/sda1), and a 945GB partition for /home (/dev/sda6), and a 4.3GB partition for Swap (/dev/sda5). I did this with the hope it would make upgrades and or moving from one linux to another easier.

When I do the install what is going to be different?  Do I just pick /dev/sda1 to install onto with out formating?  Or can I only format /dev/sda1 and leave the others alone?

Side note:  the main reasons to switch back: printer admin is a nightmare and desktop freaks about once a day.  Main reason I switch to Mint, I really didn't like unity.  But I think I've found some customizations to make it worth the trip back.

Dan

---

### Post by 2F4U on 2013-05-10
You would format /dev/sda1 since this will become your root partition, but you don't need to format swap and /home (this would remove your data). Take care of existing config files from Mint, which usually reside in /home. These may interfere with your new installations. To prevent this, it might be a good idea to use /dev/sda6 as a data-only partition and have /home under the root partition. Configuration files would be saved in the new /home and the data kept in the seperate partition (this can be cleaned-up later).

---

### Post by DawgMan on 2013-05-10
Thanks I think I got it now.

how do I mark this [SOLVED]?

---

### Post by 2F4U on 2013-05-10
This should do the trick:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

