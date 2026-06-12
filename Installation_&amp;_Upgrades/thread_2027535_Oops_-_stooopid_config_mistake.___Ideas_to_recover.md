---
title: "Oops - stooopid config mistake.   Ideas to recover?"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by bobmct on 2012-07-16
Hi all,

While creating a new 12.04 LTS server system today I was trying to edit the /etc/sudoers file and couldn't access it.  So I ran a simple  sudo chmod -R 460 /etc which did in fact allow subsequent access.
However, now my sudo doesn't work for obvious reasons.  I've played with the permissions but still have not resolved this and what other potential errors I will experience.

Anyone who may have done something like this in the past may have come up with a remedy.  Hopefully he/she will share that rememdy here?

I wish to avoid reinstalling as I have a solid day of work into this but if I must start over I will.

Thanks for any suggestions you may submit.

Signed:  Old Cranky! :(

---

### Post by sudodus on 2012-07-16
Let us hope someone can give you a quick fix, but I'm afraid you are in trouble :-(

I checked the files and folders in /etc, and they do have several different permissions. It would be possible, but cost a lot of time to reset all of them to the proper permissions. If you fail you might get strange errors in the future or you may compromise the security of your system. So I recommend a fresh install. It will probably be faster this time because you can repeat quickly what you did earlier.

Use ```
sudo visudo
``` to edit the /etc/sudoers file ;-)

---

### Post by bobmct on 2012-07-16
Thanks sudodus.  That was my determination as well.  Just another day to make up.

---

