---
title: "sshd not listening on port 22 after upgrade to 18.04"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by bkline on 2018-05-16
After upgrading to 18.04, I can no longer ssh into the system without first going to the console and waking it up. Never did this before.

---

### Post by dino99 on 2018-05-16
check the 'power' settings system

---

### Post by bkline on 2018-05-19
Thanks, I had made sure that while the screen was allowed to blank out after an interval, automatic suspend was disabled.

---

### Post by bkline on 2018-05-19
BTW: apologies for the delay in replying to your suggestion. I had subscribed to the thread, but never got an alert for your posted message (and yes, I checked the spam folder). :-(

---

### Post by bkline on 2018-05-19
A possibly related symptom (also new with the 18.04 upgrade) is that after a reboot I am unable to ssh into the machine without first walking up to the console and logging in locally. Makes it awkward to reboot remotely, which means application of urgent security patches gets delayed, which can't be an intentional improvement for the upgrade. :-(

---

### Post by bkline on 2018-05-26
Bump. Is no one else experiencing these problems with 18.04?

---

### Post by kerry_s on 2018-05-27
well you know with each release they up the security features. so each release has a different way of setting things up.
so maybe you aern't setup the right way?
found this-> [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804)

---

### Post by bkline on 2018-06-14
Thanks for the link (and apologies for the late reply -- for some reason thread subscription/notification isn't working).

Unfortunately, this isn't an authentication issue (I ran into and solved that problem with earlier upgrades). The ssh daemon isn't even listening on port 22 until I log in at the console. This is definitely a new problem introduced by the 18.04 upgrade.

Does **anyone** know what's going on? And how to fix it?

---

### Post by bkline on 2018-06-14
Another data point is that the machine responds to ping requests even when sshd is not listening on port 22. So we know the machine isn't asleep (so I'm changing the title of this thread).

---

### Post by bkline on 2018-06-20
I tried reporting this problem in the *Installation and Upgrades* forum, which I had assumed was the most appropriate one, but no one there seemed to know what was going on. Ever since I updated to the latest distro release (18.04) I am sometimes unable to ssh into the machine until I walk over to the console and wake up the machine by hitting a key on the keyboard or moving the mouse. The machine is not asleep or hibernating, because I get a response back from ping when it's in this state. Obviously this is an undesirable state of affairs, as it makes me very reluctant to install updates which require reboots, even if they involve security patches, if I'm not physically located where the Ubuntu box is. What could be going on?

---

### Post by bkline on 2018-06-20
Bump.

---

### Post by QIII on 2018-06-20
Threads merged.

Please don't duplicate threads.  It dilutes the community's effort to help.  The Installation and Upgrades forum is every bit as visible to everyone as General Help, and is probably more appropriate for an issue that has arisen after an upgrade.

I changed the title of this original thread to the newer one, as it is more descriptive.

Thanks.

---

### Post by bkline on 2018-06-20
Thanks, I tried to change the title of the thread myself, but I was only able to change to for subsequent messages, not for the original thread. I appreciate the desire to avoid redundant threads, but I don't think you can fault me for lack of patience after waiting for over a month for someone who knows what's going on to respond. It's hard to believe I'm the only user who has hit this behavior, and the only explanation I could think of was that this forum didn't get as much visibility as the general forum. I'll keep waiting. ;)

---

### Post by QIII on 2018-06-20
It is quite permissible to bump your thread if you haven't redeived a response in about 12 hours.  That'll keep you up toward the top.

---

### Post by bkline on 2018-06-20
OK, I'll keep trying. :-) It has occurred to me since posting my original message in this thread, however, that most people who gravitate toward helping people in this particular forum are probably expecting to be dealing with difficulties in the upgrade process itself, rather than with random problems introduced in specific packages.

---

### Post by bkline on 2018-06-23
Well, I gave up and rebuilt the box, and the problem is gone. Not the first time an Ubuntu upgrade has borked a machine.

---

