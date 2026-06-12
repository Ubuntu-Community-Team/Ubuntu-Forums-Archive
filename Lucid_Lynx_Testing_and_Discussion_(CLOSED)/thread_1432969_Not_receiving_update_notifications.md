---
title: "Not receiving update notifications"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benblout on 2010-03-18
I installed Alpha 1, and have been upgrading almost daily through Synaptic.  I have never received any notifications that an upgrade was available.  Using ps, I can see that update-notifier is running.

Is this a bug?  Which package should I report it against?

---

### Post by Merk42 on 2010-03-18
Do you mean you never received an upgrade saying "Alpha 2 is available" etc?
If so, you're not supposed to.  Alpha 2, 3, beta 1, etc are just snapshots of where packages are at the time.

---

### Post by benblout on 2010-03-18
I have not received any pop-up notifications that updates are available.  No icon appears in the notification area.  

When I go to synaptic, there are packages to update.

I am not talking about 'Alpha 2 is available', etc - sorry I was not clearer in my original post.

---

### Post by tito_torrisi on 2010-03-18
The same happens to me, and I also never saw this "a package manager is running" icon, which I know from Xubuntu... btw in xubuntu when I do "sudo apt-get update" in terminal, I get the "updates are available" icon...

---

### Post by Merk42 on 2010-03-18
> **benblout said:**
> I have not received any pop-up notifications that updates are available.  No icon appears in the notification area.  

When I go to synaptic, there are packages to update.

I am not talking about 'Alpha 2 is available', etc - sorry I was not clearer in my original post.

The icon no longer appears in the notification area as of Karmic (it may have been earlier).

Instead after some time (not sure how long) the entire update manager window pops up telling you of updates.

---

### Post by benblout on 2010-03-18
> **Merk42 said:**
> Instead after some time (not sure how long) the entire update manager window pops up telling you of updates.
I have gone as long as three days without installing updates.  Should I have been seeing the update manager window pop up?  I'm trying to understand expected behavior, so to know if I am seeing a bug.

---

### Post by mcduck on 2010-03-18
> **benblout said:**
> I have gone as long as three days without installing updates.  Should I have been seeing the update manager window pop up?  I'm trying to understand expected behavior, so to know if I am seeing a bug.

No, if it's just three days from your updates then you shouldn't have seen any updates yet.

The default behavior is that for any other than security updates the Update manager will only pop up once per every seven days. (and the notification icon shouldn't appear at all).

You should also note that if you check the updates manually that will reset the counter, so it's always minimum of seven days from the last time the updates were checked, by your or automatically.

(If you want, the old behavior of seeing an icon in Notification Area immediately wen updates are available can be enabled through gconf-editor)

---

### Post by benblout on 2010-03-18
mcduck: Thank you for the extremely complete answer.  You make it clear I am seeing the expected behavior.

---

