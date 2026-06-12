---
title: "Ubuntu crashes consistently with Thunderbird"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by Krallus on 2007-11-17
I've been having various stability issues ever since upgrading from Fiesty to Gutsy.  This latest one is consistently reproducible after every boot of Ubuntu: when I open the "Search Messages" dialogue in Thunderbird, the system freezes, forcing me to reboot.

Suggestions?, Fixes?

Thanks.  

PS: Note that I was really happy with the previous version of Ubuntu but I'm very much regretting the upgrade to Gutsy.  I would prefer to NOT to have to go through the hassle of downgrading or switching to a different OS, as I've really gotten used to Ubuntu since I started using it in February.  I'd love instead if these buggy quirks can be worked out.  Some other ones I'm having are: i) Login screen resolution/refresh does not correspond to xorg.conf,  ii) video playback is grainy/green/snowy, iii) I had at least one spontaneous crash while GnuCash was open and Rhythmbox was playing some music.  I know that my video card may be outdated: ATI All-In-Wonder Radeon 7200, but I had none of these problems in the previous version.

---

### Post by Krallus on 2007-11-18
While I did force fsck a few times on the filesystem without any effect, it does appear nevertheless that the problem was a file corruption.  I moved the ~/.mozilla-thunderbird folder to ~/.mozilla-thunderbird-OLD and then copied that back to ~/.mozilla-thunderbird and voila: no more freezes with Thunderbird's search dialogue.  I went ahead and did this with my whole home directory and hopefully that will resolve some of the other instability problems I've been having.  I do know that many of the screensavers still lock up my system, regardless of the above, which is why I only use a blank screensaver now.

---

