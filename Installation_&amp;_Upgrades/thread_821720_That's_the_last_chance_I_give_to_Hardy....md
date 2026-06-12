---
title: "That's the last chance I give to Hardy..."
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by derfinsterling on 2008-06-07
Ok, I've had it with Hardy.
Since the upgrade I've had nothing but problems. I had to reconfigure sound and printing. I was no longer able to access my external harddrive (or the internal NTFS partitions), although everything was installed - but for some bizarre reason, the link that pointed to libfuse was no longer valid.

I've fixed all of this, especially with the help of this fine forum here.
Then another upgrade rolls in and I can do it. all. over. again.

I'm sick of it.

So the last chance I give Hardy before I switch to another distro: I'll do a clean install.

Now, here's my question: Do I have to save everything in the home directory or is it enough (since it's a separate mount point - or used to be, till the upgrade, I guess I have to check that as well) to run it from CD as a clean install?

Also, was will happen to my Windows partition (if anything)?
If it's lost, that's not that bad, I use it only for games anyway. Would still be nice to know beforehand so I can backup my savegames.

Any advice you fine folks can give?

---

### Post by cubeist on 2008-06-07
> **derfinsterling said:**
> Ok, I've had it with Hardy.
Since the upgrade I've had nothing but problems. I had to reconfigure sound and printing. I was no longer able to access my external harddrive (or the internal NTFS partitions), although everything was installed - but for some bizarre reason, the link that pointed to libfuse was no longer valid.

I've fixed all of this, especially with the help of this fine forum here.
Then another upgrade rolls in and I can do it. all. over. again.

I'm sick of it.

So the last chance I give Hardy before I switch to another distro: I'll do a clean install.

Now, here's my question: Do I have to save everything in the home directory or is it enough (since it's a separate mount point - or used to be, till the upgrade, I guess I have to check that as well) to run it from CD as a clean install?

Also, was will happen to my Windows partition (if anything)?
If it's lost, that's not that bad, I use it only for games anyway. Would still be nice to know beforehand so I can backup my savegames.

Any advice you fine folks can give?

Well, as I am sure you know, you can't downgrade an OS. You will have to reinstall, which includes backing up first.  In my opinion this will cause you more headaches than the few problems you have experienced with hardy... I would recommend sticking with it... especially if you have fixed your printing and sound...

---

### Post by derfinsterling on 2008-06-08
I know I can't exactly downgrade... I'm going for a clean install of Hardy. I really liked Ubuntu so far, but these crappy updates and upgrades make me think of switching distros.

I have a file on my desktop where I have the necessary commands written down in case (most of the time) that an update screws up the link to the correct libfuse version.
I just get tired of having to do it again and again and again.

Sound is affected with roughly every other or every third update. So I have to search this forum *again* to see what I did the last time to fix it.

---

### Post by loell on 2008-06-08
if your home is on a separate partition, then just install another distro of your choice, your files in your previous home partition will still be there.

if you're gonna reinstall hardy which gives you problem after updates, then either use gutsy or feisty or choose other distro.

---

### Post by fhmanas on 2008-06-08
If you want it really clean, might as well start from scratch, backup your data from your home folder and reformat, as leaving your home intact might leave you some config files/garbage you don't really need.  Also, from my experience at doing the upgrade route from gutsy to hardy, it was actually slower and harder.  A clean install is easier but not beset with it's own problems.  Hardy had a lot of problems with the clean install which I did not get from Gutsy, but I stuck with it and after some time I have configured it to the way I liked it.

But whatever, your decision, I suggest creating backups just in case.  Harder to reconstruct data than just restoring a backup.

---

### Post by derfinsterling on 2008-07-13
So, I backed everything up, formatted the linux-partitions and made a clean install to get rid of the annoyances (I wouldn't really call them problems), as a few folks here suggested.

The installation went surprisingly fast, so fast that I was sure that I'd have to do a lot of fiddling around.
But... sound works, harddrives are detected, xserver runs smooth... I was pleasantly surprised.

But then, alas, I found out that the damn printer won't print again. Like it first did when I switched to Ubuntu, back in the days od Edgy.

Tried the old solutions, nothing (so far) worked. My last resort is the AppArmor - somebody suggested putting cups into complain mode. We'll see how that works once I have finished printing the 200+ pages from my windows notebook.

I'm using the 64bit Hardy installation (I figure if I got the architecture, why not use it?), but from some of the comments I found here I'm afraid that my Epson Aculaser C1100's driver doesn't run in that environment.
I'm puzzled why I would be able to install it, though... Anyway, let's see how everything turns out. If I don't get the printer to run*, I don't know, I might switch to another distro. Don't think that this would actually fix the printing problem, but then I could say that I tried everything.

If somebody has any advice to offer, I'd be glad to hear it.



*[rant]Ok, I know that this isn't Ubuntu's fault that a driver that's provided by a third-party-company supposebly doesn't run in a 64bit environment, but COME ON! I don't care, who's responsible, but neither the printer model nor 64bit architecture are exactly new. Shouldn't *they*'ve been able to do something about that??!?[/rant]

---

