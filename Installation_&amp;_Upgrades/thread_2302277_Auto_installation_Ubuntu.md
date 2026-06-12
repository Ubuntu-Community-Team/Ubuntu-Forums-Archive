---
title: "Auto installation Ubuntu"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by canavaroski90 on 2015-11-09
Hi guys

[COLOR=#111111][FONT=Ubuntu]I'm trying to create a complete auto installation iso which will install customized Ubuntu image.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I successfully created an auto installer image by using remastersys tool, however, it does not install grub. After installation completed (haven't rebooted, still working on live cd) I need to run Boot-Repair application to install grub properly.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My question is, how is it possible to run a script in live cd (or pen drive) after installation finished? So it can also automatically install grub.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-11-09
There are many ways of going about this. The easiest is to do a minimal install, add what you want, then make an ISO of the install. That's it. 

The info [here]("https://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/") and the links at the bottom of that page might give you some clues. You'd need to include that script in your customised install prior to creating the ISO of it.

These may help. There is [Ubuntu Customisation Kit]("http://sourceforge.net/projects/uck/").

[This]("https://help.ubuntu.com/community/LiveCDCustomization?action=show&redirect=LiveCDCustomization%2F6.06") may be relevant to you.

Are you following a guide? Is there a plan from start to finish? What are you intending to install this customised ISO on?

PS: I'm not absolutely sure I understand, though. Are you asking how you get your customised install to install grub, just like a regular Ubuntu install would?

---

### Post by canavaroski90 on 2015-11-09
Thanks for the fast reply.

Actually I'm doing a bunch installation of Ubuntu Server 14.04.03 version to hundreds of machines. We also have our own applications which must be installed on those systems. In order to do this we need to configure libraries, custom paths, configs, services etc. to make the systems run our applications. So I have 2 ways of doing this;

1- Make a clean ubuntu server installation(choosing keyboard, language settings, timezones etc). After that deploy all of our packages into a single directory and run a script which copies all files to the relevant paths and makes required configurations.

2- Create a running server (all files copied to proper paths, all services written and running, all configurations files are filled with default values and copied to proper paths). Create a snapshot of it and make an ISO file. Burn it into a bootable pen drive and make this installation "unattended". So I can make bunch of copies from this usb pen drive and all I need to install is attaching the usb and forgetting the pc.

I choose the second way. Created a "ready-to-run" image for installation and made it unattended. However, custom ISO installer does not install grub and I need to interfere the installation when the file copying is finished to install grub manually.

Btw, thanks for your suggestions. I'm going to try them today. I was following the link below.
[https://help.ubuntu.com/lts/installation-guide/i386/ch04s06.html](https://help.ubuntu.com/lts/installation-guide/i386/ch04s06.html)

Hope explained it clearly. Sorry, this is not my mother tongue.

---

### Post by mastablasta on 2015-11-09
clonezilla offers you a way to deploy images via network. I think it's this one: [http://clonezilla.org/clonezilla-SE/](http://clonezilla.org/clonezilla-SE/)

not sure what landscape does but I think it's made for multi server admin. also what about juju?

---

### Post by grahammechanical on 2015-11-09
The Disks utility will let us create an image of a disk and then restore the image. I have not tried this myself. But I have used the Restore Image function to put a Ubuntu ISO image on a USB memory stick and also to put a Canonical provided image of Ubuntu Personal (personal_x86.img) on to a hard disk.

It replicates the image complete with partition layout and Grub. So, if you are making an image of a disk that has Grub installed, then the Restore Image function should replicate the image on to whatever disk it is restored to. 

If you were running Disks from a live USB session with persistence and the "cloned" image was also on the USB stick, then you might get what you want. But I would recommend using the open source video driver and using GPT partitioning (which is not limited to UEFI motherboards) on the disk to be cloned.

Regards

---

### Post by canavaroski90 on 2015-11-13
> **mastablasta said:**
> clonezilla offers you a way to deploy images via network. I think it's this one: [http://clonezilla.org/clonezilla-SE/](http://clonezilla.org/clonezilla-SE/)

not sure what landscape does but I think it's made for multi server admin. also what about juju?

@mastablasta thanks for your suggestions. Clonezilla is what I've been looking for.

Thanks all for the answers.

---

