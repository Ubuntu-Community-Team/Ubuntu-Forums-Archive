---
title: "Multiple Boot Options"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by DiGiTaLFX on 2005-05-30
Hi. I've moved to Ubuntu after being a dedicated Red Hat fan, and am a bit confused about GRUB. With rh/fedora there would just be one entry in grub for the OS. Now I've installed this and I've got 5 entries plus a dead entry. Why?

Could someone explain to me the difference between the Default entry and the non default entry. I know about memtest, so its handy to have that there. And what is recovery mode? What does it do etc? Basically I'm interested in editing the list down to just 3 entries - Ubuntu, memtest and Windows.

Also, if I install the K8 kernel (thats the correct one for an Athlon 64 isn't it? - i'm on amd64 generic at the moment), what do i do to remove the generic kernel - presumably just remove a few packages with synaptic?
Thanks very much

DiGiTaLFX

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=DiGiTaLFX]Hi. I've moved to Ubuntu after being a dedicated Red Hat fan, and am a bit confused about GRUB. With rh/fedora there would just be one entry in grub for the OS. Now I've installed this and I've got 5 entries plus a dead entry. Why?

Could someone explain to me the difference between the Default entry and the non default entry. I know about memtest, so its handy to have that there. And what is recovery mode? What does it do etc? Basically I'm interested in editing the list down to just 3 entries - Ubuntu, memtest and Windows.

Also, if I install the K8 kernel (thats the correct one for an Athlon 64 isn't it? - i'm on amd64 generic at the moment), what do i do to remove the generic kernel - presumably just remove a few packages with synaptic?
Thanks very much

DiGiTaLFX[/QUOTE]
 After you tested that the kernel works fine with all your harware, you can safely remove "recovery" listing. At least, I always do (and also edit the name to somehting more humanly readable).

---

### Post by mingus on 2005-05-31
[QUOTE=DiGiTaLFX]Hi. I've moved to Ubuntu after being a dedicated Red Hat fan, and am a bit confused about GRUB. With rh/fedora there would just be one entry in grub for the OS. Now I've installed this and I've got 5 entries plus a dead entry. Why?

Could someone explain to me the difference between the Default entry and the non default entry. I know about memtest, so its handy to have that there. And what is recovery mode? What does it do etc? Basically I'm interested in editing the list down to just 3 entries - Ubuntu, memtest and Windows.

Also, if I install the K8 kernel (thats the correct one for an Athlon 64 isn't it? - i'm on amd64 generic at the moment), what do i do to remove the generic kernel - presumably just remove a few packages with synaptic?
Thanks very much

DiGiTaLFX[/QUOTE]
 [I]Debian automatically generates the menu.lst control file, unlike other distros.  It seeks to detect other installations for multi-boot, adds a recovery entry for Ubuntu and the common memtest.  Read the file and you'll see user-defined data points, e.g., #kopt= where any kernel arguments you add will be placed in the default section below after you run update-grub.

You can bypass this feature and manually modify the file and run grub-install if you wish.  This is sometimes necessary if Debian failed to find another installation, or how it loads differently, e.g., you want to use chain loader and it didn't.

The default entry is simply the first boot choice in the list and after the defined timeout will be what grub automatically boots into.  You can change the time.

Recovery Mode is just the same as the default except that kernel arguments may be removed or added to simplify kernel loading.  Sort of like Windows Safe Mode, however Windows loads many fewer drivers than this Linux option.  E.g., common to turn acpi or apic or framebuffer off.  I've noticed this Debian generated file doesn't do hardly as much with this as other distros like SuSE.  You can do exactly the same thing with the default choice by simply changing the arguments while in the grub menu.

Re 64, sorry, can't help with this one.[/I]

---

### Post by DiGiTaLFX on 2005-07-20
Thanks very much. Long time since I've replied, but I killed Ubuntu until now where I've decided to make it my main OS. Anyway its much clearer now about these. Only thing is that by default entry I meant that i see something like

kernel Default
kernel recovery Default
kernel
kernel recovery

What are these top two entries with the word Default attached to them? How do they differ in functionality to the ones without the word default?

Cheers

DiGiTaLFX

---

