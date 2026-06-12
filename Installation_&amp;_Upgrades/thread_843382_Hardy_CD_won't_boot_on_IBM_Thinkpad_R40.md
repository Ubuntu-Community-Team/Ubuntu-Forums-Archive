---
title: "Hardy CD won't boot on IBM Thinkpad R40"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by battyice on 2008-06-28
This morning I decided to install hardy on my IBM thinkpad R40, which has never given me installation issues in the past.  Gutsy ran great on it with no tweaks, as well as Debian Etch.  

The Hardy cd will not boot into the livecd environment, it hangs when the progress bar is about 20% across under the Ubuntu logo.  At this point all harddrive activity stops, the cdrom stops, and the machine requires a manual reset.  I was able to install using the alternate cd, but encountered the same hanging issue when the system tried to boot for the first time.

Any ideas?  I love running hardy on my desktop, would be nice to have it on the laptop as well.

---

### Post by battyice on 2008-06-30
I did some more searching and decided to try "noacpi" the boot prompt, the machine still hangs.

---

### Post by oceallaighm on 2008-06-30
Hi,

I has the same problem on a Toshiba L300D-10Q as well as using noapic at the boot screen, I also had to disable the internal network card in the bios. Note my network card is a Realtek RTL8102E. After this both the 64 bit and 32 bit Live CD's could fully boot into the Desktop.

It may be the network card or another piece of hardware that Ubuntu does not like.

I hope that this is of some help.

---

### Post by battyice on 2008-06-30
I can try disabling some of the integrated devices to see if that makes a difference.  As a short term solution I installed dapper on it last night and that is running great.

---

### Post by upchucky on 2008-06-30
just a guess

xorg.conf is choking it when trying to load splash screen? try basic xorg?

---

