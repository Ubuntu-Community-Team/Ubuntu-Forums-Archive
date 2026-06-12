---
title: "Grub to Vista Bootloader"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Zacha on 2007-10-19
Please do not post things like "Why do you want to do that?" or "Vista Sucks!" in this thread please.

Well. To make it short.
Yesterday I installed Ubuntu.
I thought I told it NOT to install GRUB to MBR.
But when I restarted my computer I was met by GRUB to my surprise.
At first I thought "What the heck" but today I noticed that I can't hibernate in Vista anymore (probably because of the wrong MBR).

So I wonder how do I put GRUB on the ubuntu partition instead and still be able to restart and boot into Vista to fix the bootloader there afterwards? (As I have no Vista DVD, only recovery CD's...)

Or should I fix the bootloader first in Vista and then use a LiveCD to install grub to the ubuntu partition (and how do I do so it doesn't write to MBR again if so?)

---

### Post by angrykeyboarder on 2007-10-19
> **Zacha said:**
> Please do not post things like "Why do you want to do that?" or "Vista Sucks!" in this thread please.

Well. To make it short.
Yesterday I installed Ubuntu.
I thought I told it NOT to install GRUB to MBR.
But when I restarted my computer I was met by GRUB to my surprise.
At first I thought "What the heck" but today I noticed that I can't hibernate in Vista anymore (probably because of the wrong MBR).

So I wonder how do I put GRUB on the ubuntu partition instead and still be able to restart and boot into Vista to fix the bootloader there afterwards? (As I have no Vista DVD, only recovery CD's...)

Or should I fix the bootloader first in Vista and then use a LiveCD to install grub to the ubuntu partition (and how do I do so it doesn't write to MBR again if so?)

I've got GRUB in the MBR and I've never had any problem with Vista because of it.  It hibernates just fine. In fact, it only hibernates under Vista.  It won't in Ubuntu and it never did in XP.

I find it odd that this is causing a hibernation problem for you. Are you sure it couldn't be something else?

---

### Post by Zacha on 2007-10-19
> **angrykeyboarder said:**
> I've got GRUB in the MBR and I've never had any problem with Vista because of it.  It hibernates just fine. In fact, it only hibernates under Vista.  It won't in Ubuntu and it never did in XP.

I find it odd that this is causing a hibernation problem for you. Are you sure it couldn't be something else?
Hmm, I just tested both Vista and Ubuntu.
Vista-Shutdown : Works fine
Vista-Sleep : Works fine
Vista-Hibernate : Logs me off and stops there.
Ubuntu-Shutdown : Works fine
Ubuntu-Suspend : Complains sometimes, but AFAICS it suspends fine.
Ubuntu-Hibernate : 1:st time locked at startup. 2:nd time couldn't hibernate (shutdown) 3:rd time same errors as 2:nd time but waiting for a little longer it shuts down, it locks at startup after 2-3% (as 1:st time).

And I've not changed Vista in any way the last day (except some defrag and such...)
So I guessed it was the MBR (as XP hibernate seems to use it..)

---

### Post by Zacha on 2007-10-19
Well. As noone answered me anymore can someone just tell me how to change to vista bootloader as my original question was?

(sorry for the double post but this post is about a different thing than my last)

Problem solved.
It hadn't installed GRUB to MBR, ubuntu had just made the ubuntu partition the active one (activated the boot flag on it) so the windows MBR which just boots the active partition booted the ubuntu partition where I had installed GRUB.
A quick google search came up with some ppl who said that the hibernation file must be on the active partition. And as windows couldn't access the ext3 partition it couldn't hibernate.

---

