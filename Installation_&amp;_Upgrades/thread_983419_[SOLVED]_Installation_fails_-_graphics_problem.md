---
title: "[SOLVED] Installation fails - graphics problem?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by psylinux on 2008-11-15
[FONT="Arial"]Tried installation of 8.10 - installation went fine until the (presumably) last point - final message is along lines of 'Checking battery [OK]', then dailog appears saying something like 'graphics system restarted 6 times in last 90 seconds - something is very bad - trying again in 2 minutes |OK|' (sorry for not being more precise, but I've tried thrice to install and I'm not going through all that long wait just to check an error message:???:](*,))

Just goes round in circles until eventually appears to hang
I have nvidia 7900GT running dual Viewsonic VP930 monitors. On 1st install attempt the second monitor showed pretty garbage, on 2nd attempt it mirrored the primary all the way through, on 3rd attempt I unplugged the DVI connector - all ending up in same error.

My system is AMD 64 X2 4400+, currently with 2 installs of XP (on separate HDs, one for gaming and experimenting, the other for serious:wink: work)

Any ideas how to complete the install?
[/FONT]

---

### Post by Partyboi2 on 2008-11-16
Have you tried installing using the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/intrepid/") which is a text base installer?

---

### Post by psylinux on 2008-11-29
Thanks - although the use of the alternate disc didn't solve the problem directly, it did help me figure it out. It was something to do with an abandoned vista install and the fact that my primary partition is not where ubuntu's boot manager expected it to be. A quick check on the net, a re-installation of grub, and an edit of the grub installer file got ubuntu up and running alongside my two XP installs.

I've got my dual monitors working fine, thanks to nvidia's panel, but my Creative X-Fi xtreme music seems to be a hopeless case. Guess I'll have to wait for someone with more up-to-date skills than I to revamp the driver, now that Creative's abandoned the task to the open source community. Go Team!

Ta

---

