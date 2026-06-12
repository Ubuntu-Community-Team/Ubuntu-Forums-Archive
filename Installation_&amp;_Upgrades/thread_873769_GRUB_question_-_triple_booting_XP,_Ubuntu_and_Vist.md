---
title: "GRUB question - triple booting XP, Ubuntu and Vista"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by mrshift on 2008-07-29
Hi folks,

Currently I have XP on c:, Ubuntu on my external drive and I'd like to install my copy of Vista Ultimate on my internal e: drive.

The question is, would GRUB pick up Vista and add it to the bootloader, or would Vista try and install its own, and I lose access to one (or more) of my OS's?

Cheers,

  Andy.

---

### Post by Shazaam on 2008-07-29
Usually what happens is ANY version of Windows will re-write the mbr during install. There are several ways to work around this (and probably some that I don't know about). If you search the Ubuntu forums (especially Tutorials and Tips) you will find more information than what I can give you.

---

### Post by mrshift on 2008-07-29
Thanks Shazaam - I'd be interested to know if there's a utility that can configure your MBR/bootloader if it all goes horribly wrong. I can live happily if the installation of Vista makes me lose access to Ubuntu (as it's easy to reinstall), but this is a work machine and if I lose access to XP I'm seriously screwed.

I'd rather not risk installing Vista if it means there may be problems accessing XP.

I'll ask the same question differently. To recap, I have XP and Ubuntu installed, and I already have the correct partitioning to handle Vista. I have read in several places the best order to install these (if triple-booting) is XP, Vista, Ubuntu. If I now install Vista, would it then be straightforward enough to do a clean reinstall of Ubuntu in it's existing drive, assuming there's nothing in it I mind losing?

---

### Post by karatekid on 2008-07-29
intalling vista is most likely not to cause any troubles to your exixting XP installation.
installing vista will rewrite the MBR accordig to vista bootmanager.
the vista bootmanager automatically provides the option of booting to vista or other old windows systems.
for booting  ubuntu you can use EasyBCD to create an entry for ubuntu.

though everything should work out perfectly even if anytihing goes wrong you would not lose your XP installation but you wont be able to boot to XP
for this there are many boot manager/repair tools which can easily restore your exixting XP .
i suggest you download 
Ultimate Boot CD and burn it to  cd ,just in case something gets messed up.
also its good you keep your XP ,vista, ubuntu Cd's handy.

---

