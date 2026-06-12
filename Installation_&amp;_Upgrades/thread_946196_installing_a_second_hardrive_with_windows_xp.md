---
title: "installing a second hardrive with windows xp"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by krysia on 2008-10-13
I want to install my old 14gig.hd.to my computer running 
ubuntu 8.04 and need advice on how to do this.

---

### Post by cidhus on 2008-10-13
Install to the second hard drive. Use manual partitioning to partition the second drive and keep Ubuntu away from the first. As a minimum, you'll want a swap and a Linux partition.

As for the boot loader, I'd put it on the second drive and chainload(hd0,0)+1 to XP, and use setup to tell the computer to boot from the second drive. At least until I had both working. That way, I could use setup to switch back to booting from the first drive if the install was broken. If you are familiar with the NT Loader in XP, you could add your new O/S and boot directly from the first drive.

This is a difficult question because the answer depends more on your personal tastes than it does on Ubuntu. Linux is difficult because it doesn't make choices for you. Once you become confident in your choices, Linux loses its difficulty and becomes refreshingly liberating. Read the faqs and search the forums for similar questions to see how others went about it. "Dual boot XP" might be a useful search term.

Herb Coburn

---

