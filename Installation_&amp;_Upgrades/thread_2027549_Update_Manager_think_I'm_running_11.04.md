---
title: "Update Manager think I'm running 11.04"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by vjd5023 on 2012-07-16
Earlier today I attempted to upgrade my current Ubuntu version (10.10) to 11.04 using update manager. I got an error in one of the early stages, and after searching forums I think I've got the error taken care of. The problem is that update manager thinks that I'm running 11.04 now so I'm being asked to upgrade to 11.10. I've thought about just trying to go straight from 10.10 to 11.10 but I'm not sure if that will get me into more trouble. I think this resulted because I killed the update manager process while it was at the point of the error. This led to all of my repositories being switched to natty even though I was running maverick. I restored my repositories to their original states (maverick default and I've removed all third party ppas which I believe was my original problem). Nonetheless, does anything have any idea of how to alert update manager to the fact I'm still running 10.10? Or should I just attempt to upgrade straight to 11.10? Thanks in advance for any responses!

---

### Post by Laiquendi on 2012-07-16
Updating from 10.10 may not be the best idea, why not to install 12.04?
Point is - too many dist-upgrades also cause errors and misconfigurations, so clean install may be the answer.
Just simply backup your data, installed application list, settings, and install 12.04.

If you still prefer to leave the 10.10 on your computer and update step by step, I'm sorry but i don't know where the switch is, if it wasn't in the repositories.

---

### Post by darkod on 2012-07-16
I am not sure if changing the repositories back will affect it, or at which point the upgrade stopped (during download of the new packages or once the upgrading of packages was started), but you can try finishing an interrupted upgrade with:
```
sudo dpkg --configure -a
sudo apt-get install -f
```As I said, not sure if you need the old or new repositories for that to work.

I agree with the previous reply about upgrading 10.10 to 11.04, it might not be worth it. Even if it finishes without a glitch, you still have "only" 11.04 that is running out of support in October.

New upgrades in a row will very probably mess up at least something.

At this point, after you held on 10.10 that long, maybe backing up the data and doing a clean install of 12.04 LTS is the best way forward.

---

### Post by sammiev on 2012-07-16
I would try 12.04 first on a USB/CD to make sure you can run it first before you install it. Depends on your computer hardware and how old it is.

---

### Post by vjd5023 on 2012-07-16
Thanks for the input, I didn't know upgrading could be so messy. It's sounding like a clean install may be the best way to go forward. I wanted to at least upgrade to 11.10, which would mean two consecutive update manager upgrades. Are there any backup programs you'd suggest that copy important files I may want? I already backed up my home folder, which contains all my personal files.

---

