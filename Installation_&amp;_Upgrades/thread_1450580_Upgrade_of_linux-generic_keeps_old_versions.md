---
title: "Upgrade of linux-generic keeps old versions"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by surferX on 2010-04-09
My installatio with 250mg root partition is nealy full after an updrade of linux-generic which has kept the old kernel and modules.

I can easily delete them or is the a way to instruct apt-get or dpkg to only keep the current version?

---

### Post by jfenn2199 on 2010-04-09
I removed it on my end with computer janitor

---

### Post by moetunes on 2010-04-09
By default apt doesn't remove kernels - I recommend keeping at least one backup kernel just in case

---

### Post by beta.tester on 2010-04-09
> **surferX said:**
> My installatio with 250mg root partition is nealy full after an updrade of linux-generic which has kept the old kernel and modules.

I can easily delete them or is the a way to instruct apt-get or dpkg to only keep the current version?

Hi

There are 2 ways to tackle this and *both* ways need to be handled like eggs => fragile and potentially dangerous:

1) Grab Ubuntu Tweak (download the .deb file and install) and go through the options carefully. (There is one there for the kernel cleaning :)

2) My preferred way is this:

at the command prompt in a terminal, very carefully and double checking your typing:

sudo dpkg --get-selections | grep linux-image

sudo apt-get purge "oldest kernel shown with above command" without the quote marks.

to be safe then run:

sudo update-grub

Hope this helps, kind regards     john

---

