---
title: "Trying to install edgy.. &quot;no root filesystem&quot;"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by supergrapeman on 2006-10-26
Hello all,

I've just downloaded the edgy iso. It's a step backward for me compared to dapper (where my wireless card and nvidia graphics cards were autodetected)..

Nevertheless, I thought I'd try installing over my existing upgraded (dapper to edgy) install.

Using the install tool, I get as far as "prepare mount points", where I get stuck. The installer thing keeps complaining "no root file system". Huh? I'm trying to define that the root file system is at /dev/hda7 (see the attached screendump). 

](*,) 

Grrrr - what am I missing? Please don't let me know that this is yet another edgy bug..

---

### Post by ghosthead123 on 2006-10-26
I have got the same problem :confused: 
Koud someone help please?

---

### Post by opticyclic on 2006-10-26
I'm not sure, but I think this means that the partition needs to be marked as root in the file table.
Aren't there flags that you can set?

---

### Post by shinythings on 2006-10-26
I had the same problem when doing a clean install over an existing dapper install. I solved it by going back to the gp-parted overview, deleting the partition I wanted to install on and creating a new one. It was automatically selected and there were no more complaints.

---

### Post by Rackerz on 2006-10-26
I had the same problem, run gParted format the partition you want as the root file system and try again, you might have to reboot before doing so.

---

### Post by supergrapeman on 2006-10-27
> **Rackerz said:**
> I had the same problem, run gParted format the partition you want as the root file system and try again, you might have to reboot before doing so.

Cool, thanks for the pointer/ workround, I will give this a whirl.

Why on earth would re-formatting it to ext3 (it's already ext3) fix this? 

Maybe this is worth filing as a bug? I guess most people won't be affected, as if they are upgrading they will just use apt or synaptic, and if they are installing fresh, they won't be trying to install over an existing ext3 filesystem.

---

