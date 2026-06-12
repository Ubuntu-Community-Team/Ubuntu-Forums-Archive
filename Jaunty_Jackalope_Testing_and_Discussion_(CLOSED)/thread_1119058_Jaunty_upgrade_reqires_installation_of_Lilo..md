---
title: "Jaunty upgrade reqires installation of Lilo."
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jheaton5 on 2009-04-07
I upgraded to jaunty from intrepid. to do this I followed these steps:

1. I changed my sources.list file to point to the jaunty repositories.
2. I did sudo aptitude update.
3. Then I upgraded aptitude with sudo aptitude install aptitude.
4. Then I did sudo aptitude full-upgrade.

All went well until the end when I got a message telling me to install Lilo.

>  It seems to be your first LILO installation. It is absolutely necessary to run liloconfig when you complete this process and execute /sbin/lilo after this. 
LILO won't work if you don't do this.

I don't want Lilo, I want Grub.  I have two other distros that boot with grub and intrepid used to boot with Grub.

What can I do to get out of this situation?

Can I just do sudo aptitude install grub instead?

---

### Post by cariboo on 2009-04-07
I have moved your thread to Jaunty Testing and Discussion.

I just ignored lilo, as it gets installed, but not configured. Grub does get installed and configured.

Jim

---

### Post by jheaton5 on 2009-04-07
Thanks cariboo907.

I'll let you know how I come out.

---

### Post by mendres on 2009-04-07
> Ubuntu 8.10 systems installed from the desktop CD mistakenly had the lilo package installed as well as grub, although grub was used for booting. If you use the recommended Update Manager upgrade method, then the lilo package will be removed if it does not appear to be used. If you upgrade using some other method and are sure that you only use the GRUB boot loader, then we recommend that you remove the lilo package manually.

Source: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by jheaton5 on 2009-04-07
Lilo removed

/boot/grub/menu.lst manually corrected

Jaunty is up and running.  Thanks guys

---

