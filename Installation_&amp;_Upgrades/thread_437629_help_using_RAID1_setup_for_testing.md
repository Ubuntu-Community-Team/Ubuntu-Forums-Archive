---
title: "help using RAID1 setup for testing"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by summersab on 2007-05-09
This SORT OF fits under the Installation forum. I figured I wouldn't clutter General for a change . . .

So here's my scenario. I'm tired of breaking my default installation by playing with things, so I wanted to make a setup specifically for the purpose of testing / experimenting / purposefully breaking. My idea to make this simple is to create a RAID1 setup from spare drives and purposefully remove a drive from the array as a clean copy after install. This way, I could mess around with the existing drive and break it until I feel satisfied. Then, in order to reinstall, I boot from the other (clean) drive and restore the array to the junked up drive.

It sounds great on paper, but would it work? I ran into a few problems. First, I had to make sure that GRUB was installed on each drive. Easy enough. Now a lone drive won't boot. Crap. Why can't I boot a single drive from a broken RAID1? My last question is complicated. How, once I break my setup, do I go about booting SPECIFICALLY from my clean drive and restoring my setup to the junked drive? That's it. Thanks for your help, and if it works, I think that this is a GREAT way to test out release candidates. Cheers!

---

