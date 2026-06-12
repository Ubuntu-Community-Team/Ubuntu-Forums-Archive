---
title: "Gimp doesn't start"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2011-04-30
Fresh install of Kubuntu 11.04 amd64.
Gimp doesn't start from the menu.

From command line, it gives this error message.
```
(gimp:6702): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault
```

Is this a bug, or something I can fix?

TIA

Peter

---

### Post by jynyl on 2011-04-30
It's a bug; #742516 at launchpad.
There is a workaround at Launchpad;
- change GTK+appearance to Rayleigh
- start Gimp and stop it
- change GTK+ appearance back to oxygen.

This seems to work for me.

---

### Post by onewing on 2011-05-05
Thanks, jynyl. Had the same problem. That solution worked. Your was the first google result I tried.:popcorn:

---

### Post by jakslev on 2011-05-07
HI5 - that worked. Pretty silly :)

---

### Post by kalafox on 2011-05-16
It worked for me too, many thanks.

It's really a weird solution however !!!

---

### Post by theOGRE on 2011-05-17
Worked for me as well.  Silly, but thanks for the workaround.

---

### Post by monkotronic on 2011-06-10
incredible.  worked for me as well.

---

### Post by Nayar on 2011-06-18
Great :D

Anyways, hope the devs fix the bug.

---

### Post by jconstantino on 2011-07-12
thank you :)

---

### Post by tarahmarie on 2011-08-20
WTH? 

Thanks!

---

### Post by NikoC on 2011-10-11
Just installed gimp from ppa (ppa:matthaeus123/mrw-gimp-svn) and problem seems to be fixed!

---

### Post by ADani on 2012-03-08
> **jynyl said:**
> It's a bug; #742516 at launchpad.
There is a workaround at Launchpad;
- change GTK+appearance to Rayleigh
- start Gimp and stop it
- change GTK+ appearance back to oxygen.

This seems to work for me.

Had the same problem, thanks.
I sort of remember doing this a while back, but I don't think it was for Gimp... I think I'm going to go try this in another computer that has an unrelated ubuntu issue, who knows, it might work!

---

