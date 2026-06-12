---
title: "How to sign Kernel"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2014-04-05
Environment: _**Ubuntu 13.10 only - EFI**_

Hello everyone,

I"ve tried to install latest stable 3.14 Linux kernel on my system without success, until I realized it needed to be signed.

I have absolutely no idea about the process necessary to generate the "/boot/vmlinuz-3.14.0-generic_**.efi.signed**_" and to update the "/boot/grub/grub.cfg" accordingly.

Any suggestion?

---

### Post by ubfan1 on 2014-04-05
So you are trying to add a later kernel to 13.10.  You don't sign the kernels, Canonical does, so you need to download the right package.  The package install should run update-grub and create a new grub.cfg.

---

### Post by grahammechanical on 2014-04-05
Ubuntu trusty tahr does not yet have the Linux 13.14 kernel and it may not come into the repositories until after 14.04 is released. I do not think that a Ubuntu signed Linux 13.14 kernel yet exists.

You have to apply to Microsoft and pay a fee to get the to verify  that the kernel is not malicious code and then after some days/weeks Microsoft will issue a key.

Here are the latest Kernel Team meeting minutes.

[http://discourse.ubuntu.com/t/kernel-team-meeting-minutes-april-01-2014/1596](http://discourse.ubuntu.com/t/kernel-team-meeting-minutes-april-01-2014/1596)

Notice

> [COLOR=#333333][FONT=Ubuntu]The 3.13.0-21.43 Trusty kernel has been uploaded to the archive. With [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kernel freeze about to go into effect this Thurs Apr 3, _I do not _[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]_anticipate another upload between now and then._ After kernel freeze, [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]all patches are subject to our Ubuntu SRU policy and only critical bug [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]fixes will warrant an upload before release.[/FONT][/COLOR]

Regards.

---

### Post by actionmystique on 2014-04-05
Thanks for both answers, very helpful.
Now I'm wondering whether I should try to remove the EFI protection from my system.
Is it possible to do so without having to reinstall everything?

---

### Post by grahammechanical on 2014-04-05
Here is something. A Ubuntu Linux kernel 13.14. It is sure to be signed.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-10-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2014-02-10-trusty/)

By the way this problem is nothing to do with EFI. Do not mess with that. If Windows was installed in EFI mode and you change from EFI then Windows will not load. This is a matter of secure boot. This thread will interest you. Ubuntu+1 would have been a better place to ask your question. There are users in that section who like to install the very latest kernels.

[http://ubuntuforums.org/showthread.php?t=2214217](http://ubuntuforums.org/showthread.php?t=2214217)

Regards.

---

### Post by oldfred on 2014-04-06
Some opinions on secure boot:

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

If secure boot kernels are available in repository, you need to boot in secure boot mode to have those kernels installed. If not currently installed with secure boot you cannot boot in secure boot as only secure boot systems will boot. 
You can boot the Ubuntu installer in secure boot mode and use Boot-Repair to run updates and install the secure boot versions of standard kernels. Not sure how to install secure boot kernels from ppa.

---

### Post by actionmystique on 2014-04-06
[**[COLOR=#000000]@grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")**: **I don't have Windows on my system anymore. Your link do not provide signed kernels and they look like unstable ones on top of that. Finally, this problem is directly related to EFI. When my system is updated with new linux kernels from the official PPA (**3.11**), it is done with EFI-signed ones:

[https://docs.google.com/document/d/1QvIr88_XByvJJhB0DbWo4uYMVwn7LmhPA7jqA1LiRZo/edit?usp=sharing](https://docs.google.com/document/d/1QvIr88_XByvJJhB0DbWo4uYMVwn7LmhPA7jqA1LiRZo/edit?usp=sharing)

@**oldfred**: "*Not sure how to install secure boot kernels from ppa*." As far as I know, the latest kernels (3.13, 3.14) cannot be found online as signed packages.
I asked[ Tim Gardner]("https://plus.google.com/u/0/113080763989353661636?prsrc=4") (from the Linux kernel development team) about this and he indirectly replied:
"You'll have to set your BIOS into compatibility mode before you can boot an unsigned kernel."

Unless there is new information, I'm done with this issue. I'll to wait for official Ubuntu releases to provide signed kernels. The next 14.04 is supposed to land on the 17th of april.

---

