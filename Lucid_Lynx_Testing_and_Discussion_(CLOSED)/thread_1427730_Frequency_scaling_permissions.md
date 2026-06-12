---
title: "Frequency scaling permissions?"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rob2687 on 2010-03-11
Since installing Alpha 3 I can't control the frequency scaling without using **sudo cpufreq-selector**. Also the frequency scaling applet for gnome-panel does not work. In previous releases clicking the applet would drop down a menu to select which frequency scaling governor to use. In Karmic it asked for the root password before changing the governor but now there is no options at all. Previous releases didn't even require any root password or elevated permissions at all. 

How can I get it working again without requiring a root password?

---

### Post by mc4man on 2010-03-11
If the applet becomes workable again (should) and a password is required then it should be fairly easy to remove the need for auth. 

If you're the admin user I'd just create a .pkla file to address this.

(have done so in karmic for both accessing (mounting) internal filesystems and the cpu applets. - in lucid the internal filesystems is already taken care of thru UDisks.pkla

The .pkla will not make any difference if running from the command you posted, so atm creating one for the cpu frequency is a moot point and I rather test before posting how,  though can if you wish for when the applet returns

Happen to be on a lucid livecd (03/08)now  and the applets are working fine so I'd expect their use to return 
(the applets don't require auth. on the live cd, probably due to the live-cd.pkla

Don't have an lucid install on my laptop, if I did I would probably use the .pkla though ultimately  I'm not sure of how the whole policykit deal will end up by release.

---

### Post by mdurham on 2010-03-12
see this thread [http://ubuntuforums.org/showthread.php?t=1299820]("http://ubuntuforums.org/showthread.php?t=1299820") it might be helpful.

---

### Post by autark on 2010-03-12
For me, changing any option in the CPU Frequency Scaling Monitor, the only visible effect is this: the SCIM icon is toggled on/off! I don't even get an authorization prompt.

---

### Post by mc4man on 2010-03-12
> see this thread ....
That was in regards to karmic  and the thread didn't get a few warnings about directly editing actions that are in some later posts. (forum closed a few days later.

While editing the action(s) directly does work in karmic and most likely also in lucid, I'd personally refrain from doing so if the desired change could be taken care of w/ a pkla (as things stand now.

( As far as karmic I found 2 changes very useful and they would work either way though settled on the pkla's as the best solution

> 
ls /var/lib/polkit-1/localauthority/10-vendor.d/*.pkla
/var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.DeviceKit.Disks.pkla
/var/lib/polkit-1/localauthority/10-vendor.d/org.gnome.cpufreqselector.pkla



---

