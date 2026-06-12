---
title: "Boot problem following recent 6.10 upgrade"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by Jordan Skittrall on 2007-04-16
After running automatic updates earlier today, my system is unable to boot as far as login.

Using a recovery mode boot option, the boot process gives up with the last lines being:
"
 * Mounting local filesystems...
 * Configuring network interfaces...
[17179596.816000] BUG: soft lockup detected on CPU#0!
"

I am running 6.10 on a Dell Inspiron 6400 (a laptop) with an Intel Core 2 Duo processor.  (The system recognizes this as two processors usually.)

I believe that the earlier update included a kernel bugfix, but I'm not able to confirm this.

I run a dual boot system with Windows, and am still able to get the Windows setup to boot, so I'm guessing it's unlikely to be a hardware problem.

I'd be very grateful for any thoughts/directions to another posting I've missed.

---

### Post by panty31772 on 2007-04-16
Seems some  of this might be relevant to your problem ! 

[COLOR="Red"][https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418)[/COLOR]

[COLOR="Red"][http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/)[/COLOR]
[COLOR="Red"]
[http://ubuntuforums.org/showthread.php?t=322180](http://ubuntuforums.org/showthread.php?t=322180)[/COLOR]

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=251944](http://ubuntuforums.org/showthread.php?t=251944)[/COLOR]

Hope this helps you !!

---

### Post by Jordan Skittrall on 2007-04-17
Turning wireless networking on does indeed resolve the issue.  Thank you for the links (especially as it related not to the update I'd just applied, but to something else I'd forgotten I'd done - d'oh).  I'll attempt to apply the patch when I get a chance.

---

### Post by panty31772 on 2007-04-17
Why you are so very welcome !!! 
Glad to have been able to help  :KS 

Hope the patch works out that annoying little problem for you !

---

