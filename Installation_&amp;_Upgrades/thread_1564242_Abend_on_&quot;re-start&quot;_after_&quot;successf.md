---
title: "Abend on &quot;re-start&quot; after &quot;successful&quot; 10.04 Install"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by Langstracht on 2010-08-30
Well successful in that it told me so.

However, after okaying a restart, and the disc being ejected I am now looking at a frozen screen (there was more than one but they went by so fast I don't know how many) filled with the like of:

[ 1095.nnnnnn] end_request: I/O error, dev sr0, sector nnnnnn

the last of the first nnnnnn's is 865443, and of the other 505072, this being consistently repeated 3 times.

The machine is an Acer Aspire, supposedly dual boot with Win 7.

The question is "what do I do now?"

---

### Post by oldfred on 2010-08-30
I have not seen abend since greenbar paper days.

If you are still at part of the install. It seems to eject a little soon, as it still wants something from sr0. I usually hit enter and it closes and reboots.

---

### Post by Langstracht on 2010-08-31
Well hitting Enter did not do it for me. Nor did trying any other key combination I could think of.

Getting increasingly impatient with the lack of a response to my plea, I finally just killed the machine and turned it on again ... and it worked fine.

Seems I fretted needlessly, for MANY hours, thinking I had bricked, and made non-returnable, my brand new machine  ...

You live and sometimes learn!

---

### Post by oldfred on 2010-08-31
Glad it is ok. Some here are having issues, but it is pretty hard to brick a computer by just installing  software. 

We do often have to reinstall boot loaders either grub, grub2 or windows to the MBR or even chroot into a broken system from the liveCD and update it.

---

