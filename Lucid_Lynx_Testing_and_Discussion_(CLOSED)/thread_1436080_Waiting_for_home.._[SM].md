---
title: "Waiting for /home/.. [SM]"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mr51m0n on 2010-03-22
Hello Ubuntuers

I just installed ubuntu 10.04 and then wanted to mount my old home drive on an lvm.

so i installed lvm2 package and then deleted my original homedrive and made an entry in etc fstab to mount my home drive to the right place.

now, when booting up, ubuntu hangs at the boot screen saying "Waiting for /home/simon [SM]".

when starting in recovery mode, i see my homedrive successfully mounted and it belongs to my user and has good permissions...

any idea?

Thanks, Simon

---

### Post by H3g3m0n on 2010-03-22
I had a similar issue here.

In my case it wasn't LVM related, I had an old entry in /etc/fstab of a partition that no longer exists. Rather than silently failing and continuing on it got stuck on it.

I noticed that initscripts package was pulled in an update I did just befoure.

I would assume that the scripts are not correctly detecting you LVM partition mounting and freezing where as in the past they would normally ignore it and keep going.

Last update also managed to break login into X on my desktop, but thats a separate issue.

---

### Post by amsterdamharu on 2010-03-22
Hi Simon,

I read somewhere before that hal is going to be taken out of lucid and that fstab is no longer used. I have no idea what that means but I currently mount my home partition with fstab too and it's working fine. My home is not on an lvm though.

What's in the fstab? I remember mounting my home as /home not /home/ but not sure if it matters much.

Do you get that waiting for message after a login? Strange that anything form home needs to be run before login unless you tinkered with something.

You can try to press control + alt + F1 and log in as root, then check what's mounted, make sure home is mounted and has a subdir called simon [SM] that has the right permissions set up for simon. Maybe it is not writable and mounted read only?

If its mounted type exit to log out and try to log in as the user (non graphic).

---

### Post by H3g3m0n on 2010-03-22
As a quick and dirty hack around it, you can try comment out the fstab entry and mount it manually in /etc/rc.local until it's fixed.

---

### Post by keybuk on 2010-03-22
This is a known bug and will be fixed before Beta 2

---

### Post by mr51m0n on 2010-03-23
Ok, Thank you all!

I could fix it by just moving my home folder entry just below the / entry in fstab :)

Simon

---

### Post by H3g3m0n on 2010-03-23
According to a reply I got on submitting this as a [bug]("https://bugs.launchpad.net/bugs/544223"), the [SM] means you are supposed to press either the S or M key, S skips the entry with the failed mount and the other drops you to a maintenance shell.

So this system wait up is expected functionality (except it needs a better text message).

---

### Post by keybuk on 2010-03-23
> **H3g3m0n said:**
> According to a reply I got on submitting this as a [bug]("https://bugs.launchpad.net/bugs/544223"), the [SM] means you are supposed to press either the S or M key, S skips the entry with the failed mount and the other drops you to a maintenance shell.

So this system wait up is expected functionality (except it needs a better text message).

Except for the additional bug (which doesn't apply in this case) that once it decides that it's bored waiting, it requires you to choose whether to skip it or abort entirely -- if it shows up seconds later, the prompt doesn't go away

---

### Post by Stason on 2010-03-24
I am affected by this around 30% of my reboots. I.e. the fstab entry is correct, but sometimes it does not mount.

---

### Post by sinanju on 2010-03-25
> **Stason said:**
> I am affected by this around 30% of my reboots. I.e. the fstab entry is correct, but sometimes it does not mount.

My fstab is fine as well.  In my case, I have a second disk (EXT4 on LVM on LUKS) for backups.  The second disk uses a keyfile to unlock and mount.  The setup worked fine under Karmic and works about 25-50% of the time under Lucid.

---

### Post by Captain_Kirk on 2010-04-08
> **Stason said:**
> I am affected by this around 30% of my reboots. I.e. the fstab entry is correct, but sometimes it does not mount.


Same here... lately there appears the message telling me I should push S or M... nevertheless it still gets stuck around 30% of (re)boots. Seems that issue hasn't been solved for beta2, yet. :(

So long,
Kirk

---

### Post by Captain_Kirk on 2010-04-09
some "mountall" files got upgraded, but problem still exists... :confused:

---

