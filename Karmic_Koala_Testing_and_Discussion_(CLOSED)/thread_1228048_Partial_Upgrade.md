---
title: "Partial Upgrade"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-07-31
I installed Alpha 3 and everytime I run the update manager I keep getting a message saying that it is a partial upgrade.  Any idea how long it will be before I'm not a partial upgrade anymore?

---

### Post by buzzmandt on 2009-07-31
have you run sudo apt-get dist-upgrade?

---

### Post by keenish27 on 2009-07-31
> **buzzmandt said:**
> have you run sudo apt-get dist-upgrade?

Nope.  All I did was install Alpha 3 and then ran the update manager.

---

### Post by buzzmandt on 2009-07-31
in terminal do > sudo apt-get update
then do 
> sudo apt-get dist-upgrade

should take care of it for you

---

### Post by ikt on 2009-07-31
> **buzzmandt said:**
> should take care of it for you

I don't think doing partial upgrades via the update manager are a problem, ie he wants to know why he's getting the message not how to avoid the message, as far as I am aware running the update manager is the correct way to update in alphas of ubuntu.

I'm not actually 100% sure what a partial upgrade is.

---

### Post by taavikko on 2009-07-31
> **ikt said:**
> as far as I am aware running the update manager is the correct way to update in alphas of ubuntu.

I'm not actually 100% sure what a partial upgrade is.

Using update-manager in devel-releases isn't a must.
User uses what he/she's accustomed to.

Partial upgrade happens when dependencies aren't sorted and this results in packages in inconsistent state (package removals and such)

---

### Post by buzzmandt on 2009-07-31
> **keenish27 said:**
> I installed Alpha 3 and everytime I run the update manager I keep getting a message saying that it is a partial upgrade.  Any idea how long it will be before I'm not a partial upgrade anymore?

My understanding was how long before I'm not a partial upgrade anymore?

answer:  as soon as you run dist-upgrade

Apologies if I was mistaken.

---

### Post by Jay_Bee on 2009-07-31
I had the same thing and I ran a partial upgrade and everything is fine, so I guess it's pretty safe.

---

### Post by keenish27 on 2009-07-31
> **buzzmandt said:**
> My understanding was how long before I'm not a partial upgrade anymore?

answer:  as soon as you run dist-upgrade

Apologies if I was mistaken.

Its no problem.  I am just hesitant to do partial upgrades because the last time I did it destroyed my system.  I went ahead and did it this time and everything is fine so I'm happy.  I love testing the new releases, its just gets annoying when you need to reinstall the OS every couple of days.

Thanks for all of the help.

---

### Post by psyke83 on 2009-07-31
The problem is because the "devicekit" package is now marked as a conflict on devicekit-power. See: [https://lists.ubuntu.com/archives/karmic-changes/2009-July/005206.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/005206.html)

Folks, always check the changelogs on the affected packages before allowing a Partial Upgrade. This time it was safe to allow, but there are many cases in which a Partial Upgrade will cause an inconsistent, or even unbootable system.

buzzmandt,

The Partial Upgrade in update-manager is the equivalent of running "apt-get dist-upgrade" when packages are to be removed - so the same advice applies.

---

### Post by purecharger on 2009-08-22
> **psyke83 said:**
> 
Folks, always check the changelogs on the affected packages before allowing a Partial Upgrade. This time it was safe to allow, but there are many cases in which a Partial Upgrade will cause an inconsistent, or even unbootable system.

If that is the case, what is the recommended course of action? Is there a way to upgrade packages without hosing my system?

I just did one of these partial upgrades, and the nvidia driver got removed, leaving me to manually install from nvidia.com.

---

### Post by ezsit on 2009-08-22
> If that is the case, what is the recommended course of action? Is there a way to upgrade packages without hosing my system?

I would simply not do the update and check back later that day or the next day to see if the repos and dependencies are straightened out. What, y'all have no patience?

---

### Post by jblackhall on 2009-08-23
> **purecharger said:**
> If that is the case, what is the recommended course of action? Is there a way to upgrade packages without hosing my system?

I just did one of these partial upgrades, and the nvidia driver got removed, leaving me to manually install from nvidia.com.

If you click "Close" instead of "Partial Upgrade" when the box comes up, you'll be fine doing "Install Updates" in Update Manager, which should only check packages that are able to be upgraded, i.e. nothing will be removed.  Once you do that, you may want to run Synaptic to see which packages would potentially be removed and then come to this forum to see whether they're supposed to be removed or whether they're being incorrectly removed (like they're in the process of being built)

---

