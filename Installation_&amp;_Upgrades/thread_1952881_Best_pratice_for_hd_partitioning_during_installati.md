---
title: "Best pratice for hd partitioning during installation"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by LtPitt on 2012-04-05
Hi everybody!

I want to achieve the best possible result in terms of reinstallation and portability of my Ubuntu install.

I've read here and there that if you keep your /home on a separate partition when you have to reformat or change system things are easier...

Do you have any better suggestions / tricks?

Thanks a lot :)

---

### Post by kc1di on 2012-04-05
> **LtPitt said:**
> Hi everybody!

I want to achieve the best possible result in terms of reinstallation and portability of my Ubuntu install.

I've read here and there that if you keep your /home on a separate partition when you have to reformat or change system things are easier...

Do you have any better suggestions / tricks?

Thanks a lot :)
I always use a seperate /home Partition that way you don't have to loose important data if you must re-install. 
Also use ubuntu one to store files I don't want to loose across platforms or installations.

---

### Post by darkod on 2012-04-05
From my experience I would say separate /home is all you need. So that would be three partitions in total, /, /home and swap.

When installing a server there are other options to consider for more different separate partitions, but with a desktop system the above is basically enough.

It makes a clean install easier in that you can always format / and reinstall but you still have your /home intact. Just make sure you NEVER format it, you ALWAYS specify that you have the separate /home partition during the clean install, and ALWAYS use the same filesystem that you originally had on /home. Also, ALWAYS use the same primary username in the new install as in the old one so that the /home/username folder will match.

Changing a filesystem will automatically tick the format box, and if you notice this you can click Back or Cancel and think what you did wrong. But if you don't notice it you end up with formatted /home. I have seen it here on the forum.

---

### Post by LtPitt on 2012-04-05
What about the configurations?

I know that some software allow you to use an hidden folder in your home for configuration but what about the others?

I'm forced to make an /etc backup too, right?

This could be a solution: [http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

But maybe it could be also a way to take old mess into a new installation, right?

---

