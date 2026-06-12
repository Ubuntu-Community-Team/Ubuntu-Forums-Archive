---
title: "But what about kernel..."
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by joshier on 2006-07-18
Hey

What about kernel 2.6.17?

Is dapper drake using this kernel?.. As currently I have to use madwifi, then ndiswrapper etc to carve my way through the wireless issue.

I don't want to fiddle around with command line, so it would be nice if dapper drake (which supports my broadcom 4306 wifi) was based on kernel 2.6.17 or higher.

Cheers.

---

### Post by matthew on 2006-07-18
It uses 2.6.15. There is an effort to backport 2.6.17 from Edgy Eft, the version of Ubuntu that is currently under development, but that is not an easy thing to do so we have no ETA nor even a guarantee that it will be able to happen.

---

### Post by joshier on 2006-07-18
How do you mean?.. are you saying ubuntu will never support 2.6.17??

I would say it's quite an important thing to impliment, I mean, it has native support for so many more hardware products.. would be silly to miss it out!

Also, why does it make it so difficult?.. I remember that I used synaptic to update my kernel when I had suse a few months back.

Also, why exactly has it taken so long for ntfs write support?.. it's really weird.

Thanks

---

### Post by avtolle on 2006-07-18
To check on kernel, go to Applcations -->Accessories-->Terminal, and enter the following: uname-r. This will give you the version of the kernel presently installed, which is not the one you are hoping for.

EDIT: someone beat me to it.

---

### Post by matthew on 2006-07-18
> **joshier said:**
> How do you mean?.. are you saying ubuntu will never support 2.6.17??

I would say it's quite an important thing to impliment, I mean, it has native support for so many more hardware products.. would be silly to miss it out!Ubuntu is already using 2.6.17 in its new version under development (Edgy Eft, to be called 6.10) scheduled to be released in October. It is going to be supported. The question is not whether Ubuntu will use 2.6.17, but whether it is possible to adapt that kernel to the current release, 6.06 codenamed Dapper Drake.
> **joshier said:**
>  Also, why does it make it so difficult?.. I remember that I used synaptic to update my kernel when I had suse a few months back.If the backport developers are able to resolve the dependency issues involved in bringing a kernel from the development version into the current release (that's the hard part) then installing it will be very easy via Synaptic. It's the first half, adapting something that requires things not currently in 6.06 for use in this release that is difficult.
> **joshier said:**
>  Also, why exactly has it taken so long for ntfs write support?.. it's really weird.Because NTFS is a closed source filesystem. People had to guess, fiddle with, and slowly reverse engineer the filesystem to get a Linux driver written. If Microsoft had wanted Linux to have access to it is would have been a quick and easy process--they would have released either a Linux driver themselves, the source code for NTFS, or at least the technical specifications necessary for the driver to be easily written. None of that happened.

---

### Post by joshier on 2006-07-18
Thanks for the quick responces, I can see why now.

Anyway, I won't be getting ubuntu until it's on the 2.6.17 version as I don't want to faff around with ndiswrapper, I done that with suse and I had to do like, 10 commands every single start-up to get it running,  and I didn't wanna mess around with any start-up scripts, and also ubuntu doesn't seem to have a hibernate feature,  unlike windows xp.

---

### Post by joshier on 2006-07-21
Hey, this is brilliant.. just noticed there's an alpha for the new kernel.. just brilliant :D

Thanks!

---

