---
title: "Couple of kernel questions?"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by RecoilUK on 2008-11-29
Hi guys

Is there a quick way to check the options the default kernel was compiled with?

And, if I need to recompile it, are there any special precautions I need to take, if i,m running the ATI closed source drivers?

Thanks.

p.s I have tried a few different distro,s over the last few days, namely SUSE, Mandriva, Fedora, Debian, Ubuntu and now finally Xubuntu which was just what I was looking for, congratulations to the whole Ubuntu team, job well done.

---

### Post by ibutho on 2008-11-29
Most distros have a file called config (or config-$VERSION) in /boot. I am sure thats where the default options can be found.

---

### Post by markbuntu on 2008-11-29
The new ati drivers are dkms so just be sure to include that in your new kernel build.

---

