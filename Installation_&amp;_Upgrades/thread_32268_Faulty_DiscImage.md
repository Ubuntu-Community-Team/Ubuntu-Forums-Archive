---
title: "Faulty Disc/Image?"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by edm00se on 2005-05-06
I do not claim to be any linux guru, however I've been using Ubuntu since Warty (about August last year) and have been enjoying it. I haven't addressed this issue at all, since it happened right before my final exam week, and didn't want to think about anything other than failing 15 credits of college. In any case, here's the scoop:
  Approximately 21-April, having upgraded with the final release, to Hoary, I run apt-get update/upgrade and it upgrades about 120-ish MB's of updates. Fine by me. The next time I reboot my desktop, the following day, it doesn't boot. In fact, it doesn't get me to ... anything. I plugged good ol' KNOPPIX (3.8.1) in and check to see if I can get anything off of what I ascertain to be a failing boot drive. I pull my webserver and user directory off the boot drive and stick it onto my second hard drive, which was having no problems and was likely laughing at the other.
  I attempted to do a quick fix and reformat the boot drive and reinstall. My only problem is that in the install process, between the "installing core components" and "installing 'other' components" (might've been additional components, the next phase, if you will) that it'll reach a package, seemingly random, and fail saying "the package is invalid" and "if you're installing from a CD, try burning at a lower speed", etc.
  I've tried burning as low as 1x speed for the install disc from the .iso image from multiple mirrors. I've md5sum checked the disc and it checks out fine. However, should I do a disc check from the installer, it finds itself to be invalid. What I think has happened, but am unsure on how to verify, is that my optical drive (a Rosewill RD-162, 16x Dual Layer DVD+/-RW burner) might be FUBAR.
  What's weirder, now, two weeks later, with a different boot drive (only drive in it at the moment), neither Hoary nor Warty will install, including the Warty install disc (one of the professionally burnt ones from the boys themselves in Europe) that I originally installed from to this machine in the first place.
  Add to that the fact that Debian Sarge is install flawlessly, WHAT IN THE SAM HILL IS GOING ON?!
  So, three possibilities: 1- Ubuntu now hates me (after all the love I've given it), 2-every disc I've burnt is somehow invalid (save when I md5sum check the thing, but not when booted from it in the install), 3- my optical drive is the culpret.
  How can I check this? I'm willing to accept and replace my Rosewill with a better drive, Lite-On for example, however I want to know for certain that it's the bad guy. Keep in mind, Debian Sarge is installed without *any* problems.
  All help is greatly appreciated.
    -A Pissed-Off Ubuntu Quasi-n00b

---

### Post by aragirn on 2005-05-07
(I know edm00se personally, so don't try to figure out where in his post some of the things I reference were mentioned.)

I'm assuming that you've been burning these on your powerbook, and md5ing them there?  (Not that this makes much difference as the pressed Warty CD no longer works either)

Have you tried putting your optical drive on another IDE Channel?

Have you tried putting a different optical drive in the computer? (steal one from another desktop in the house if there is one)

Was the Sarge CD a netinstall?  If so, that might explain why you were able to install... it's possible that your burner will read the first part of the disk, but then bail on a later portion (and will need to be replaced).  But your Knoppix CD is working, so...


I'd recommend trying with a different optical drive (don't buy one yet though), and/or on a different IDE channel.  Let me know how it works for you.

---

### Post by edm00se on 2005-05-07
I *have* tried plugging in a different cd drive, from a different machine, and got most of the way through the install process, however it hung in the "installing additional components" about 39% through, in one of the language packs. I figured, well, maybe it's just a glitch and not the disc drive. However, I've hit a snag: now the installer doesn't recognize my replacement boot drive (an older 6GB Maxtor) as "partitionable media". So, I'm now having to wait until I get my hands on a replacement drive; was going to anyway, just wanted to install first and verify it'd work.
  More news after I acquire my replacement drive, may take a couple weeks. Should I continue running into the same problem, I may try a new IDE cable I have lying around. I'm not excited about it at the moment.
  As for my burning, I *have*  been burning and md5sum-ing on my PowerBook. As for the Sarge install, it was a full disc install. It did some updating from the net afterwards, but was a full install from the disc. On this note, is there an Ubuntu net install disc? I've not been able to find one. Also, would I be able to pass the Hoary install cd any options to install as a net install?

---

### Post by edm00se on 2005-05-13
Okay, here's the skinny. I'm a bonehead, basically. After trying a couple different hard drives, it turns out that I had a busted IDE cable, not by much, but enough, evidently. Now that it's replaced, all is good. Go me.

---

