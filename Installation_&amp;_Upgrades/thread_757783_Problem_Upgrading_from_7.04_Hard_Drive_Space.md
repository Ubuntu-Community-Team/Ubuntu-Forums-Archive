---
title: "Problem Upgrading from 7.04: Hard Drive Space"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by apolloxi on 2008-04-17
I just recently deleted a 10GB folder from my Ubuntu hard drive on my laptop, giving me about 19GB of free space (whereas before, I barely had above 2GB free).

For some reason, whenever I go to upgrade to 7.10 from my Update Manager (keep in mind, I've downloaded every upgrade for 7.04, so there is nothing left to update in this system), it only gets to the second step of the installation before telling me I don't have enough disk space.

How the hell could I possibly not have enough disk space when the upgrade requires 1.3GB free, and I have almost TWENTY TIMES that amount free?

I tried doing the "sudo apt-get clean" command, too. Nothing that the pop-up window suggests has worked.

Can anyone help me with this?

!!! - EDIT - !!!

Found the real problem. Please read my post below.

---

### Post by apolloxi on 2008-04-17
Actually, I just looked this up a little more than I had before, and I saw that the pop-up specificially mentioned there was no free space in "/", not my general filesystem.

So, I used the Disk Usage Analyzer in accessories to see that I have NO space left on "/". It's 100% full, at 25GB.

Is there anything I can do to fix this?

---

### Post by st0nedpenguin on 2008-04-17
Did you delete the folder to a temp trash/recycle bin type arrangement?

If so the files may still be there and you'll need to empty the trash to reclaim the space.

---

