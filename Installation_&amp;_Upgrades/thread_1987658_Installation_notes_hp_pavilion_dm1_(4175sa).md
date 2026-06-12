---
title: "Installation notes hp pavilion dm1 (4175sa)"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by ChrisCamacho on 2012-05-26
hp pavilion dm1 (4175sa)


Noticed flaky results to say the least with another distro, and needed additional steps in Ububtu, so though I would provide my experiences and solutions here...

using jocky install broadcom wireless drivers

jocky will fail to install the ati-updates driver but do it anyway

run

sudo dpkg-reconfigure fglrx-updates

(I think this installs it but at any rate I have good 3d speed)
catalyst control centre reports version
012.036.000.031.041067

I'm guessing future update will need to be done
using the "official" installer ?

edit   /etc/modprobe.d/blacklist.conf

add

blacklist bcm43xx
blacklist hp-wmi

You should find you can disable bluetooth without
it stopping wifi now 

If you want to boot with bluetooth off by default (but still
able to switch on manually if needed)

edit /etc/rc.local 

add

rfkill block bluetooth

but make sure this is on a line by itself and
*before* exit 0 ...

with a fully ubdated Ubuntu 12.04 using the above
I have had no freezes but did get a kernel panic
on shutdown once from the fglrx
but hey compared to random lockups every hour seen with another distro I can live with it!!

If you do the policy kit trick (why disable it by default???)
then even hibernation works fine!
(I know shocking!)

Hope this helps, cause I'm now real happy with my new laptop its actually really nice!

---

### Post by ChrisCamacho on 2012-05-28
The lock ups sometimes don't happen for sometime....

and alas started again, fortunately I noticed an AMD bugzilla post that mentioned upgrading to an earlier driver started the very same problem happening...

So I "upgraded" to the earlier problem free drivers and what do you know no lock ups even with extended minecraft play and also with my shader programming...

In addition 3d seems slightly faster and a lot less "jerky"

amd-driver-installer-12-4-x86.x86_64.run  <-- problems
ati-driver-installer-11-12-x86.x86_64.run <-- GOLD ! :D

The blacklist items in the above post still hold for other hardware issues as mentioned.

I noticed that when returning from hibernation the screen isnt locked which isn't terribly secure on a portable device!

I mapped the "internet" button next to the power button to
the following script...

```

xscreensaver-command --lock
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Hibernate

```

fingers crossed I think I have this thing fettled (I hope NOT famous last words!!)

---

