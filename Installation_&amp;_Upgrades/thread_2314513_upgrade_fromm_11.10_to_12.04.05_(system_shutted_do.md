---
title: "upgrade fromm 11.10 to 12.04.05 (system shutted down, can not continue it)"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2016-02-21
Dear Fellows

  I was trying to upgrade from ubuntu from 11.10 to 12.04.5 by using update manager. Suddenly my laptop shut down due to lack of power charge. Now, when I want to continue the upgrade process  this error comes:

[PHP]Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).[/PHP]

Please Somebody help me how can I upgrade my ubuntu to 12.04.05?

  Any hints appreciated.

  Regards
   Bobi

---

### Post by Bucky Ball on 2016-02-21
Did you backup your valuable data prior to attempting this? Upgrading from an end-of-life release (and 11.10 hasn't been supported for some years) is a path fraught with danger and problems. Your best option is to clean install 12.04 if that is where you want to go, but I'd advise you go directly to 14.04 LTS and try to avoid getting into the position where you are using an unsupported release in future.

LTS releases are supported for five years, 14.04 LTS until April 2019. 

Hopefully someone may have some clues about how to get you out of this mess, but when the power dies during any release upgrade the machine is generally left in a similar state to yours.

---

### Post by howefield on 2016-02-22
You could try dropping to recovery mode by and selecting the dpkg option.

If you do not get a grub screen when booting, press and hold the shift key soon after switching the machine on.

---

### Post by babakflame on 2016-02-22
Dear Fellows
  
  Thanks a lot for your valuable comments. I solved my problem by your comments and other hints in this website.
  The problem solved by booting the recovery mode and following howefield comments.

@ Buckyball: I am upgrading to 14.04 at the moment.

  Thank you guys.
    Regards
      Bobi

---

