---
title: "ata8: Classification failed"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Fafnr on 2008-04-24
I'm hoping this is the right forum - if not, I'm sure someone will set me right. :-)

I just installed 8.04 (yay!) but unfortunately, it seems to dislike one of my drives intently.
During boot (I disabled the splash-screen so I would get more info) it says:
ata8: Classification Failed
and then retries several times. First at 10 sec intervals, then 35. All this means a boot takes me roughly 5-6 minutes... Completely unacceptable.

This probably isn't an Ubuntu problem per se - might just be something I did, or a drive-check I need to run or something... But I have no idea. 

Any thoughts are welcome!

Regards,

Søren

---

### Post by Fafnr on 2008-04-25
This is really serious - at least for me - so: bump.

---

### Post by Fafnr on 2008-04-25
Some further information:

ata4: classification failed
ata4: reset failed (errno=-22), retrying in 10 secs

and so on... Please! ANYONE!
What can I do?

---

### Post by sgroarke on 2008-05-06
Hi Soren

Are you still getting this, 'cos I've got a completely knackered system with the same thing!

What I get is the same sort of message as you, but the ata8 is sometimes another number (ata4, etc.)

It tries several times, then it all times-out and falls through to a busybox shell.

Yet I can boot off the 'old' kernel (pre-8.04) fine.

One question: my system has a mix of SATA disks and IDE disks, and some funky grub config to allow the dual-boot environment I need (and under 7.10 it all works fab). Do you have anything similar I wonder?

Cheers,
Sean

PS I have upgraded 3 (very different) system to 8.04 in the last week or so and each one has gone very badly (albeit in very different ways) The Ubuntu guys have some serious quality issues with the upgrade process...

---

### Post by Fafnr on 2008-05-17
Hello sgroarke,

Yes, I'm still having the same problem, though I have yet to update my Ubuntu-installation with any new packages since release. I don't have the patience to wait for it to boot, TBH.

I havn't tried an earlier Ubuntu version, but I DID have Kubuntu 7.10 for a while, before deciding to try Ubuntu 8.04 - and that booted just fine. 

I too have a funky combination of SATA and PATA disks, though I havn't looked in the grub configuration - Ubuntu handled all that very nicely without me having to look at the gritty details, luckily. I am running on an MSI Neo Platinum (I forget which it is exactly, but it runs with a Core 2 Duo) with the newest BIOS (I think 1.18 or 1.19), and 2gb of RAM.

I upgraded my Laptop from 7.10 to 8.04 without any problems (luckily!) but I too have had strange problems in 8.04 that detracts from my "it just works"-perception of Ubuntu. :/
Though probably not all of it is Canonicals fault - like Firefox 3 constantly crashing, or every single icon flickering for 5 seconds when opening the lid of my laptop - it's still very annoying.

Please, should you come upon any information on how to fix this, I would be very grateful if you posted it here!

Regards,

Søren Andersen

---

### Post by sgroarke on 2008-05-17
I have done a *lot* of research in to this issue in the last few days and I must say it is, to coin a very English phrase, a "can of worms". :-)

When digging in to this one finds that there is a long history of issues with the pata_jmicron driver. The symptoms vary a lot, but all seem to boil down to variations on "takes a long time to work" or "stops working after a while".

Like you, Ubuntu 7.10 worked fine for me. That was kernel 2.6.22. But it looks like 2.6.24 (used in 8.04) has some catastrophic jmicron bugs. 

At first I assumed it was just a Ubuntu issue (and the fact they did not spot it in testing is a fault against them!) but it turns out it's widespread. I took the recent Fedora 9, released a few days ago, and it has *exactly* the same issue. Guess what? It's using 2.6.24 too...

I even yesterday built a stripped-down kernel for 2.6.24. Very minimal. Almost no modules - everything built-in (including the jmicron stuff). Guess what? Just as useless.

This is a bone-fide non-Ubuntu-specific kernel bug. If I had more time I'd look more deeply into fixing it. But frankly, why bother? Being a pragmatist, just deinstall the 2.6.24 kernel from 8.04 and use the 2.6.22 kernel. The chances of you (or I or anyone) actually needing something in 2.6.24 not present in 2.6.22 is very very small...

