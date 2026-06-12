---
title: "Ubuntu 16.04 &quot;Reboot and select proper boot device&quot; after cloning drive"
date: 2016-07-23
forum: Installation &amp; Upgrades
---

### Post by hc-koch on 2016-07-23
Hello,

I am using Clonezille to clone entire disks to other local disks because I have computers with identical hardware configuration. This used to work fine, I install Ubuntu on one of them, configure it and then clone it to all other disks with Clonezilla.

Unfortunately since 16.04 they won't start. It's stating "Reboot and select proper boot device or insert Media..". It doesn't matter whether I choose UEFI or legacy. Even more annoying is that a new installation from a Ubuntu 16.04 disk with option "Delete everything and install Ubuntu 16.04.1" (it recognizes the other installation!) doesn't fix the issue. Same error. If I install it without trying to clone before it works fine.

I tried to fix it with fdisk from livecd and I tried boot-repair disk with several options. Here's the log from the latest try, choosing recommended repair: [http://paste.ubuntu.com/20645235/](http://paste.ubuntu.com/20645235/)

---

### Post by hc-koch on 2016-07-24
I fixed it. I downloaded the UEFI/amd64 version of clonezilla and recloned it.
Seems like Ubuntu 16.04 is making something different in installation (UEFI installation default despite activated legacy mode?).

Btw I find the Ubuntu support in this forum (this is the official one isnt it) pretty disappointing. None of my three question was even answered once. I know it's a free OS but if you want to measure with Windows... Well, however, solved.

---

### Post by grahammechanical on 2016-07-24
What do you mean by "official?"

Do you mean in the sense that some of us are paid to give advice? This is a user forum. We are all users. We voluntarily try to help out to give something back for the free gift of Ubuntu.

The big question now is: Will you give something back based on this experience of yours?

---

### Post by hc-koch on 2016-07-24
By official I mean that this is the place Canonical refers to if you want support for personal use of Ubuntu.
I don't want to get on the wrong side of someone. I think providing a solution to this problem and marking it as solved instead of just leaving set already a good example.
Of course actively participating would be another step but I don't see why I should - based on this experience of mine.

---

### Post by wildmanne39 on 2016-07-24
> I think providing a solution to this problem and marking it as solved instead of just leaving set already a good example.
I want to thank you for posting the answer and marking it solved.

Also want to point out that your thread was not posted that long ago and we are all from different time zones and the person that may have known the answer to your issue probably has not been on yet.

Also while this is a big forum there is only a few people that actually answer questions probably around fifty on a regular basis so please do not judge the forum on the short time your post has been on it.
Thanks again and at anytime you are welcome to become part of the solution for helping more people.

---

