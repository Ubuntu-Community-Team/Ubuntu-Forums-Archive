---
title: "Ubuntu server 7,04 - halts at startup [...Ok, booting the kernel]"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by juveniledee on 2007-07-19
Hi,
Ubuntu newbie here, so please excuse my ignorance...

Installed ubuntu server 7.04 same error recieved at shown in the attachment.....

I've installed Ubuntu server v6 on vmworkstation 5.5.3, installation process runs thru as normal.

At reboot after the install the following startup message is received:

view attachment...

and halts......same problem when i install v7.04....

Can anyone please help me with this, thanks...

---

### Post by 5-HT on 2007-07-19
There's something going on, but you're not given any information to go on. What about either removing 'quiet' from the boot options, or adding 'verbose'? That may help spurt out some error messages to help figure out what's the cause of the hang. 

cheers,

---

### Post by juveniledee on 2007-07-19
Hi 5-HT

thnks for the quick response.... removed quiet from the command line as shown in attachement:

but still the same problem... it seems to load the kernel but hangs on the next step.
Any idea what the next step is in the sequence of execution??

also there has not been any modification to the default settings..


thanks....

---

### Post by juveniledee on 2007-07-19
sorry...wrong choice of words...it uncompressed the linux image and then freezez at the point of booting the kernel....

---

### Post by 5-HT on 2007-07-21
> **juveniledee said:**
> Hi 5-HT

thnks for the quick response.... removed quiet from the command line as shown in attachement:

but still the same problem... 
thanks....
argh...not a very descriptive error message is it? I'm not familiar at all with running Ubuntu on vmware, perhaps some searching may turn up some info.

What I can say is that acpi, apic, drive, and  possibly irq issues are usually the prime suspects in such cases, virtualized or not. If a search doesn't turn up anything, disabling (via boot options) acpi (acpi=off noacpi) or apic (noapic), or trying something like pci=biosirq might do the trick.

Attached is the complete list of kernel boot parameters available (had to zip it to get past the maximum attachment file size- it's only a text file directly from the current kernel source).
Sorry I couldn't be of more help. The issue *should* have a workaround, I'm just not aware of what it is.

Hope you get it going!

---

### Post by juveniledee on 2007-07-21
Hi,

i took the easy the way out of this one...i used the alternate cd to install and it worked like a breeze...

thanks for the parameter list...will come in handy as i muck around with it...

cheers...

---

