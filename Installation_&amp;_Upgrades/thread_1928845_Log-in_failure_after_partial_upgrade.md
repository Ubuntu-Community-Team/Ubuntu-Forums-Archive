---
title: "Log-in failure after partial upgrade"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2012-02-20
Using Ubuntu 11.10 with Unity 2D

Yesterday, I downloaded a different icon set. I didn't install them.

Later in the day, the update system reported that software was available. I selected it, but was offered a partial upgrade of some 200+ files.

Ever-wary of partial upgrades, I declined it and de-selected the software update. Nevertheless, it downloaded furiously for a while. I assumed that it was simply because my system is set to routinely download recommended software automatically without installing them.

Today, when I started up, it got to the log-in screen, which appeared a little different to normal and wouldn't accept my password. It continued to revert to the log-in screen. I am very confident that I haven't messed up my password.

I'm now using my second machine to access this forum.

Any suggestions on what to do?

Thanks

---

### Post by youngunix on 2012-02-20
did you try the "recovery mode"?

---

### Post by Buster95 on 2012-02-21
> **youngunix said:**
> did you try the "recovery mode"?

Yes - tried selecting recovery mode at Grub. Same result.

Tried earlier kernels. Same result.

Tried all the options available at the log-in. Same result except for "recovery console".
It opens a small terminal window (about 10% of the total available window area). It can't be re-sized but seems to function as a normal terminal.

Do you know how to launch 11.10 via the terminal?

I've already tried "ubuntu-desktop", "ubuntu-desktop start" both as user and root.

Oh- I also checked whether I had a hardware issue, by running MS Windows (dual boot in Grub).

I guess that I could download a fresh iso on my other machine and load it up, but am not sure how to manage the partitions.

I don't want another Linux partition and don't want to screw up the current MS partition. So I'm delaying that in the hope of inspiration.

Any guidance would be gratifying.

---

### Post by Buster95 on 2012-02-21
Success!
Using the tiny terminal screen that I was able to open, I did a "dist-upgrade" which took more than an hour.

I exited the terminal and it restarted henormally. The only thing that remains different (so far) is the log-in screen, which looks a bit different. However, it works!

I guess that, although I declined to progress with the partial upgrade, something I did there must have broken something important. The upgrade fixed it.

---

### Post by youngunix on 2012-02-21
> **Buster95 said:**
> Success!
Using the tiny terminal screen that I was able to open, I did a "dist-upgrade" which took more than an hour.

I exited the terminal and it restarted henormally. The only thing that remains different (so far) is the log-in screen, which looks a bit different. However, it works!

I guess that, although I declined to progress with the partial upgrade, something I did there must have broken something important. The upgrade fixed it.

I'm glad you got it to work, and keep in mind that disturbing updates/upgrades is really a bad idea.
Next time you want to upgrade but don't want to wait awhile for it, leave it overnight. 
good luck.

---

### Post by Shadius on 2012-03-12
I've got this problem and nothing seems to be working. After a partial upgrade, I can no longer login. I've had to do "adduser recovery" to create a new user so I can log into my system, but I still cannot log into my other user account. :(

---

