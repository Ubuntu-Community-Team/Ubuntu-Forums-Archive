---
title: "Partial Upgrade in Lucid"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vrkalak on 2010-02-06
I have been testing Xubuntu Lucid 10.04 since it first went to Lucid, and now through each Alpha release.

The Lucid Dist-Upgrades from 2 nights ago, have b0rked my Xubuntu install.
No problem, as it is not my 'main' OS and I kinda expect this to happen, through the early development stages of a new edition.

After downloading and installing the updates/upgrades, the system asked for a computer re-start.  After Grub and the Log-in screen, came the dreaded BSOD.  :( * (black screen of death)*
I've done everything I can to bring it back, but to no avail. I finally have to do a 'hard shutdown'.   I can still get in the b0rked OS by going in through another Linux OS and mounting it.  Or by mounting from the original Xubuntu Lucid A2 LiveCD.  Luckily, all my files, data and such are in a separate */home* partition.

[I][B]If you learn nothing else ... remember this one thing ... _never_ do a "Partial Upgrade".

[/B][/I]Oh, well ... live and learn.  :P

Over all, I am very impressed with the new and coming LTS of Ubuntu Lucid ... the Devs are doing a great job.

---

### Post by philinux on 2010-02-06
The sticky thread #2 has all the advice for this.

---

### Post by vrkalak on 2010-02-06
Now, I really feel 'stupid' . . . how do I delete this thread/post anyway?

---

### Post by philinux on 2010-02-06
> **vrkalak said:**
> Now, I really feel 'stupid' . . . how do I delete this thread/post anyway?

Dont worry we've all done this. ;)

---

### Post by 23meg on 2010-02-06
> **vrkalak said:**
> 
If you learn nothing else ... remember this one thing ... _never_ do a "Partial Upgrade".


That's not exactly good advice. There will be cases along the development cycle where a partial upgrade will be required, such as the case with package name changes, and refusing to do it will lead to your installation not being in sync with the archive.

Take a look at [the sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") for more information.

---

### Post by gjoellee on 2010-02-06
> **vrkalak said:**
> I have been testing Xubuntu Lucid 10.04 since it first went to Lucid, and now through each Alpha release.

The Lucid Dist-Upgrades from 2 nights ago, have b0rked my Xubuntu install.
No problem, as it is not my 'main' OS and I kinda expect this to happen, through the early development stages of a new edition.

After downloading and installing the updates/upgrades, the system asked for a computer re-start.  After Grub and the Log-in screen, came the dreaded BSOD.  :( * (black screen of death)*
I've done everything I can to bring it back, but to no avail. I finally have to do a 'hard shutdown'.   I can still get in the b0rked OS by going in through another Linux OS and mounting it.  Or by mounting from the original Xubuntu Lucid A2 LiveCD.  Luckily, all my files, data and such are in a separate */home* partition.

[I][B]If you learn nothing else ... remember this one thing ... _never_ do a "Partial Upgrade".

[/B][/I]Oh, well ... live and learn.  :P

Over all, I am very impressed with the new and coming LTS of Ubuntu Lucid ... the Devs are doing a great job.

I think that issue can be solved by removing "plymouth".

---

### Post by vrkalak on 2010-02-07
So, how do I get in there, to remove Plymouth?

I can only get into the b0rked Xubuntu Lucid A2 by mounting it from another OS on my PC or by using the LiveCD.  Not even the Recovery Mode of the same disto will work.

If all else fails ... the next Alpha 3 will be released in a couple of weeks.  I can just install A3 over my Lucid A2. [I]
Either way, I'd still like to know how to get in there to fix it?

:P It's all good ... No harm done.[/I]

---

### Post by OrangeCrate on 2010-02-07
> **philinux said:**
> Dont worry we've all done this. ;)

+1, it's how you learn.

If you break it beyond repair, the worse that happens is that you have to reinstall.

No big deal.

---

### Post by ranch hand on 2010-02-07
If you can mount it you can chroot in and run apt to your hearts content.

---

### Post by philinux on 2010-02-07
> **vrkalak said:**
> So, how do I get in there, to remove Plymouth?

I can only get into the b0rked Xubuntu Lucid A2 by mounting it from another OS on my PC or by using the LiveCD.  Not even the Recovery Mode of the same disto will work.

If all else fails ... the next Alpha 3 will be released in a couple of weeks.  I can just install A3 over my Lucid A2. [I]
Either way, I'd still like to know how to get in there to fix it?

:P It's all good ... No harm done.[/I]

I use this script to chroot in from my karmic install on drive one. A live cd can be used too.

My lucid install is on drive 2 which is sdb1.

```
#!/bin/sh

## Directory /mnt/karmic already exists ( create this directory if needed)

sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

fi

```

---

### Post by phenest on 2010-02-07
Boot into recovery, then to a root shell.

---

### Post by Funnnny on 2010-02-07
Do everything you want, and learn how to fix it.
I ran into so much problem when I first time testing 9.04, in 9.10 there's more. Do some partial upgrade, break some package, learn how to resolve it, that's the way it goes ;)
And then you'll realize you need to review what it's going to upgrade ;)

---

### Post by gjoellee on 2010-02-07
> **vrkalak said:**
> So, how do I get in there, to remove Plymouth?

I can only get into the b0rked Xubuntu Lucid A2 by mounting it from another OS on my PC or by using the LiveCD.  Not even the Recovery Mode of the same disto will work.

If all else fails ... the next Alpha 3 will be released in a couple of weeks.  I can just install A3 over my Lucid A2. [I]
Either way, I'd still like to know how to get in there to fix it?

:P It's all good ... No harm done.[/I]
  You can't boot in recovery mode?

---

