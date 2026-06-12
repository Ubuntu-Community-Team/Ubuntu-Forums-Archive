---
title: "Is something getting buggy with Software Updater?"
date: 2023-08-05
forum: Installation &amp; Upgrades
---

### Post by jadaube2 on 2023-08-05
Software Updater is acting strange on two computers this morning. On one, it wanted to do a partial upgrade (which is almost always a mistake), and on the other computer, it just says that about a gig worth of updates are available but doesn't show those updates.  I also saw a post this morning [https://ubuntuforums.org/showthread.php?t=2489595](https://ubuntuforums.org/showthread.php?t=2489595) from several other people who got the partial upgrade message, did the upgrade, and lost GDM.

Is something going on with the repositories? I'm inclined to hold off upgrading anything for the next few days to see if it's fixed.

---

### Post by ajgreeny on 2023-08-05
Yes, you are one of many who have seen this problem, including me in my Xubuntu 22.04, when I tried upgrading using ```
sudo apt update
sudo apt full-upgrade
``` so it's not only Ubuntu with gdm3 that suffers but other DE versions as well.

Mine worked fine this morning using the **full-upgrade** command (I never use a GUI for package management but just apt commands) and I assume whatever the problem was has now been overcome, so I hope by now you are also up and running as normal.
If you still have the problem just wait a bit longer as I'm fairly sure the phased updates system will eventually get all back to normal.

---

### Post by ian-weisser on 2023-08-05
Possible bug report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262)

---

### Post by jadaube2 on 2023-08-05
Well, I just ran Software Updater again at 03:38 GMT and the problem seems to have solved itself - no more partial upgrade messages.

---

### Post by makitso on 2023-08-08
I am still getting the Partial Update notice when running Software Updater.  I have cleaned the apt cache, etc but nothing works.  Normal apt update or update via Synaptic work correctly. Suggestions on how to clear the flag for Partial Update?

---

### Post by VMC on 2023-08-08
Please mark this topic Solved in thread tools if satisfied.

---

