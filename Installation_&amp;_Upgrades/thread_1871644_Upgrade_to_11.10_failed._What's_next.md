---
title: "Upgrade to 11.10 failed. What's next?"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by pieroxy on 2011-10-29
I started an upgrade. All went well up to the point where it is installing libc-bin. Here it is stuck and nothing moves again. 

Here are the last lines of the terminal:

```
Unpacking replacement lib32gcc1 ...
Preparing to replace g++-4.5 4.5.2-8ubuntu4 (using .../g++-4.5_4.5.3-9ubuntu1_amd64.deb) ...
Unpacking replacement g++-4.5 ...
Preparing to replace libstdc++6-4.5-dev 4.5.2-8ubuntu4 (using .../libstdc++6-4.5-dev_4.5.3-9ubuntu1_amd64.deb) ...
Unpacking replacement libstdc++6-4.5-dev ...
Selecting previously deselected package libgcc1:i386.
Unpacking libgcc1:i386 (from .../libgcc1_1%3a4.6.1-9ubuntu3_i386.deb) ...
Preparing to replace libc-bin 2.13-0ubuntu13 (using .../libc-bin_2.13-20ubuntu5_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.13-20ubuntu5) ...
(Reading database ... 214965 files and directories currently installed.)
Preparing to replace libc6 2.13-0ubuntu13 (using .../libc6_2.13-20ubuntu5_amd64.deb) ...


```


So now I have the "Distribution Upgrade" window in the middle of my desktop and nothing happens anymore. I don't dare rebooting since only 10% of the packages have been upgraded...

What should I do?

---

### Post by Bao2 on 2011-10-29
I never upgrade.
I always download a CD image. Then make a USB with the CD Image (because installing from the USB takes only around 10 minutes).
Then I have several hard disks and always I have the old Ubuntu in one disk and the new Ubuntu I install in a different disk (you must indicate you want that disk for the / partition but also many people miss that in that window, below you must indicate the disk where you "boot" goes (the grub). If you don't indicate the same disk probably the grub will go to other disc you don't want.

Then when starting the computer I press F11 and a menu appears and I select the disk I want boot the computer on (if your computer doesn't have such a key you must to enter the BIOS and then select the hard disk to boot the computer).

That way I have the OSes completely each one in their own hard disks without they messing around.

---

### Post by pieroxy on 2011-10-29
I know, I usually don't upgrade either. Well. Looks like I'm up for a fresh install. f*$#@ing upgrade manager!!!

---

### Post by raja.genupula on 2011-10-29
> **pieroxy said:**
> I know, I usually don't upgrade either. Well. Looks like I'm up for a fresh install. f*$#@ing upgrade manager!!!

Hi man 

  why don't you go for cd upgrade , its safer and you not gonna lost your data.Man my suggestion take back up your imp data before fresh install. 

All the best.

---

### Post by pieroxy on 2011-10-29
ok, I re-installed a fresh Ubuntu on another partition. Things are fine. My advice for anyone having Ubuntu and wanting the latest one: FRESH REINSTALL.

I think it's about the third time in my Ubuntu experience (6 years) I tried an upgrade instead of a fresh install. It has **never** succeeded. Never.

I don't know what's wrong with Ubuntu, but I'd be them I'd stop pushing upgrades at people.

---