Sean

---

### Post by Fafnr on 2008-05-18
I have to admit - I'm impressed! I'm the lazy kind of linux user - the kind that, if it doesn't work, spends about an hour trying to figure it out, and then goes back to something that actually works! (BTW - wasn't that the original argument for going from Windows to Linux? I forget. ;)

Anyway, 'tis nice to know it's not just Ubuntu that's the problem.

Thank you for looking so deeply into this - I have to admit that I don't yet feel confident building my own kernels (well... At least I'm too lazy to spend the time needed to understand what to do ;) and I didn't even think of trying another distribution to see if the bug was present there as well!

As soon as I get home, I'll try downgrading my kernel - hopefully I can then enjoy Ubuntu outside of my Laptop :-)

Regards,

Søren Andersen

---

### Post by Fafnr on 2008-05-18
So, I'm home and I want to install the 2.6.22-14 kernel - how do I do that, seeing as it's not in the repository? 

Regards,

Søren Andersen

---

### Post by Fafnr on 2008-05-19
Using packages.ubuntu.com I installed the 2.6.22-14 generic kernel. 
However, after installation, my graphicscard is no longer recognized, and I can only run in 800 x 600 or 640 x 480... 

I guess I will have to wait for some kernel-update, before I can use Linux with my Desktop... :(

/Soren

---

### Post by Jugalator on 2008-05-22
I also started getting this just now, ata4: Classification failed, a few retries, messages on that it can't reset "ata4", and finally a message on "limiting speed to x Gbps", but still having the boot stall. A reboot and still the same thing. I'm using Ubuntu 8.04 and everything worked fine the first week or so.

I haven't reconfigured neither my hardware nor any "depths" of the system. The only file I've really touched would be the grub boot config file to change a boot device, but that was a while ago and didn't cause any ill effects at the time.

So I wonder what the trigger is.

I also have a mix of ATA (my DVD) and SATA (hard drives) devices, and all I'm really wondering right now is which of those devices "ata4" might be for me... I don't even use that many **ATA** devices, if it's enumerating them from ata1, that is.

Edit: Moonswan has some info, but no actual fix, here on the Arch Linux forums (obviously a cross-distro issue): [http://bbs.archlinux.org/viewtopic.php?pid=360567#p360567](http://bbs.archlinux.org/viewtopic.php?pid=360567#p360567)

---

### Post by nxt on 2008-06-20
I am having the same problem too. I can still boot with the 2.6.22 kernel from 7.10, but I end up with 800x600 resolution unable to compile the new nvidia driver as it uses the new kernel :(

The same issues is with the clean install - ending in BusyBox.

This is a real problem for me, because I have not been able to do any serious work on my computer for more than 2 weeks now. I hope this will get fixed soon as I do not want to reinstall my whole computer.... god knows what I might install. :(

---

### Post by Dr. Akam on 2008-06-25
> **nxt said:**
> I am having the same problem too. I can still boot with the 2.6.22 kernel from 7.10, but I end up with 800x600 resolution unable to compile the new nvidia driver as it uses the new kernel :(

The same issues is with the clean install - ending in BusyBox.

This is a real problem for me, because I have not been able to do any serious work on my computer for more than 2 weeks now. I hope this will get fixed soon as I do not want to reinstall my whole computer.... god knows what I might install. :(

Take a look at the link that as been posted here.

At the Arch Linux Forum they have a patch.

[http://bugzilla.kernel.org/attachment.cgi?id=16498&action=view](http://bugzilla.kernel.org/attachment.cgi?id=16498&action=view)

That is the link for this patch.

I had some time to test this patch but for me it changed nothing.
I was hit by this problem today and I don't know why. I changed nothing on my system.

Is there a bug report on launchpad?

Regards
Dr. Akam

---

### Post by Dr. Akam on 2008-06-26
No boot problems anymore. :-D

I disconnected my computer from the current for about 2 hours.
Now it starts within seconds.

I have no error messages in my kernel log anymore.

I hope this information is helpful.

Regards
Dr. Akam

---

