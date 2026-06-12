---
title: "Installer hangs on VAIO PCG-C1MV (old laptop)"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by japc126 on 2008-02-23
I'm trying to install ubuntu to this old laptop, but I get a problem.

In the cd boot screen, I select the option to install ubuntu/ run it from live cd. Then, ubuntu starts to load, the little bar going back and forth. But while the screen is there, it dissapears, and a black screen with a comand line appers. it says something or other "busybox". What do I do? (got the same problem after trying kubuntu and xubuntu live cds)

(I'm sorry if I sound like a moron, but english isn't my native lenguage and I'm trying to be as descriptive as possible)

---

### Post by CRCarl on 2008-02-24
So FYI, good error messages help, 

> it says something or other "busybox". 

is really funny but not helpful. I would suggest you start by downloading the text installer .iso and using that to install with, if you still get an error, start a new thread with some new details.

---

### Post by japc126 on 2008-02-24
Do you mind giving me a link to download the text installer? I cant find it

Edit: nvm, it's the alternate cd

---

### Post by pablolie on 2008-05-16
I am having the same issue - I owuld love to install Ubuntu 8.04 on a Sony PCG-C1MV Picturebook, it would impress a lot of people in my environment, and I am a huge fan of Ubuntu as it runs on my "home server" and I love to use it.

But the installation of both 8.04 and 7.10 fails miserably on this computer, always goes into the dreaded
initramfs
sequence, not saying anything about what went wrong. It just gets stuck. I have tried a lot of different installation options. The F6 option gives me
acpi=off
noapic
nolapic
edd=on
Free software only
as clickable options. I have tried them all at once and in different configurations, no luck. The exact same same sequence happens, namely
ubuntu logo with loading bar back and forth
(initramfs)

and that's that.

The BIOS options for this little Transmeta Crusoe powered box are very simple and auto-discovery.

I have searched high and low and can't find help. Anyone? I'll pay! I really want this to work.

---

### Post by EXCiD3 on 2008-05-18
Have you tried the "all_generic_ide" boot option? it sometimes fixes the initramfs problem (but there are multiple causes for that) but its worth a shot.

---

