---
title: "Migrating from 11.04 to 12.04"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by FrankenCub on 2012-05-05
Before posting this I searched for an answer but surprisingly didn't get any hits from this forum. Found some that were kinda helpful but nothing that completely resolved my questions. I would like to go about it without formatting my home partition, as I have my HDD split up as root/home/swap, but isn't there a lot of files in home that are used by the root partition ? I wouldn't want them to effect the new install, or would upgrading be best way about it ? I kinda question that because a fresh install has always been recommended from what I read here.

---

### Post by dino99 on 2012-05-05
your partitionning is good : a separate /home partition let you format the / (root) partition & re-use both /swap & /home, without formatting them of course, to do a fresh install on /.

Anyway you cant directly upgrade from Natty to Precise : only LTS -> LTS & previous -> next are possible, which is not your case.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by FrankenCub on 2012-05-05
> **dino99 said:**
> your partitionning is good : a separate /home partition let you format the / (root) partition & re-use both /swap & /home, without formatting them of course, to do a fresh install on /.

Anyway you cant directly upgrade from Natty to Precise : only LTS -> LTS & previous -> next are possible, which is not your case.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Thanks dino, I wasn't sure about the upgrade idea. So just fresh install on root, good enough. Should I expect any issues with other files in home, like compiz, .grub, eclipse, etc being compatible with 12.04 ?
Another file I have a question about, seems I'm questioning lol, .kde, I at one time had Kubuntu installed side by side with Ubuntu and have since dumped Kubuntu. Can I also dump that file ? Inside it are files autostart, cashe-username, env, share, tmp-username, and document socket-username.

---

### Post by FrankenCub on 2012-05-06
Got it installed but wasn't even thinking and formatted the / partition, now home doesn't point to where I wanted it to, points to a new home. My old home now shows up as 961 GB filesystem. Is there an easy way I can correct that ?

Troubles with setting up dual monitors too, one screen is white, looks like a common problem.

---

### Post by FrankenCub on 2012-05-06
[LEFT]Ever since installing 12.04 I've been goin Google mad lol. When the system goes lookin for my home partition, instead of going to the one that 12.04 installed I would like it to go to the one that I used before (11.04). I have found what looks to be a simple process... [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Basically inserting the UUID in the fstab file to identify the path. Would I actually need to copy the new home over to the old partition ? Anyone ?
[/LEFT]

---

### Post by grahammechanical on 2012-05-06
Did you do a fresh install of 12.04? If so, then install it again and this time you must tell the new install that you have a /home partition.

After selecting the / partition and marking it with a mount point of / you next must select the partition that is the old /home partition and click Change and give it a mount point of /home but do not mark it to be formatted. Repeat - DO NOT FORMAT THE /HOME PARTITION.

Now the install will see the old home partition and you will notice that any applications that you reinstall will pick up their old configurations because applications put their configuration folders in the user's home folder on the /home partition.

They are hidden files but we can see them when we set Nautilus to Show Hidden Files in the View menu.

Applications that you no longer use can have their dot ( . ) folders deleted.

Regards.

---

### Post by FrankenCub on 2012-05-06
> **grahammechanical said:**
> Did you do a fresh install of 12.04? If so, then install it again and this time you must tell the new install that you have a /home partition.

After selecting the / partition and marking it with a mount point of / you next must select the partition that is the old /home partition and click Change and give it a mount point of /home but do not mark it to be formatted. Repeat - DO NOT FORMAT THE /HOME PARTITION.

Now the install will see the old home partition and you will notice that any applications that you reinstall will pick up their old configurations because applications put their configuration folders in the user's home folder on the /home partition.

They are hidden files but we can see them when we set Nautilus to Show Hidden Files in the View menu.

Applications that you no longer use can have their dot ( . ) folders deleted.

Regards.

Thanks graham, yes I did a fresh install but forgot to show it my previous home. Will do another fresh install tonight, thanks #-o


That's better :)
Except the dash shows nothing, well it does show my music but there's no applications showing and search shows no results, unless it's music :S
I'm gonna stay away from the Nvidia drivers for now also so I can still use both monitors, tried to set them up again with the Nvidia drivers and the issue with one white screen is still there.

Ok edit again, dash fixed, now just to find a fix for Nvidia

---

### Post by drcrim on 2012-05-14
Thanks Graham, great advice to avoid losing files in /home and still get the benefits of the upgrade.  I found it best to remove all hidden dirs and files in $HOME and let the apps rebuild as needed.  I had many hidden dirs/files that I didn't need anyway.  Now I have a "clean" install of 12.04 with all my old files and it didn't take very long either.

---

### Post by nikonian on 2012-07-10
The main problem with people upgrading is THEY DO NOT READ INSTRUCTIONS, and rush through it. What's the rush, folks? Slow down, read, re-read and re-read AGAIN... then, carefully, triple-checking EVERYTHING, do it step by step, as you'll only come crying to us if it all goes wrong.

Remember, pride comes before a fall - noone is infallible.

---

