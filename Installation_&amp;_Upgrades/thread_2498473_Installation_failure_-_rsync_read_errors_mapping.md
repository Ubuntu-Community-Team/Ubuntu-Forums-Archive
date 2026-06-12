---
title: "Installation failure - rsync read errors mapping"
date: 2024-06-15
forum: Installation &amp; Upgrades
---

### Post by nicmol76 on 2024-06-15
Hi.

Installation of Ubuntu 22.04 RTL on local SSD fully cleaned formated, health checked, laptop HP pro Book G4 using the USB stick is failling at:

Jun 14 18:14:30 ubuntu subiquity_log.5671[9075]: rsync: [sender] read errors mapping "/tmp/ tmpszpdh1cz/mount/var/lib/snapd/seed/snaps/gnome-42-2204_176.snap": Input/output error (5)

Iso checksum once download had been checked, then flashed using Rufus and Belena Etcher (twice, in case) without any reported error so the tick seems good health.
 
But it's a 8Go one ! And I just had read the instructions that advise 12Go !!?  I mean &#129300; seriously ? Could it be the problem ? Why so much when 4Go stick is enough for Mint or Majaro...I hope it's not the real problem.

Currently I can't afford a new one but fortunately my pc has an internal secondary HD. Since Ubuntu Live works consistently using the bootable USB, 
could anyone explain me how to create on the SSD a bootable 12Go "rescue" drive into which I will copy the ISO, that will mimic the purpose of the USB Stick just for the installation (and in case of complete recovery)  ?

Thanks

---

### Post by TheFu on 2024-06-15
What is "8Go",  "4Go" and  "12Go"?  I don't know those terms.

Any normal Ubuntu Live boot ISO can be used as a rescue OS. Just use the same release you have installed, but don't worry about the DE included.  Lighter versions should be smaller and faster, but have the core tools needed to address most issues.

---

### Post by ActionParsnip on 2024-06-15
> **TheFu said:**
> What is "8Go",  "4Go" and  "12Go"?  I don't know those terms.

Any normal Ubuntu Live boot ISO can be used as a rescue OS. Just use the same release you have installed, but don't worry about the DE included.  Lighter versions should be smaller and faster, but have the core tools needed to address most issues.

Go is gigaoctet
https://rpgwatch.com/forum/threads/gb-go.6152/

---

### Post by him610 on 2024-06-16
gigaoctet
> gigaoctet m (plural gigaoctets). (computing) gigabyte synonym &#9651;. Synonym: (abbreviation) Go. Coordinate terms.

> What is the difference between go and gb?
So go=gb because gigaoctet=gigabyte. Until today I did not know this because I had never heard of the gigaoctet. It makes sense, eight bits to a byte, so why not call it an octet?

I had never heard of it either until I saw TheFu questioning it.

One of the guidelines of writing etiquette that we had in one organization where I worked was that if a new term or acronym was to be used, it would be defined at first use like this, *gigaoctet (Go)*. It would also be listed in an appendix to the document.

---

