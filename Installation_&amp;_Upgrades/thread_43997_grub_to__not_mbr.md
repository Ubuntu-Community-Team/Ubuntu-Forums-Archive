---
title: "grub to / not mbr???"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by boutros on 2005-06-24
hello,

i installed ubuntu on my laptop last night and it toasted my mbr. no choice even to install to root. Thtat has caused alot of wasted time restoring everything. I would love to try out ubuntu but if grub auto installs to mbr and there is no choice otherwise that is no good for me.

is there away to choose grub install to root of partition instead of mbr.

thanks for info,
boutros

---

### Post by Xian on 2005-06-24
[QUOTE=boutros]is there away to choose grub install to root of partition instead of mbr.[/QUOTE]
During the installation the CD should present a screen to you asking where you would like to place the bootloader. It will give you two options: the MBR and somewhere else (defined by you). You then have a place to input where on your system you would like to install grub. The correct answer would be to pass to the installer the location of the root partition (or /boot partition if you created one). So, if your root directory is located at hda3, then you would just reply /dev/hda3.

If it did not give you this option then you have a broken installer.

---

### Post by boutros on 2005-06-24
hello Xian,

thanks for the info. I wasn't presented with the option so i am now downloading a new iso. And i will give it a try. Thanks again for your response, and have a blessed weekend.

peace,
boutros

---

### Post by Xian on 2005-06-24
If for any reason you still have a problem pass the 'expert' command to the initial boot prompt on the InstallCD and that should all but force it to appear. The reason you wouldn't want to go this route by default is that the expert mode also presents you with choices that are pre-configured in the normal routine.

---

### Post by boutros on 2005-06-25
tring the expert installnow. Did an install from a new disk and same thing. Grub just takes over and ruins my boot setup. Thanks goodness with bootit i was able to recover my w2kpro partition, make it active and re-install bootit and i am back in business. Hopefully the expert install will work.

peace,
Boutros

---

### Post by boutros on 2005-06-25
hey there,

all i got was erros for grub and lilo install attempts to hda1. see new post.

thanks alot,
boutros

---

### Post by Xian on 2005-06-25
[QUOTE=boutros]all i got was erros for grub and lilo install attempts to hda1. see new post.[/QUOTE]
Yeah, I get that too alot. You generally just have to let the installer make a second pass that that grub install and it will go in just fine. Go to the installer menu and select to install grub (bootloader) once more. Do the same process and direct it to your root partition. It will usually work then.

Keep in mind you don't need to even install the bootloader since you won't be using it to access Ubuntu. If you just skipped that step or aborted after it failed you would be just fine. It is not necessary.

---

### Post by boutros on 2005-06-25
thanks again Xian,

i may try that. As for not installing grub or lilo i am not sure that wil work for me. I use bootitng to access the parition that either XP/2Kpro or linux is on but still need the bootloader to load linux.

but i could probably manually install grub to / if needed. I may read up on that and try it when i have the time..

thanks so much again.
boutros

---

### Post by Xian on 2005-06-25
[QUOTE=boutros]As for not installing grub or lilo i am not sure that wil work for me. I use bootitng to access the parition that either XP/2Kpro or linux is on but still need the bootloader to load linux.[/QUOTE]
I'm not familiar with your exact boot scheme so I coulndn't comment specifically. But for instance I use another Linux distro (Debian) to boot my other GNU partitions, which would include Ubuntu, and I can boot all of them without any corresponding loader installed, just so long as I just keep Debian's grub installed on the MBR. If I were to reinstall Ubuntu I could skip the bootloader step and it would not impact my ability to boot after installation, as that is taking place from another partition and a separate grub configuration.

---

