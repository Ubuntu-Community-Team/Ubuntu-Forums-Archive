---
title: "Mint 16: MDM fails to load during boot - system hangs"
date: 2014-02-05
forum: MINT
---

### Post by PopsTheSailor on 2014-02-05
Something happened to my conf and now during boot, I get an error that says MDM Display Manager failed to load. The other strange thing that happened is that my /etc/fstab file had a swap file entry added to it. I don't use a swap drive and if I look using Gparted the UUID / Drive it not listed. I don't know how this happened but now I can't start up. I get to Grub, select the OS (Mint 16), the little mint logo appears and then I just hang there for ever. 

During boot, if I do an Alt-Ctrl-F6 I can get to a terminal login prompt but don't know where to go from there. Anyone know of a way to do a "reset" on MDM or any other tricks to try?

---

### Post by Bucky Ball on 2014-02-05
*Thread moved to **Other OS/Distro Support**.*

---

### Post by jalver on 2014-05-20
Hello,

I am wondering why this treads is marked as resolved : "[SOLVED] Mint 16: MDM fails to load during boot - system hangs" because I do not see any answer ?
(sorry I am new to this forum and may be I am looking in the wrong place).

Cheers
Jalver.

---

### Post by superian on 2014-06-19
Probably them going 'not our problem'.

It's doing this for me too - if you go to a command line (eg via ctrl-alt-F2) and run 

```
startx
```

it will probably work.

Until mdm is fixed, my solution is to use lightdm instead. See the forum at linuxmint.com for more.

---

### Post by Bucky Ball on 2014-06-19
As this thread was nearly six months dead until it was resurrected, let's call it:

*Thread Closed.*

Please post new threads with descriptive titles and in the appropriate forums for any further issues. Thanks.

---

