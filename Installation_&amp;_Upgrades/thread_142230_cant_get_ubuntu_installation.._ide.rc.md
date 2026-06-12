---
title: "cant get ubuntu installation.. ide.rc ??"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Felix21685 on 2006-03-10
hey guys

ive got a Sata RAPTOR which i unplugged.

ive got an older IBM 40GB regular (ribbon cable) EIDE or whatever they are called.

ive tried setting it to cable select or primary.

so i get to the first sceen which asks me to pick if i want the server or desktop install..
i hit enter to do regular install
it loads all the drivers and what not and stalls @

...../ide.rc

ive tried 2 different cds ive had.

not that ive installed ubuntu on this drive in a different computer which had WINXP on it..
i used a win98 fdisk to remove partitions.
i rebooted and still no go.
any help guys?
-Felix

---

### Post by Felix21685 on 2006-03-10
here is where it stops


Running /etc/hotplug/usb.rc
usbcore: already loaded
usbhid: already loaded
usb [success]
Running /etc/hotplug/ide.rc

and then it just hangs..

---

### Post by Felix21685 on 2006-03-10
i guess i will just try to repartition my main sata drive and put it on there...
i just can't get it to work on this second regular drive..

---

### Post by Felix21685 on 2006-03-12
i got another suggestion
from someone on my photo forums 
to try
linux acpi=off noapic

but that didn't work either.

is it supposed to be scpi first then apic second ?

---

