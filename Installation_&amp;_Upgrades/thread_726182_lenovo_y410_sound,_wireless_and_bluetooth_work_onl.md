---
title: "lenovo y410 sound, wireless and bluetooth work only AFTER suspend to ram"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by ganja_guru on 2008-03-16
Hi guys,

sound, wireless and bluetooth works only if i suspend-to-ram with Fn+F1, it never works on a clean boot. I disabled the ipw3945 in the restricted drivers manager, rebooted, and modprobe ipw3945, and wireless was working. So what I figure is that at some point in the boot process the bluetooth, sound and wireless modules run into some issues which prevent it from working. Is there some way to delay these modules from loading so that I can load them manually later?

Thanks for all the help.

---

### Post by ganja_guru on 2008-03-17
i tried upgrading to hardy heron alpha, but it looks like this issue isn't resolved with 2.6.24 either.

---

### Post by ganja_guru on 2008-03-17
somehow I think this is distribution specific, with the way ubuntu handles initscripts.. I'll try with some other distros and let you know if it works out of the box...

---

### Post by sberan on 2008-03-29
I'm having this problem with my y410 too, under hardy. Maybe I should file a bug report, I've never done that before.

---

### Post by cevans on 2008-04-13
I'm having the same sort of problem, but only with bluetooth, in Hardy with a 2nd-gen Macbook Pro. I'll look into it further sometime this week.

---

### Post by unicynic on 2008-04-24
It's not distribution specific. I think it's the ACPI script. I see that the proc devices are not created (I think) on boot for the state of the wifi, bluetooth, and hardware mute keys. After you press Fn+F1, it runs the suspend script that create these devices.
The same problem is in Mandriva 2008.1. In openSUSE 10.3 it's worst as openSUSE uses a different key capture for Fn+F1 and just won't suspend at all.
I'm trying the Live of hardy heron and the suspend trick doesn't work. Maybe I need to install first.
FYI, I'm using Lenovo 3000 Y410 too.

---

