---
title: "[SOLVED] iBook G4 - Superdrive mounting for live CD"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Thorney on 2008-09-14
So I bought my first laptop today - it's second hand and it appears the hard drive is foobar. to do some diagnostics I wanted to run a live CD, so I downloaded Ubuntu for PPC (intrepid-alternate).

I am at the "Detect and mount CD-ROM" stage of the install, looking at /dev I cannot see anything that jumps out saying I am a super drive...
Obviously since the terminal and installer are running from the CD I can assume its going to work, right?

So does anyone know either what the device will be called or more likely - how can I find out?

fdisk isn't present either...

Thanks!

---

### Post by Thorney on 2008-09-14
from looking through /var/log/syslog
hdc is a MATSHITADVD... CD/DVD-ROM drive
But then in /dev/ there is no hdc....

---

### Post by pxwpxw on 2008-09-14
if you run the ubuntu cd in rescue mode and let it get set up, then drop to a console
(ctrl alt F2) you will find it on /cdrom.

---

### Post by Thorney on 2008-09-14
> **pxwpxw said:**
> if you run the ubuntu cd in rescue mode and let it get set up, then drop to a console
(ctrl alt F2) you will find it on /cdrom.

Thanks for the reply - unfortunately that didn't quite work as you said.
There is a /cdrom directory - but I don't think that is the device file, its empty in any case.
I tried in the installer to manually set it too /cdrom but the error message in the log under terminal 4 says:
```
(process:2861): mount: mounting /cdrom on /cdrom failed: Block device required
WARNING **: Configuring `cdrom-detect` failed with error code 1
```


If busybox is using the cd drive why can't ubuntu? Is there a way to see how busybox is using it?

looking through /bin and trying commands that sound useful yields not much:
[LIST]
[*]list-devices cd - also blank output
[*]cdrom-checker - outputs commands like "INPUT critical cdrom-checker/start"
[*]discover-mac-io doesn't output anything, probly not using it right tho.. 
[/LIST]


Any other ideas?

---

### Post by pxwpxw on 2008-09-14
Well I have it here on an iBook g4, using the server cd in rescue mode and it is showing me the cd on /cdrom in the rescue shell, and listing the files on the cd, also in mount. I am not using busybox, you have to use rescue mode and let it proceed right thru to the select rescue root stage, where you drop to a console instead.

---

### Post by Thorney on 2008-09-14
> **pxwpxw said:**
> Well I have it here on an iBook g4, using the server cd in rescue mode and it is showing me the cd on /cdrom in the rescue shell, and listing the files on the cd, also in mount. I am not using busybox, you have to use rescue mode and let it proceed right thru to the select rescue root stage, where you drop to a console instead.

Hmm I am not using a server cd but that shouldn't matter.
I have tried images: install, install-powerpc, rescue, rescue-powerpc and check... all getting to the same point - "No common CD-ROM drive was detected." I am sure that if it was detected it would be automatically mounted into /cdrom like it has on your machine pxwpxw . (Thanks very much for checking that by the way)
It then asks load drivers from floppy? - dont have one so say no...
asks if I wish to manually select a cd-rom module and device.
If I say no -> Red screen - Installation step failed: Detect and Mount CD-ROM
If I say yes it asks if I want to start PC card services, i just clicked yes.

Then asks what module to use (none or _cdrom_)
it then wants the device file for accessing the cd-rom: default is /dev/cdrom
at this point when I go to another terminal ```
~ # cd /cdrom
/cdrom # ls
/cdrom #
/cdrom # cd /dev
/dev # ls c*
console        cpu_dma_latency
/dev # ls m*
mem
/dev # df -h
Filesystem    1k-blocks     used     Available     Use%    Mounted on
tmpfs          386512         24        368488       0%          /dev

```

I'll download ubuntu 6.10 just to remove the chance that the problem is in the pre-alpha iso of intrepid.

---

### Post by pxwpxw on 2008-09-14
Ok I see what you mean, very likely an intrepid alpha bug.
804 is ok here. and I was using 704 above.

busybox just runs on the rescue kernel/initrd loaded at boot, doesn't need the cd mounted.

---

