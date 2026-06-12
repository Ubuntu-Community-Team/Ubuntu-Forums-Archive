---
title: "Took the plunge: Now I'm Dapper."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by jonrkc on 2006-06-08
Well...  After a good deal of soul-searching I decided I might as well grit my teeth and try upgrading from Hoary to Breezy to Dapper.  The upgrade from Hoary to Breezy was a breeze, so to speak; but the upgrade to Dapper didn't work.  There was a font problem, among other unknown things, and though I followed instructions given here to show xorg the new location of the fonts, still no go.  

So, knowing I had a disk image (via partimage) of my Hoary installation, and, in addition, a complete backup (via rdiff) to fall back on, I slipped the live Xubuntu disk into the CD drive and experienced high blood pressure and anxiety for about three hours.  

Now I'm to where I can operate halfway normally, but there remains the task of getting apcupsd to work, which is not always easy.  Without it, my UPS backup will operate the computer when the power fails, but won't know how to shut it off.  So that's my next chore.  My firewall is OK (subject to verifying); lm_sensors magically knew how to work (thank goodness: That's always been THE most difficult job after an upgrade or installation); I'm able to obtain the programs I lost after discovering that it really helped to be connected to the Internet before trying to update sources, etc. (can't think of everything).  My own version of OpenOffice.org functions apparently just fine--I was worried about that.  

I copied my home directories and /usr directories from my rdiff backup, using the "u" option (update) so I wouldn't destroy new versions but would add what was missing from the Dapper release.  That worked fine.  

I get some mysterious error messages about device null permission denied, but they don't seem to affect anything.  I habitually just roll up or minimize terminals that are shouting at me like that, because it doesn't do any good for them to do it, usually.  I will check for errors later if I have to.

And that's my upgrade/installation story so far.  It was less painful than many a one I've done; I like the way the installation itself requires almost no user intervention, and it didn't hang up on me at any point.  That's encouraging.

Now to see what goes wrong in the next few days, and if I can fix it with help from the Ubuntu forums.

---

### Post by dtfinch on 2006-06-08
Sounds kind of scary. Any programs you've copied from the old install, apt-get doesn't know about.

What I've always done is choose what I want to keep from my home directory and blow away the rest. Reconfiguring is pretty easy.

---

### Post by jonrkc on 2006-06-08
Some programs aren't available in any of the repositories, so I guess it wouldn't help if apt-get did know about them.  But you made a good point.

I won't part with anything in my home directories!  I'm a pack rat.  That's why I bought a 120GB disk and when I can afford one I'll buy a 400GB one.  :)

---

### Post by jonrkc on 2006-06-09
Oooo-kaaay...  Hmm; I calculate I've spent over 48 hours (that's constant, not counting breaks, sleeping, taking anti-anxiety medicine, etc.) struggling with my Dapper installation.  One moment it seemed delightful, and the next, a nightmare.  Things seemed to break for no reason.  Finally I got to the point last night where I could burn DVD's so I figured I could burn CD's as well.  Went to bed late but happy.

This morning I couldn't boot into the system, and it took me over four hours of steady work to get anywhere--and that anywhere was a restoration of my Hoary 5.04 system from images I'd very luckily made before starting the Dapper stuff, using partimage.  

I'm not giving up.  I'm going to re-install Dapper for the fifth (I think) time, on another hard drive, and see what I can figure out.

So right now I guess I'm kind of a Hedgehog-Drake critter.  No wonder I'm having problems.

The most mystifying part of all this was my inability to restore a working boot system on my hard drive that had Dapper on it (and now has Hoary again).  I have done that several times in the past without a hitch, but today grub was telling me all sorts of things like no file system found, no valid device, etc., even though I followed the notes I'd made after a successful job last week.

I began to think the drive was faulty OR that I'd made some awful mistake in setting up the file system or even in partitioning it.  But since partimage restored the system in 20 minutes or so without a hitch, I just don't know.

**Edit on June 10, very early...**I reinstalled Dapper Xubuntu and so far everything is working, including CD burning...  Managed to salvage almost all my old preferences and settings, too.  And what might have taken a couple of days (and considerable puzzle-solving) to re-install via rpm, took only a few minutes, and involved no puzzlement, using apt-get.  So I'm cautiously happy again, after another full day of working with this thing.  

The installer crashed one time, but on the second attempt it had no troubles.  In my case, it seems much more willing to devote an entire hard drive to an installation than specified partitions; I'm not too fond of that, but I can live with it.  

Unless something goes majorly wrong, I hope I can get by without another installation for three years--when security updates will expire for this release.  

Am I still glad I switched to Ubuntu from Mandriva about a year ago?  Absolutely.  Ubuntu fits my pretty low level of expertise better, is much easier to update, and works better for me in all ways except one: Mandriva allows (or at least did allow) an "upgrade" installation that is actually a repair installation, though not advertised as such.  Many times I recovered from a bad system failure by merely "upgrading" from the original installation CD's.  So far, Ubuntu, to my knowledge, is not so equipped.  I think it would be a good idea to implement.

---

