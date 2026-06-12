---
title: "Installation problems  (bunch of errors)"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Realedazed on 2008-07-13
Hello!

I've been dying to get into Linux for a while and I after reformatting my gramma's computer (since she had a virus), I figured I'd test Ubuntu on her.  

Well, here's what I've done. Hopefully you can spot the problem.

Downloaded both versions of the installer. Live CD and the alternative. Also downloaded the Gnome Partitioner and KillDisk

With KillDisk, I wipe the entire drive. Then with the partitioner, I partition it  to approximately 5gb for Ubuntu /boot, 30gb for /home and 5 for swap, as per some instructions I found either here on the web.

I try to install the OS but I continue to get errors like a i/o error. So I erase the partitions and reformat. I try the alt installation and it works. I get the bash ($, right?) prompt, but I have no clue what do do with it. I'm a big newbie, so I NEED a GUI.

So I format and partition again with one big partition and one small for swapping. I try again with the LIVE CD and get the same errors. This time, problem reading partitions and stuff.

Sorry, I don't have the exact errors, since I lost the sheet of paper I wrote them on. But does someone have a clue what's going on?

---

### Post by Rocket2DMn on 2008-07-13
Don't be afraid of the alternate install cd, it's intuitive and easy to use.
You don't need a separate /boot partition, all you really need is swap (no mount point) and root (/).  Using /home is optional, too, but it is nice to have, so go for that one.
You should also check the md5sums on the .iso image files, then burn at a slow speed like 4x to prevent write errors.
HowTo md5sum - [uhelp]community/HowToMD5SUM[/uhelp]
Hashes to check against - [uhelp]community/UbuntuHashes[/uhelp]

---

