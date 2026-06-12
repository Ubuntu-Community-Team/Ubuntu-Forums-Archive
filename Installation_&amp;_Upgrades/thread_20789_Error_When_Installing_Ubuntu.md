---
title: "Error When Installing Ubuntu"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by kb00heda on 2005-03-18
Hi,

I'm about -- I hope(!) -- to install the preview version of Ubuntu Hoary. After the first steps of the installation, the CD pops out, and the machine reboots. However, I'm left at the GNU GRUB prompt, and if I try executing "boot" I get

Error 8: Kernel must be loaded before booting

What could be wrong, or, better, how to load the kernel and make booting possible? Couldn't find any earlier thread describing this?

It's a clean install on an SATA-drive, and the machine is a year old, with a Intel Pentium CPU (I downloaded the 386-version of Hoary).

Any help would be most appreciated!

Regards,
David

---

### Post by kb00heda on 2005-03-19
The same thing happened when I tried Warty instead. I'm left at the GRUB prompt and can't go further.

This can't be happening "by default" if one doesn't adjust the proposed partitioning? In that case more people than me ought to have had the same problem. 

I discovered a note about it in the French Ubuntu site, and it seemed to me they worked it out, but I couldn't understand how (due to my non-existing knowledge of French!).  :cry: 

/David

---

### Post by kb00heda on 2005-03-19
Hi,

I got it worked out. In the end it was all about a misconfigured boot order in the BIOS. I ruled that out -- apparently way to early without checking -- since I had a working SuSE 9.2 system before attemting the Ubuntu install. One never learns...!  #-o 

Anyhow, it was resolved, and now I'm left to configure my new Ubuntu. I hope it will be a good and lasting experience.

Regards,
David

---

