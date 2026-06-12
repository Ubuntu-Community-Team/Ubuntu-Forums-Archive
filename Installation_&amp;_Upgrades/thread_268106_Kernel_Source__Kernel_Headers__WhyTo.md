---
title: "Kernel Source?  Kernel Headers?  WhyTo"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by baustiech on 2006-09-29
I see many HOWTOs on this, that, new kernels, etc., but I've yet to find a clear explanation of why the kernel headers seem to be separated out from the kernel source.  Or, most importantly, how to get them back together again.

I've also yet to successfully recompile anything against these broken-out headers and sources.  Many smaller software "bits and pieces" expect to find unadulterated kernel source + headers, and any small change often breaks them in various time consuming ways.

Take for example the new SATA RAID2 Promise SuperTrack EX 8350 on u606 / linux 2.6.15-27 on amd64 k8, which has presently grown into a 3-day installation problem engulfing two people and is sure to burn up most of this weekend.

Don't mean to slam, but over at least one decade now, this is far from the first time I've had substantially aggravating and time-wasting bad experience with Promise Technology, which has always seemed, in my experience, to be waaay overpromised.  Sure, their stuff CAN work, and apparently does for a great many people, but I feel compelled to stress that if I had been the spec/purchaser on this project there's just no way Promise would have beaten out a 3Ware card, even if the Promise card were free and the 3ware were $1k or more.  I've never experienced even a hint of difficultly at installation with any 3ware cards; whereas, Promise has never failed to cost me pain and sometimes even resulted in being pulled from emergency-revised project specs.  Cheaper always costs more.  Alas.

We're presently trying to compile a fresh, bone-stock 2.6.18 from kernel.org (in the hope that the Promise EX8350 driver will compile properly against it), but that defeats much of the "LTS purpose of using a distro otherwise so good as u606.  We would like to stick to u606 packaged kernels, just for convenience of customer support.

Could anyone offer insight on how to get the u606 packaged kernel source + headers back together again, like it comes from kernel.org, so that lesser-quality and/or lesser-well-supported driver projects, such as the Promise SuperTrack EX 8350, can be compiled without inordinate difficulty?

TIA

---

### Post by pseudonym on 2006-09-29
Would the package linux-source-2.6.15 be what you are looking for? THis is the u606 kernel in its complete, original form. The headers packages are just there so people with the release kernel can compile 3rd party modules if need be, rather than having to download a complete source tree.

Don't ask me anything about that RAID controller, though :)

---

### Post by baustiech on 2006-09-30
Thanks for your suggestion.

The Promise EX8350 driver (apparently named shasta24.o) needs this file, which is not present in the linux-source-2.6.15 package:

/usr/src/linux-2.6.15/linux/include/version.h

That file isn't there in the packaged kernel source (2.6.15) archive that I downloaded.  However, in the .tgz from kernel.org, that file is present.

Regardless, even after I copy that version.h file (from kernel.org source tree) over into the u606-packaged kernel source tree, the Promise driver source fails to compile for various reasons.  Their Makefile appears to be self-conflicting as in it's missing sections that it requires of itself.

Wow, what a joke. Promise: "yay! wE tOo hAvE OpEn SoUrCe DRIVERS!!!!"

Oh, and the Promise site has been down since right after I posted the thread topic.

---

