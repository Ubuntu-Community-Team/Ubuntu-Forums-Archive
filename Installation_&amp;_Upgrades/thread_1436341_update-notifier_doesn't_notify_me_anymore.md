---
title: "update-notifier doesn't notify me anymore"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2010-03-22
It never notifies me about any updates.

In my startup following line is present:

update-notifier --startup-delay=60

In my repository settings I have chacked that it should llok for updates daily.

What can be wrong?

---

### Post by quixote on 2010-03-23
I don't know why it does that, but I've had the same problem.  My workaround was just to hit the "check" button to manually update the list whenever I remembered.  Not ideal, but at least you'll get the updates.

---

### Post by strawberry on 2010-05-02
Let me join the company :(
The update notifier hasn't been working since I installed 10.04 RC.
I don't know what to check/correct in the system. 
I look for the security updates and the new version of packages manually.

---

### Post by SgtPepperKSU on 2010-05-02
Have you guys read the release notes (or the release notes of any release since 9.04)?

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/1004#Change%20in%20notifications%20of%20available%20updates)

---

### Post by strawberry on 2010-05-03
Thanks a lot for the info.
I haven't read the referred release notes at all. It's my fault. 
It was useful feature for me, so if I stay at ubuntu, I will apply the command the RN mentioned.
By the way, there were not any security update since 10.04 RC was issued? Other hand, the two guys before me haven't received any security updates at all?

---

### Post by quixote on 2010-05-04
SgtPepper: I think you're talking about something else.  I'm certainly not complaining about the lack of the orange alert button thingy.  Good riddance.  I like the new way of notifications about updates much better.  What I, and I think the OP?, are talking about is that there is no notifications about updates at all.  If I run Update-Manager, it says my system is up to date no matter how long it's been.  I have to manually hit the "check" button.

---

### Post by z06steve on 2010-05-04
I have the same behavior.  Installed on two computers, one Friday night, and the other yesterday and have not received any updates on either.

---

### Post by mihai.ile on 2010-05-06
Just use:

```
$ gconftool -s --type bool /apps/update-notifier/auto_launch false
```

to have the old behavior (with the updates icon in the tray), I am using it this way.

---

### Post by montysan on 2010-06-09
> **quixote said:**
> SgtPepper: I think you're talking about something else.  I'm certainly not complaining about the lack of the orange alert button thingy.  Good riddance.  I like the new way of notifications about updates much better.  What I, and I think the OP?, are talking about is that there is no notifications about updates at all.  If I run Update-Manager, it says my system is up to date no matter how long it's been.  I have to manually hit the "check" button.

I've had the same problem. [Here's my post]("http://ubuntuforums.org/showthread.php?t=1504892").

No solution yet, but there was some useful info about 'apt-get update', which if you run kick-starts the update manager. Maybe this isn't being called at start-up, or maybe update-notifier is supposed to do this but it isn't?

---

