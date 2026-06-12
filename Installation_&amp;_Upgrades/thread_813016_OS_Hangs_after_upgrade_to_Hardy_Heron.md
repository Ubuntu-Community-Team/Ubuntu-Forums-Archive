---
title: "OS Hangs after upgrade to Hardy Heron"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by snegoviK on 2008-05-30
Hi all!

My installation of Kubuntu was running brilliantly, everything was working as expected. Just a few weeks ago I decided to upgrade (apt kept on telling me to). I decide to give it a try and unfortunately it seems it ruined things.

For some reason system unexpectedly hangs from time to time when I run the system with kernel version 2.6.22-16/7-generic. The system doesn't crash if I run it with 2.6.22-14 but it periodically lags (things freeze for a split second and then come back to life). When I say system hang, I mean everything dies, so keyboard and mouse do not respond and the only way to cure the problem is to make a hard reset.

I am practically a noob at Linux administration so I am not very sure how to diagnose such problems. To me it seems its a hardware/driver issue and since I  use a laptop it might be the devilish ACPI.

After running grep error /var/log/*, this message popped up a couple of times:

```

messages.0:May 23 15:50:57 snegolinux kernel: [7.808985] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

```

I did read the article about this and I did try extracting DSDT from BIOS to see what's it like. There was a minor warning (not all control paths return a value) and I easily fixed it but unfortunately sticking fixed DSDT.aml didn't solve anything so my guess is that it's not the problem.

Anyway, I am pretty much clueless and I am actually thinking of downgrading back to Gutsy.

If anyone had similar problems or can guide me through any further diagnoses, which could shed some light on what's going on, I will appreciate your help.

UPDT: Just booted up as *-17 kernel and ran grep again. Got a few extra messages:

```

sneg@snegolinux:~$ egrep ".*May 30.*error" /var/log/*
/var/log/kern.log:May 30 16:44:38 snegolinux kernel: [4.272000] usb 1-1: device not accepting address 2, error -71
/var/log/kern.log:May 30 18:08:57 snegolinux kernel: [13.700838] usb 1-1: device not accepting address 2, error -71
/var/log/syslog:May 30 18:08:57 snegolinux kernel: [13.700838] usb 1-1: device not accepting address 2, error -71
/var/log/syslog.0:May 30 16:44:38 snegolinux kernel: [4.272000] usb 1-1: device not accepting address 2, error -71

```

Any ideas? :)

sneg

---

### Post by paulphillips on 2008-05-31
Haven't experienced problem, but I thought Hardy was using a 2.6.24 kernel?  Am I wrong?  Does that possibly mean that your upgrade was only partially implemented?

---

### Post by snegoviK on 2008-05-31
I am sorry, I listed the wrong versions. System hangs when using:

2.6.24-16 and 2.6.24-17, system doesn't hang when booting with 2.6.22-14.

---

### Post by snegoviK on 2008-06-02
Bump. Still looking for help regarding this issue...

Is reinstall the only option for me?

---

