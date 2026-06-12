---
title: "Update/Upgrade issue"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by chrisav on 2006-07-05
Hello,

I am surprised and a bit sad.
I had installed ubuntu on a pIII 900MHz pc some time ago for me to learn this distribution and for my mother, to get rid of wind... slowly.
Then a week or two ago I upgraded the system with the adequete cd.
Two days ago I updated and upgraded some specific softwares and the ones that the system said they had updates/upgrades, even I tried to do it for the whole system. 

Their were no apparent problems at all.
Until now when I launched Ubuntu. It like freezed at the beginning with command lines and error messages. 
The system seems to be broken, perhaps the "kernel" itself.
I don't know perhaps it's a problem of compatibility because of dependencies also.

I can also see that some lines show that the file system is Ext2fs, when it should be ext3fs.

I am starting to think that for newbies this system of updating/upgrading is too "dangerous"/risky because of dependencies or something else.
But it's true also that with other operating systems I almost don't update/upgrade at all.

I just don't know what to do now. I was starting to imagine migrating more and more each day.

Thanks for your help
Chris

---

### Post by confused57 on 2006-07-05
You're definitely not alone, I've seen numerous people have the same problem after dist-upgrade.  You might find something in the Stickys section listed above, on how to repair your upgrade...Good Luck.

---

### Post by Dr. Nick on 2006-07-05
When you get the grub screen at the begennig, try to pick a old version of the kernel to boot into. Dont use the top ubuntu choice, try the 3rd or so (not a recovery one) That will load you into your old kernel, see if it works.

I used to have a problem similar because I had run out of room on my hd for the new kernel to fully install, so it would crash on boot

---

