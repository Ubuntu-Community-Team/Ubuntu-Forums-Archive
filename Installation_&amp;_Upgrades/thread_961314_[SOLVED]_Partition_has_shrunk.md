---
title: "[SOLVED] Partition has shrunk"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by fewjr on 2008-10-28
I have a small problem. I don't see what I'm doing wrong. I use gparted to make a 50GB partition on a 500GB drive for WinXP. I install it, then follow Herman's ([http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)) howto for installing Ubuntu. Except for I already have made the ntfs partition fpr WinXP. It installs fine like you show, except for some reason when I run gparted to look at my partition setup (I want to add openSUSE, etc.), my WinXP partition is only 5 or 6 GB in size instead of 50GB and Ubuntu has the rest of the drive. How is Ubuntu install shrinking ntfs partition like that without me telling it to. I know it is something I'm doing wrong. This is the 2nd time I've installed this way, and had these results.  What do you think?

Buddy/fewjr

---

### Post by Pumalite on 2008-10-28
Get Gparted Live CD and shrink XP to your hearts desire.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by bapoumba on 2008-10-28
> **fewjr said:**
> I have a small problem. I don't see what I'm doing wrong. I use gparted to make a 50GB partition on a 500GB drive for WinXP. I install it, then follow Herman's ([http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)) howto for installing Ubuntu. Except for I already have made the ntfs partition fpr WinXP. It installs fine like you show, except for some reason when I run gparted to look at my partition setup (I want to add openSUSE, etc.), my WinXP partition is only 5 or 6 GB in size instead of 50GB and Ubuntu has the rest of the drive. How is Ubuntu install shrinking ntfs partition like that without me telling it to. I know it is something I'm doing wrong. This is the 2nd time I've installed this way, and had these results.  What do you think?

Buddy/fewjr

If you used the guided partition, by default the Ubuntu partition will be big and the XP one small (on the one I've done, I recall 5-6 GB, that might be it). At this point, use manual partitioning, and use the partitions you have prepared the way you want.

---

### Post by fewjr on 2008-10-29
Pumalite said: > Get Gparted Live CD and shrink XP to your hearts desire.

As I stated, I used gparted to make the 50GB partition for WinXP. 
 bapoumba said: > If you used the guided partition, by default the Ubuntu partition will be big and the XP one small (on the one I've done, I recall 5-6 GB, that might be it). 
Thats exactly what happened. The problem is when I use gparted again to make WinXP partition larger, it won't let me. I mean, if I shrink the extended partition on the front end, it won't let me expand the 1st Primary partition back where it was. What I want is WinXP on the first Primary partition (50GB). Ubuntu is flexing its dominance!:wink:

---

### Post by Pumalite on 2008-10-29
I said Gparted Live CD.
Post screenshot of drives/partitions with Gparted Live CD

---

### Post by fewjr on 2008-10-29
I apologize....I meant that. I did use the gparted-live cd.

---

### Post by Pumalite on 2008-10-29
What about the screenshot?

---

### Post by fewjr on 2008-10-30
pumalite,
     I apologize once more. Things have been hectic at home, and I'm working. I went on [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) and read some documentation. I think I see what I was doing wrong. I will give it another go and post results when I get time to do it. You folks are great at helping us novices. Its greatly appreciated, but I know you like when we do our best to figure out things on our own. Its a learning experience. I'll post a screenshot if it doesn't go well.

Thank You
fewjr

---

### Post by Herman on 2008-10-30
:) Hello fewjr,
See step 4 of 7, (or illustration 13) in that link?

I'm guessing the Ubuntu is detecting the amount of files you have in Windows and is offering to shrink Windows as small as it can be.

Are you remembering to use your mouse to grab the slider between the old partition and the new partition and drag it to the right until you have the partitions proportioned the way you like?
(I  might need to fix the explanation under that illustration to try to emphasize that more).

Regards, Herman :)

---

### Post by fewjr on 2008-10-31
Thats exactly where I messed up Herman. I'm sorry, I guess I jumped the gun on this thread. I should have payed better attention and figured it out first. It still helps when you all add your thoughts. It makes me see things more clearly. Your explanation on your site is fine I think since I re-read it. I used gparted livecd to fix my mistake. Now I have WinXp & Ubuntu where I want them. I also made my SWAP 1GB, instead of the 10 Ubuntu made, and put it in the middle of the disk. I also added a 100MB GRUB partition & two 50GB partitions for Mepis & openSUSE. Thanks guys.

---

### Post by Herman on 2008-10-31
:cool: Cool!

...all the same though, next time I edit that web page I'll change it a little bit to point out the fact that that thing's a slider and make sure people notice that they can use it if they want to.
Thanks for letting me know, if you found it easy to miss then maybe other people will too, so I'll fix it, (at least as far as my website is concerned anyway).

Regards, Herman :)

---

### Post by fewjr on 2008-10-31
Cool back atcha:). I just downloaded Intrepid Ibex. I'll put it on its own partition and see if it cures any of the hardware issues I had with Hardy, (nVidia 8200 chipset & Atheros stuff). Check this thread, maybe you have some ideas:[http://ubuntuforums.org/showthread.php?t=959344](http://ubuntuforums.org/showthread.php?t=959344).

Thanks
Buddy/fewjr

---

