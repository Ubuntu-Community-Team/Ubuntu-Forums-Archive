---
title: "upgrade to 12.10"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by duplicate on 2012-10-21
In response to an email from System76, I have attempted an upgrade to 12.10 from 12.04.

The chief reason for wanting this release is the promise of the built-in coolkey pkcs#11 support for my CAC card.

I downloaded the .iso and burned the image to a DVD, and the install completed, but now I only arrive at a grub rescue> prompt.

I have been trying to follow the instructions here:
[http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)

I have located the ubuntu partition and found the grub .mod files and set the prefix to that directory (reading the link above will explain what that means)

but the bigger problem -- bigger than poking through and hoping to fix the grub menu manually -- is that the system keeps shutting off after x minutes (1, 10, a few).

Even rebooting to the LiveCD and choosing "Try Ubuntu" does the same thing.  I can work for maybe a few minutes (like to read/post here), but it shuts off intermittently without warning.

I am reduced to using my wife's MACbook to post here with a duplicate account.

I have decided that I have made so many modifications to my system that I need to do a clean install, but I would really like to get into the system to save personal files to CD first.

Can you help me get back in to get ready for a new install?

Thanks,
Daniel

---

### Post by b9k9kiwi on 2012-10-21
> **duplicate said:**
> 
...
to save personal files to CD first.

...


You might have done this prior to attempting the upgrade, of course :(

You should be able to boot from the installation DVD to locate personal files and copy them to an external drive (dunno about burning to CD though).

---

### Post by duplicate on 2012-10-21
As far as booting to the LiveCD, I can, but I gave up after the 8th or 10th time it shut off unexpectedly.  I'm hoping it is just overheated temporarily, but I've never had a problem with that until today, even though I often leave it on for days on end.

Most of my important files are on UbuntuOne, but I have USB sticks I can save files onto.  The real problem is keeping it awake long enough to accomplish this.

Daniel

---

### Post by b9k9kiwi on 2012-10-21
If you have another box available, you could put the failed upgrade disk into that as a second drive and suck the files across to the first drive.

---

### Post by Jedcurtis on 2012-10-21
> **duplicate said:**
> As far as booting to the LiveCD, I can, but I gave up after the 8th or 10th time it shut off unexpectedly.

Daniel

Have you tried to boot using a different Live-CD distro, or previous version Live-CD; i.e. Ubuntu 12.04?  Just a thought...

Jed

---

### Post by duplicate on 2012-10-22
Update:

I let the box cool a while, then "Reinstalled 12.10", but this time I wiped the drive and set up a new partition table.  The install completed, all the way to the point of reminding me to take out the installation media before rebooting.  When it came back up, it again dropped me at a grub rescue> prompt, and the only command it seems to recognize is ls.

I can only get online from booting to the LiveCD, so I can't really affect my installation from there.  I am truly stuck.  I hoped a fresh install would correct the booting issue, but alas, no go. I have trie to follow the instructions on the page I mentioned above, but get errors at every turn.

grrrrr

Daniel

---

### Post by duplicate on 2012-10-22
P.S.: Yes, I have a LiveCD from 11.10, I believe, or 11.04, but what can I do to repair grub from there?

---

