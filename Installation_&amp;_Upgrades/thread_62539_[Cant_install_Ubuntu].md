---
title: "[Cant install Ubuntu]"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by marcosglas on 2005-09-05
During Ubuntu 5.04 installation I get the following errors:

FATAL: Error inserting fan (/lib/modules/2.6.10-5-386/kernel/drivers/acpi/fan.ko): no such device.
FATAL: Error inserting thermal (/lib/modules/2.6.10-5-386/kernel/drivers/acpi/thermal.ko): no such device.
Starting system log daemon:syslogd, klogd

The installation locks there until the display gets blank.
Is there any way to avoid detecting those devices?

I'm a Linux newbie, so I need "step by step" instructions.

Thanks in advance.

MARCOS

---

### Post by felix.rommel on 2005-09-05
Boot with your Ubuntu CD. Then when the boot screen appears:

Add the following to the boot prompt:

acpi=off

And press RETURN.

As far as I can remember you get help with F2 and F3.

---

### Post by marcosglas on 2005-09-05
Ok. Thanks.
I'll try doing that.

Thanks a lot.

Marcos.

---

### Post by marcosglas on 2005-09-06
NO. It didnt work.
I need HELP!!!! please!

Thanks in advance (again).

---

### Post by felix.rommel on 2005-09-15
What PC do you have? A laptop?

Maybe there is a problem with your graphic card cause your screen gets black. You should add another option so that it looks like:

linux vga=771 acpi=off

Another Option is to download Breezy Badger RC 1 which is the precessor of Hoary but  IS NOT stable enough at the moment for a production environment.

But for private use you can download the ISO cd image and try to boot with it and install it. The final release will be available in October and then you can update easy to the final release with the update manager without installing it again.

---

### Post by marcosglas on 2005-09-15
Actually I could install Ubuntu, at least partially. The problem jis that it took TOO much, at least 12 hours to get to the part where the system is restarted. Then it should finish installing components, but after some minutes it gets stucked.
I'm installing it in a Desktop PC --> processor: Cyrix M II - 300 --> 160 MB RAM --> HDD: 3 GB.

---

### Post by felix.rommel on 2005-09-20
Sorry, I wondered why I didn't get any e-mails for this thread but I haven't subscriped to it ;)

Did you try it with Breezy RC1 or Hoary?

I cannot say anything about your hardware - for that you have to post more informations. Maybe there is some broken hardware!? Windows does work on broken hardware - which is bad - but Linux does not work on it - which is good.

Another option is to wait till Breezy final is out next month - at the moment there are still some problems which have to be ironed out - I know what I'm talking about, I upgraded to a beta version on my working machine which I will never do again ;)

In the meanwhile you can try SUSE LINUX:

[http://www.opensuse.org](http://www.opensuse.org) 

There you can download the stable version 9.3 or the release candidate of 10.

---

