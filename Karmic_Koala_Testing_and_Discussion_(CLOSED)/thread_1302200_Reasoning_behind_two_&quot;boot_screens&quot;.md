---
title: "Reasoning behind two &quot;boot screens&quot;?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-10-26
When you typically boot into Karmic, you are greeted with the following:

BIOS
GRUB
Ubuntu Logo
xsplash
GDM

Having the Ubuntu Logo and the xsplash, instead of just one boot screen seems a bit unnecessary? From a typical user point of view, it would appear that Karmic takes longer than Jaunty to go from GRUB > GDM because of two splash screens instead of one such in previous releases. A user might expect the login window to show after the first appearance of the logo, but instead have to wait for another splash screen after the logo fades out.

What's the reasoning behind this? Is the logo to hide all the verbose messages and make it look prettier?

---

### Post by Mr. Picklesworth on 2009-10-26
> **humphreybc said:**
> When you typically boot into Karmic, you are greeted with the following:

BIOS
GRUB
Ubuntu Logo
xsplash
GDM

Having the Ubuntu Logo and the xsplash, instead of just one boot screen seems a bit unnecessary? From a typical user point of view, it would appear that Karmic takes longer than Jaunty to go from GRUB > GDM because of two splash screens instead of one such in previous releases. A user might expect the login window to show after the first appearance of the logo, but instead have to wait for another splash screen after the logo fades out.

What's the reasoning behind this? Is the logo to hide all the verbose messages and make it look prettier?

The logo is the old usplash. That's exactly its purpose, with the benefit that it also makes fschk and the like much more presentable.

X now kicks in a bit earlier, replacing usplash. It is there until X loads, so everything that X needs to function is loaded while this first splash is up.
The second full screen splash is running on the X server while the other necessary resources load. It's the same splash (and the same X server) between GDM and your desktop.

---

### Post by RAOF on 2009-10-26
The goal is to eventually only load usplash in exceptional circumstances: when fsck kicks in, or when you need to enter a passphrase for your encrypted partition before X can start.

My understanding is that usplash is currently unconditionally enabled because the boot process isn't yet quite fast enough to skip straight to X.  As I understand it, a Lucid goal is to have boot fast enough to not use usplash in the common case (and thus speed boot up a bit more :)).

---

### Post by humphreybc on 2009-10-26
> **RAOF said:**
> The goal is to eventually only load usplash in exceptional circumstances: when fsck kicks in, or when you need to enter a passphrase for your encrypted partition before X can start.

My understanding is that usplash is currently unconditionally enabled because the boot process isn't yet quite fast enough to skip straight to X.  As I understand it, a Lucid goal is to have boot fast enough to not use usplash in the common case (and thus speed boot up a bit more :)).

Ahh, gotcha. That makes sense.

Thanks guys!

---

