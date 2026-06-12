---
title: "splash screen resolution problems"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by flecktor on 2010-07-02
hi,

after my last upgrade from 9.10 to 10.04, the system trys to automaticly mount the windows ntfs partition that is not there anymore. as a result i get this partly message "NTFS signature is missing Maybe the wrong device is used? or the whole disk instead of a..."

the problem is that the boot sequnce gets stuck at this point, and i found a way around, that i type my password and press enter, and it let me skip this. However it seems to come back from time to time that the password trick doesn't help. and b.t.w. when i see the splash screen it is represented as out of resulotion, like a few lines of blue dots(i have kubuntu core).

i didnt file it in the log file of dmesg, i use nvidia drivers.

anyone know what is the source of all this?

---

### Post by cariboo on 2010-07-02
You can get rid of the ntfs error message by removing the ntfs mount line from /etc/fstab.

I don't have a problem with plymouth, so I can't help you there.

---

### Post by flecktor on 2010-07-14
thank you ill try that.

---

