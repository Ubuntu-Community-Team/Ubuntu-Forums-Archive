---
title: "upgrade ubuntu 20.04 beta to final"
date: 2020-01-19
forum: Installation &amp; Upgrades
---

### Post by swebh on 2020-01-19
If I upgrade from beta to final will that cause problems with a windows 10 installation I have on a seperate drive? I don't want to have to repair the windows installation or boot through grub to windows.

b/g:
On this system I currently have windows 10 on an sm951 drive playing nicely with Ubuntu 18.04 on a sata ssd. (Don't think the rest of the system is really relevant here, happy to supply details if actually needed.)

I have to do some major disassembly of this PC soon (before 20.04 final release). As this will give me easy access to remove the sm951 drive I'm considering installing Ubuntu 20.04 beta on the ssd (while the sm951 drive is removed) and subsequently upgrading that to final (I don't mind that the beta is unstable for a short while, I'll be using a different system for production anyway).
(Just tot state what's probably obvious - removing the sm951 drive is a pain, it's under the gpu and some heatsinks.)

As I installed each system with only one drive connected, they both play together nicely, I can boot from uefi to windows without going through grub, upgrades etc for each system are very easy.

What I really want to know is: would upgrading from ubuntu beta to final be like installing ubuntu with the windows drive connected (so that I have an unhappy windows system, mess to fix up), or like a normal upgrade (ubuntu leaves windows alone and both systems continue to play nicely)?

Thanks very much

---

### Post by SeijiSensei on 2020-01-19
If you install 20.04 in the space that 18.04 occupies now, you should be fine. Kubuntu 20.04 has been pretty stable for me so far.

I'd probably just go for a fresh installation rather than upgrading from 18.04 to 19.04 to 19.10 to 20.04, which i believe is the required path.

If you have free space available, I'd install 20.04 there and leave the 18.04 installation untouched. If something goes wrong you could then revert to 18.04 from the grub menu.

---

### Post by Impavidus on 2020-01-20
Nothing special happens when a release goes final. They will stop pushing new features some weeks before that and will continue pushing bugfixes for long after that, all of which get installed through your regular upgrade routines. They just make an announcement and branch off a new development version. The large number of upgrades and bugs before final release may leave some cruft, which may be a reason to fresh install anyway.

BTW, even having the Windows drive attached while installing Ubuntu won't damage Windows as long as you select the right partitions to install it to, but it may put the boot loader in the EFI partition of the Windows drive.

---

### Post by swebh on 2020-01-21
hmmm, okay thanks everyone.
Sounds like one day I need to learn the art of installing Ubuntu without messing up my EFI partion (or whatever it is that generally happens -> problems).
Until then, I'll just keep installing with only one drive connected.

---

