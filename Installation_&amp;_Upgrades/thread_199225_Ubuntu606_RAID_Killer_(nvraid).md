---
title: "Ubuntu606: RAID Killer (nvraid)"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by kelpdip on 2006-06-18
2xhdd: Windows RAID 0 (fakeraid)
1xhdd: Linux Only

I suppose this post is at least half rant. I'm very disappointed with Ubuntu. I figured I should try it because it has been #1 on Distrowatch for some time now.  I was pleasantly surprised by the install method until I saw the "writing bootloader to hd0" message flash by. My first reaction was to yank the cables on my raid array, but I knew it was too late. There was no bootloader configuration the way SuSe always has had, just partition setup. I figured it would either ask me later or assume I wanted it on the same physical disk the OS was going on. Thank god for important data backups. And no, windows recovery fixmbr/fixboot/rebuild did NOT work, the RAID was trashed. I'm back to SuSe now with the higher level of install configuration and have never had a problem with it messing with things it shouldn't before asking my permission. From the live CD Ubuntu looks great, but this experience will probably keep me away from it for a while.

Also, I'll save the next poster the troubleof posting (what would have been) useful links:
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

