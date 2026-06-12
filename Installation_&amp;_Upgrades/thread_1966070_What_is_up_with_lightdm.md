---
title: "What is up with lightdm?"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by hiro24 on 2012-04-26
I've upgraded 2 boxes today to 12.04, a desktop and a laptop, and on both I'm having absolutely no joy with lightdm.  On both boxes it's just... hanging.  I've tried several different things, but no luck w/ anything.  I'm trying to find other ppl who have problems w/ it.. surely I'm not the only one.  Does anybody know what's going on?  It just... hangs.  It never comes up.  I can Ctrl-F4, login and startx and get my interface fine, and if I install gdm I have a login prompt on reboot.. it's just lightdm that's herpa derp right now.

Please, does anybody know what's causing this, or what a fix might be?  I'll shoot any logs back you're looking for.

---

### Post by hiro24 on 2012-04-26
Anybody?

---

### Post by jadtech on 2012-04-26
yor not the only one there are others here today right on this forum same issues look through maybe one is solved it ..

---

### Post by hiro24 on 2012-04-26
I assumed there were others but I thought surely there'd be some sticky maybe about it. I mean it's a pretty serious problem and so far I'm 2 for 2 machines with this problem.

---

### Post by jadtech on 2012-04-26
yeah my thought is I hope all are going to luanch pad and putting in the bug reports on these issue to help them selves and others, with these issues in  the future   ..

---

### Post by techsupport on 2012-04-26
> **hiro24 said:**
> I assumed there were others but I thought surely there'd be some sticky maybe about it. I mean it's a pretty serious problem and so far I'm 2 for 2 machines with this problem.

You would need to find the actual related bug report in launchpad. I didn't bookmark it, but I did find it and it explained what is going on.  Just switch to GDM for now if you need to enable 3d in Ubuntu, and remove LightDM for now until it is patched. But otherwise, just drop to Ubuntu 2D session for now, until they patch it.:P

---

### Post by hiro24 on 2012-04-28
Oddly enough I've fixed the problem on my desktop.  It turns out auto login was causing some type of problem.  When I turned off auto login, suddenly lightdm would start coming up for me.

However, it's not coming back up when I log off.  Anybody know what could be causing this?  Man, lightdm is starting to look like much more trouble than it's worth..

---

