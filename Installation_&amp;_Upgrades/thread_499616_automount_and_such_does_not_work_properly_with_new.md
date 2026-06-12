---
title: "automount and such does not work properly with new kernel"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by theory_prof on 2007-07-12
I am using Dapper, which uses the 2.6.15-23-386. I downloaded a newer kernel
and compiled and installed it. The new kernel is 2.6.20.3. (I chose this kernel for 
a specific reason, as it allowed me to apply a certain patch only available to that kernel.)

Now, everything looks fine when I boot into the new kernel, but automount does not work 
properly anymore. Also other things like my PCMCIA modem card is not seen any longer. 
I looked at the device manager and under the old and new kernel what is reported is 
completely different. I have attached screen shots. In short, under the new kernel the
machine looks as if it does not any hardware. 

Any suggestions?

---

### Post by HermanAB on 2007-07-12
Automount works very well when it works...

The solution is to learn how to manually mount stuff.  It is typically something like:
$ sudo mkdir -p /mnt/cdrom
$ sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
$ sudo umount -l /dev/cdrom

Cheers,

Herman

---

### Post by theory_prof on 2007-07-14
Thanks, but of course, I know how to do that. Is there any way that the new kernel will recognize my hardware like before?

---

### Post by theory_prof on 2007-07-14
As a tangent:

I wouldbe curious how to get my (hardware) PCMCIA modem back to work...

No, no I do not connect through it to the Internet, but it's nice to fax people....

---

