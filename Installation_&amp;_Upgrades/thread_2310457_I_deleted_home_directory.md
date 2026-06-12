---
title: "I deleted /home directory"
date: 2016-01-19
forum: Installation &amp; Upgrades
---

### Post by manemis on 2016-01-19
Hi I was about to make simbolic link my /home partition to /home under / partition. the problem is, I have tried this with gksu nautilus, but when I erased /home under /, the nautilus has turned off and I never can use nautilus(it sais I have no permission.)
I have backed up my original home directory, but now I cannot even login.
What shouls I do?

---

### Post by v3.xx on 2016-01-19
As you discovered, you can't do that.  You need to put things back like they were.  You have a live dvd?  With it you can use the live session to access the hdd.

---

### Post by manemis on 2016-01-19
When I install ubuntu, I obviously made home patition apart, but it seems not linked home directory in /. There was another home directory in /. But I made /partition with only 20gb, so I must use the home partition already I've made. Can I replace it?Can't I?

---

### Post by oldfred on 2016-01-19
If you already have /home then you can skip the initial copy commands. But this shows the entries required in fstab and other details:

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by manemis on 2016-01-19
Thank you for your advice. But I remember that I made backup with only copy and paste in nautilus not rsync, then it means it does not have ownership and permissions?

---

### Post by oldfred on 2016-01-19
Your ownership & permissions with /home can be reset. But system, not so much.
I think link shows that also.

       Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER

Note that -R is recursion. Never run on any system folders, or else you probably just have to reinstall and restore from backups.

---

### Post by manemis on 2016-01-20
Thank you! all is well now.

---

### Post by oldfred on 2016-01-20
You can change to Solved.

During install with a separate /home partition you have to use the Something Else install option, choose the /home partition, but be sure NOT to tick the format or else it erases it.

---

