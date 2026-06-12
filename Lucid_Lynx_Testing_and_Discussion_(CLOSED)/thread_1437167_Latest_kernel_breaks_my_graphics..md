---
title: "Latest kernel breaks my graphics."
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Owen.C93 on 2010-03-23
Hmmm -17 kernel doesn't agree with my graphics and it just crashes at gdm.  The os is fine but my screen is a bit odd.

Is there an easy fix or does anyone know how to perhaps reinstate nouveau from recovery mode?

edit: Now my grpahics is messed up on boot with -16 aswell. -15 seems ok so far.

---

### Post by Dilutu on 2010-03-23
It breaks my X too.I can boot into recovery mode to console just fine but when I try to startx, my monitor shutts off! I 'm using a nvidia 4000mx card. 16 still boots ok.
Th.

---

### Post by Owen.C93 on 2010-03-23
I fixed mine :D:D

What worked for me was going to /etc/X11/     and then there should be a xorg.conf     for some reason mine had vanished but I had a failsafe. So I copied and pasted that and re-named it    xorg.conf

And then it worked. Let me know if it works for you :)

---

### Post by yoasif on 2010-03-23
I am seeing this as well, and I can't get into a console to even report a bug.

Has any bug been submitted? posting from the -16 kernel right now, which thankfully works fine.

---

### Post by Owen.C93 on 2010-03-23
> **yoasif said:**
> I am seeing this as well, and I can't get into a console to even report a bug.

Has any bug been submitted? posting from the -16 kernel right now, which thankfully works fine.
I'm not sure what's wrong. Have you tried checking for xorg.conf?

If others can confirm this is the cause then I can file a bug.

---

### Post by Dilutu on 2010-03-23
I Haven't had any xorg.conf for some time now (no need to with nouveau?)...

---

### Post by Owen.C93 on 2010-03-23
> **Dilutu said:**
> I Haven't had any xorg.conf for some time now (no need to with nouveau?)...
Not sure, either ten reboots did it and it was a coincidence or not. I think you might need it for first boot. I had the file in the x11 folder already and I just renamed it.

---

### Post by yoasif on 2010-03-23
> **Owen.C93 said:**
> If others can confirm this is the cause then I can file a bug.I don't have an xorg.conf -- just using Xorg autoconfiguration.

---

### Post by Dilutu on 2010-03-23
I tried rebooting a couple more times into 17, but no luck....

---

### Post by cariboo on 2010-03-23
Try:

```
sudo Xorg -configure
```

to create an /etc/X11/xorg.conf file.

---

### Post by yoasif on 2010-03-23
i don't want to create an xorg.conf file, as it is, this is broken -- looking for a way to submit  or add to a bug. 

xorg has worked fine without an xorg.conf on my hardware for at least two revisions of ubuntu.

---

### Post by Owen.C93 on 2010-03-23
> **yoasif said:**
> i don't want to create an xorg.conf file, as it is, this is broken -- looking for a way to submit  or add to a bug. 

xorg has worked fine without an xorg.conf on my hardware for at least two revisions of ubuntu.
I know but if someone with the bug can confirm adding a xorg.conf fixes it then this will help get a fix.

You can always delete it afterwards if you wish but it would be useful to test it out.

---

### Post by Dilutu on 2010-03-23
I tried "sudo Xorg -configure" but this is what I got:
"(EE) DRM NO DRICreate PCIBusID symbol
number of created screens does not match number of detected devices
configuration failed"
Th.

---

### Post by Dilutu on 2010-03-23
Manually made an xorg.conf (in fact I used a modified failsafe xorg.conf). this way, I was able to boot into 17, although in "low graphics mode"....
Th.

---

### Post by yoasif on 2010-03-24
submitted a bug report for my machine. [https://bugs.launchpad.net/bugs/545749](https://bugs.launchpad.net/bugs/545749)

---

### Post by hype on 2010-03-24
Did you do a partial upgrade?
Because i still get a proposal for a partial upgrade, and some updates are available since yesterday.

---

### Post by yoasif on 2010-03-24
nope, i always upgrade via aptitude, and only rarely do i manually install packages that are left behind. this was not a result of a partial upgrade fiasco. ;)

---

### Post by Dilutu on 2010-03-24
Well latest round of updates fixed it for me. I can now boot into 17 without xorg.conf!
Th.

---

### Post by kyleabaker on 2010-03-24
Check this:
[https://bugs.launchpad.net/ubuntu/+s...rs/+bug/545499](https://bugs.launchpad.net/ubuntu/+s...rs/+bug/545499)

---

### Post by wnelson on 2010-03-27
I noticed that nouveau is black listed

/etc/modprobe.d/blacklist-kernel-nouveau.conf

could this be the problem?

---

