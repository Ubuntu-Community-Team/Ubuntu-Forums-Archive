---
title: "Time to upgrade from, erm, 12.04 LTS - straightforward?"
date: 2019-07-17
forum: Installation &amp; Upgrades
---

### Post by BolinMDT on 2019-07-17
Hello folks

I haven't upgraded my Ubuntu release for a *little* while - so I'm still running 12.04 LTS.

Yes, I know. I'm sorry. And a bit lazy, and not very motivated when it comes to dealing with computer stuff.

So - I want to upgrade to 18.04 LTS. Which means I don't have to got through with this again until 2023. (In fact, I have never upgraded the distro on the Zoostorm desktop I am using as it was new in December 2012 when I installed 12.04 LTS.)

Will there be any problems with upgrading, given that 12.04 is no longer supported? I intend to back up everything onto USB drives just in case. Having a quick read of the notes on the main Ubuntu website suggests that I need to upgrade to 14.04 LTS, then to 16.04 LTS, then to 18.04 LTS. Will this still work given the seemingly prehistoric nature of 12.04? I don't want to have to re-install, re-format the whole computer if I can avoid it.

I am continuing to read all the info on the main Ubuntu website, and any advice, hints or tips is gratefully appreciated. Confirmation that upgrading will still work OK would be a huge help!

Thank you, Bolin.

---

### Post by westie457 on 2019-07-17
Save yourself some time and heartache.
Because of all the changes and differences between 12.04 and 18.04 it will be easier and quicker to back-up your personal files and do a clean installation from scratch.
Multiple upgrades will take about 2 hours each, and possibly have major breakage for each one A clean install takes about 20 minutes.

---

### Post by CatKiller on 2019-07-17
> **BolinMDT said:**
> Will there be any problems with upgrading, given that 12.04 is no longer supported?
Yes, very much so.

Upgrading from an EoL release is a pain, but doable.

In this case, the one you'd be upgrading *to*, 14.04, is *also* EoL.

You're looking at 3 full system upgrades, each of which will probably take a couple of hours, which aren't guaranteed to work perfectly even under ideal circumstances, and the repositories that you need for the first two have already gone to the graveyard.

A fresh install takes about 20 minutes.

---

### Post by BolinMDT on 2019-07-19
Folks, many many thanks for the advice - glad I asked before ploughing ahead!

Now, I haven't done a fresh installation since December 2012, and that was on a brand new 'empty' computer, so my memory is somewhat hazy on what I need to do......

Presumably I copy all my documents and photos and just copy them back once done, but how can I keep all my open tabs in Firefox? A friend once told me o a 'tab manager' so I will look into that.

Do I need to set up the hard drive partitions again? If so I guess I just need to make a note of how they are now and copy the sizes when installing?

(Apologies for sounding so thick, years ago I used to vaguely know what I was doing, but I have forgotten everything now!)

---

### Post by CatKiller on 2019-07-19
Essentially everything that you'll want to keep is in your Home folder. All of the user settings are there. A lot of people have /home as a separate partition for exactly that reason: they can reinstall the OS on / and mount their /home partition and they're most of the way to having everything up and running again. 

You'll only need to redo the partitioning if you want to. You can just plonk the new ones over the old ones if you prefer.

If you're starting over, one thing to consider is the difference between the old BIOS and the newer UEFI. UEFI is generally better, but the partitioning is slightly different.

The other difference between then and now is that you might have been using a swap partition; for a while swap files weren't quite as good as a swap partition, but that's no longer the case.

A standard 18.04 install will have a single / partition, and an EFI partition if you're using UEFI. Splitting that / partition into a smallish / partition and a large /home partition is a sensible step, but not essential. It doesn't need to be complicated.

---

