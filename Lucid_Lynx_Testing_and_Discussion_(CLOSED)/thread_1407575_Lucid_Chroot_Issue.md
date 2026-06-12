---
title: "Lucid Chroot Issue"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaxxstorm on 2010-02-15
I'm trying to build a custom Live CD from a chroot using Lucid.

Im using a Lucid Host system and booting the image in virtual box

I've followed the instructions from [here]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch") to the absolute letter, and the ISO never boots in virtual box. It loads the kernel and initrd.gz then just freezes.

Is there anything I can do, I'm tearing my hair out here!

---

### Post by Ibidem on 2010-02-15
Anyone done this successfully?
I'm not sure if the latest Lucid kernel will boot in VirtualBox.  I know alpha2 mini.iso has trouble, but alpha1 did work.
Try removing the "quiet splash" option; that shouldn't actually solve it, but you'll see where it's freezing.
Then post the last few lines in the boot output.
Other ways to test: try using qemu-kvm or vmware to test if it boots, or try on a real CD/on a flash drive with unetbootin.

I wish you the best of luck building Spri from Lucid!
I'm willing to test it; I've been using a similar system myself.
A little request- would you be willing to build a metapackage for icewm+xinit/xorg+a file manager+(the other stuff you put in Spri)?  That would simplify install without having a premade CD.

Ibidem

---

### Post by jaxxstorm on 2010-02-15
> **Ibidem said:**
> Anyone done this successfully?
I'm not sure if the latest Lucid kernel will boot in VirtualBox.  I know alpha2 mini.iso has trouble, but alpha1 did work.
Try removing the "quiet splash" option; that shouldn't actually solve it, but you'll see where it's freezing.
Then post the last few lines in the boot output.
Other ways to test: try using qemu-kvm or vmware to test if it boots, or try on a real CD/on a flash drive with unetbootin.

I wish you the best of luck building Spri from Lucid!
I'm willing to test it; I've been using a similar system myself.
A little request- would you be willing to build a metapackage for icewm+xinit/xorg+a file manager+(the other stuff you put in Spri)?  That would simplify install without having a premade CD.

Ibidem

The problem seems to be with VirtualBox rather than my particular chroot build. It boots fine in QEMU

I'm actually moving from IceWM to JWM, if it interests you. There will be a repo and metapackage available from sprilinux.com like there was for the old builds.

---

### Post by Ibidem on 2010-02-15
Glad to here that it's just VirtualBox.
I started on IceWM, and tend to prefer it (I have used Puppy, but it struck me as fast but not quite ready).
Also, IceWM has some stuff written for it like the Icewm Control Center (takes a little work, but worth it) and MenuMaker, 
A metapackage that depends on (jwm | icewm) might be nice, though.

---

