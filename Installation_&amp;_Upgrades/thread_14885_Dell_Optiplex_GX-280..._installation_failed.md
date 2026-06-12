---
title: "Dell Optiplex GX-280... installation failed"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by jay9333 on 2005-02-10
Hey everyone.  I just installed ubuntu on my computer, and went through the auto partitioning, etc.  I got the point where I'm instructed to remove the installation media and let the computer restart.  At that point the screen showed me what ubuntu was doing/loading I suppose, and it said the following:

... 
 * Cleaning /etc/network/ifstat...
 * Starting hotplug subsystem...

(then I get three listings of the following error)
mdprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

(and I get two errors that are very similar except it says .../hotplug/pciehp.ko instead of .../hotplug/shpchp.ko)

then it continues...
 * Configuring network interfaces
 * Setting up general console font...
 * Setting the System Clock using the Hardware Clock as reference...

and at that point it just hangs.  I've let it sit for a half hour at a time and it just sits there "setting the system clock"

any ideas?  I'd love to be able to try out this distribution if possible.  Thank you.

~jay

---

### Post by orion_114 on 2005-02-10
Try using some of the boot options.
When you boot off the Ubuntu Disc and it says press enter to boot ....
Press F1 and try using some of the options there.

---

### Post by orion_114 on 2005-02-10
I checked on my disc now. There is a boot option for "Certain Dell Machines"
Try typing this at the boot promt ...
linux aic7xxx=no_probe

---

### Post by NicS on 2005-02-10
I suppose you installed warty?

I had the same problem and submitted a thread months ago, unfortunately: no response.

I manage to tweak an installation with Hoary on gx280 with an on-screen usb hub, in fact kernel 2.6.8 seemed to be the pb.

Try with Array 4 or wait a month! It's gonna work

Good luck

---

### Post by jay9333 on 2005-02-10
[QUOTE=orion_114]I checked on my disc now. There is a boot option for "Certain Dell Machines"
Try typing this at the boot promt ...
linux aic7xxx=no_probe[/QUOTE]

Tried this, this time it hung again:
error_cod+0x2d/0x38
exited with preempt_count 1

...NicS wrote "Try with Array 4 or wait a month! It's gonna work".

Where should I get this "Array 4" from?  I looked in ubuntu's download page and it wasn't there that I could see.

thanks,

---

### Post by orion_114 on 2005-02-10
I think he means this link ? I could be wrong.
[http://cdimage.ubuntulinux.org/releases/5.04/array-4/](http://cdimage.ubuntulinux.org/releases/5.04/array-4/)

---

### Post by NicS on 2005-02-11
No you're right, sorry not have mentioned the pointer before.

---

### Post by Wim Sturkenboom on 2005-02-11
> mdprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

(and I get two errors that are very similar except it says .../hotplug/pciehp.ko instead of .../hotplug/shpchp.ko)I don't think you need them. I removed them on an older Dell laptop as I also had those error messages.. To do so, edit /etc/hotplug/blacklist and add shpchp and pciehp at the end of the list.

It will probably not solve the rest of your problems.

PS I found that info this morning while following another thread.[here](http://www.ubuntuforums.org/showthread.php?t=13445&page=2).

---

