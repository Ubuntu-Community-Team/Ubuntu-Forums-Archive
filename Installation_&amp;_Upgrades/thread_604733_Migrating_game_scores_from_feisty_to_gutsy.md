---
title: "Migrating game scores from feisty to gutsy"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Jaiber on 2007-11-06
hello

I installed Feisty on my wife's computer with WinXP as dual boot. She likes to login to Ubuntu for those little games she's so fond of. She has pretty good scores in most of them.

I didn't want to disturb the environment so I installed Gutsy on a different partition - thinking if it worked out very well, I'll ask her to switch over. The installer offered to migrate the settings from Feisty, but her game scores are not migrated.

Wasn't the migration assistant designed to transfer those scores? I want to transfer it, so if there is a command line to achieve that, please let me know.

-J
(This is my first post here, btw)

---

### Post by ag65151 on 2007-11-06
Game scores are usually kept in your /home/[username] directory in hidden directories with the same name as the game. Do you have a separate /home partition that is being used by both Feisty and Gutsy? If not, you have a "fresh" game on the new partition that has /home on the same file system as / . 

It sounds complicated, but post if you have a separate /home partition.

---

### Post by Jaiber on 2007-11-07
As far as I know, Ubuntu doesn't create separate /home partitions. So, Feisty is in sda2 ( / on /dev/sda2) and Gutsy in sda3 (/ on /dev/sda3). Both of them dont have /home separate partitions.

---

### Post by PriceChild on 2007-11-07
In nautilus, press ctrl+h to show all the hidden files and folders in your home.

The game scores and settings will probably be stored in a folder named ".name".

So for example... ufo alien invasion stores its stuff in .ufoai, enemy territory stores its in .etwolf

Just copy these folders into the /home/$user on the new partition.

---

### Post by ag65151 on 2007-11-07
You're right, the default install does not create separate /home partitions. If you did have a separate /home partition, both versions could get to it. The above advice is good, just copy the hidden directory from your fiesty home to your gutsy home and you should have all of the history.

---

### Post by Jaiber on 2007-11-07
I'm thinking it is perhaps a good idea to migrate these settings too in the next version of Ubuntu.. Thanks for the info.

---

