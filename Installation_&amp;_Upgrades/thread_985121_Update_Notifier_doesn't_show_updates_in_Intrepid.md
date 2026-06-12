---
title: "Update Notifier doesn't show updates in Intrepid"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by hoomanb on 2008-11-17
It had been a while since I had upgrade to Intrepid and I realized there had been no update notifications. So I ran update manager, noticed the sources were like 11 days old (since last upgrade) and of course manually I installed lots of updates.
BTW, I upgraded to Intrepid from hardy.

---

### Post by Partyboi2 on 2008-11-17
In Software Sources have you got the updates boxes ticked under the update tab?

---

### Post by hoomanb on 2008-11-18
I do.

Never the less, after an upgrade to all updates, I checked intrepid-proposed and some updates showed up. I don't know if it was because of the update or because I checked proposed packages. 

I have now unchecked proposed and in a few days I'll see if updates show up in the notifier.

---

### Post by hoomanb on 2008-11-20
The icon is still now showing up.

I started update manager after a few days, the list of packages wasn't updated since the last time I manually performed an update (3 days ago).

Note that I have selected daily updates in update manager.

---

### Post by hoomanb on 2008-11-30
I think I figured out the problem:
There was an apt script in /etc/cron.daily which did not have execute permission.

---

