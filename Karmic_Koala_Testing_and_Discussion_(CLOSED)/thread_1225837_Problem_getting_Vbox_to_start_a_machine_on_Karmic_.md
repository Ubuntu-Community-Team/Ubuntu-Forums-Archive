---
title: "Problem getting Vbox to start a machine on Karmic host..."
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-07-29
I installed Vbox-OSE from the repos tonight and moved a couple of machines and disks from a previous install on F11.  When I power up the machine, I get an error about the kernel module not being there, yet I know I installed the Vbox-source.  Even if I make a new machine, when I go to start it I get the same error.  Am I missing something?

The host is an up-to-date Alpha 3 install...

---

### Post by dinxter on 2009-07-29
try looking at 
$ dkms status
and 
$dmesg|grep vbox

dkms should show the modules as (installed) and 
dmesg should show any problems loading them. note though some of us are having a few problems with nmi but 3 from the repositories does work... most of the time
 [http://ubuntuforums.org/showthread.php?t=1209319](http://ubuntuforums.org/showthread.php?t=1209319)

---

### Post by neferty on 2009-07-29
you can try this: [http://ubuntuforums.org/showpost.php?p=7651917&postcount=22](http://ubuntuforums.org/showpost.php?p=7651917&postcount=22)
which has worked for me. After the *4 kernel upgrade my problem seems to have disappeared completely

---

### Post by mariner09 on 2009-07-29
That's the odd thing.  I tried the nmi_watchdog=0 and that didn't matter.

I also wanted to try the vboxdrv command, but it doesn't exist on my system.

dkms_autoinstaller log:

vboxdrv (3.0.2): Already installed on this kernel.
vboxnetadp (3.0.2): Already installed on this kernel.
vboxnetflt (3.0.2): Already installed on this kernel.
virtualbox-ose-guest (3.0.2): Already installed on this kernel.

dmesg:

[   12.540320] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   12.540323] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[   12.540324] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

I'm at a loss, because this didn't happen on F11, it was all so automatic...

---

### Post by mariner09 on 2009-07-30
What I found is that for some reason, vboxdrv was not being loaded.  I added this to /etc/modules and hopefully, when I reboot it'll all just work...

---

### Post by Buffalo Soldier on 2009-07-30
did you manage to get it working?

---

### Post by xebian on 2009-07-31
Have you added yourself to the 'vboxusers' group?

The Vbox debs from VirtualBox.org are better than those from the repo. USB support for one.

---

### Post by mariner09 on 2009-07-31
Adding vboxdrv to /etc/modules did not work and I am a member of vboxusers.

I'm getting the nmi_watchdog error at boot-up when the vboxdrv module is trying to load, but I can load it manually afterwards.

I may have to grab the packages from the virtualbox site and try them.

---

