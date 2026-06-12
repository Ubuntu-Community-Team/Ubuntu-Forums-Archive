---
title: "Fulldisk encryption and secureboot issue not booting 18.04.1 (@paddy-landau)"
date: 2018-08-13
forum: Installation &amp; Upgrades
---

### Post by j.folwer on 2018-08-13
Hi,

I've been trying to set up an encrypted windows + ubuntu disk using the great howto from Paddy Landau and this wiki: [https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)
What I get after following the instructions is: 
```
error: no such device: <long-UUID-string> 
error: no server is specified
error: you need to load the kernel first

```
**The system *will* boot fine with secureboot disabled**, so I guess something seems wrong there. I can boot fine on standard ubuntu install, and the ubuntu MOK and my own MOK are in the bios and enrolled.

The UUID on the first line is not any of the UUIDs on my computer and it comes from** /boot/grub/x86_64-efi/load.cfg** which is like this:
```
search.fs_uuid <the bad uuid> root lvmid/<another strange lvmid>
```

The /boot/efi/EFI/ubuntu directory contains both the shim and the grubx64 **signed** bootloades. I tried booting directly with the grubx64 or via the shim. 

My uneducated guess is that the cryptodisk modules and crymtomount -u are never loaded. I never get the request for the passphrase to unlock the crypted pv partition. Perhaps because they are not signed ? Do they need to be copied in /boot/grub/efi/EFI/ubuntu/x86_64-efi by the grub-refresh script ? The normal ubuntu install seems to not copy them, yet it boots fine without (from lvm / full disk encrypted partition).

The computer is a dell xps 15 - 9670 latest bios. As stated before, MokUtil and key management are honored and work for standard ubuntu.

Any ideas how to proceed ?

EDIT: Ok, I went a little further. Enabled debug=all and pager=1 in grub.cfg to see what goes on in the boot process.
I can confirm that cryptomount is loaded by grub, but is never executed with secureboot enabled. When disabled it is called and scans trough the partitions and eventually asks for the crypted passphrase. With secureboot enabled it's skipped, never called and thus nothing works.

---

### Post by Paddy Landau on 2018-08-13
Hi, the pages were in a state of flux due to important changes to Ubuntu 18.04. Some of the steps wouldn't work, and so I've been updating the documentation.

I rather suspect that the inconsistencies got you!

There's a message at the [very top of the page]("https://help.ubuntu.com/community/ManualFullSystemEncryption#PLEASE_READ_FIRST") that you might have missed warning about this.

Do you need this urgently, or can it wait for a few days while I complete the updates? (I would do it faster, but I'm dealing with long-term illness that slows me down, unfortunately.)

If you need the installation urgently, let me know.

Oh, and I need to know which version you are trying to install. The instructions are optimised (or, rather, will be optimised) for Ubuntu 18.04 (or any of the official flavours, e.g. Lubuntu 18.04).

---

### Post by j.folwer on 2018-08-13
Hello and thanks for answering so quickly. I'm in no hurry but just interested in getting this working and polished. 
Yes, I read the warnings and expected some issues . I'm a little sorry I could not fix them myself this time, despite trying to rebuild the bootloader and config a few times, singing my own binaries and modules etc. I'm not that familiar with secureboot. All I know is generics on signing the binaries and working with the MOK, but never actually got my hands dirty with the grub code and less so in the ubuntu boot process.

I'm using **plain Ubuntu 18.04.1 desktop. **When installing via the installer, and selecting the "additional drivers" checkbox, it will create the MOK certificates and private key and use mokutil to request the enrollment. On a reboot the enrollment works and I'm able to enroll the keys.

---

### Post by Paddy Landau on 2018-08-13
I'm glad that you can wait. I hope to be finished by the end of this week.

I also don't know much about secure boot. I put the instructions together with plenty of help from other people; guesswork; persistence; and a refusal to believe the experts who told me, "No, it can't be done — /boot must be left unencrypted!"

The good news is that I've managed to get both Ubuntu 18.04 and Lubuntu 18.04 working, so I know that it's possible.

---

### Post by Paddy Landau on 2018-08-22
I have finished all the changes. Please check the [new thread for MFSE]("https://ubuntuforums.org/showthread.php?t=2399092").

---

### Post by j.folwer on 2018-08-22
You did a huge job. However, secureboot still has the same issue. Did you try on a computer that enforces efi loader signing and has proper secureboot sequence?

I will switch to the other thread now. We can discuss that there unless you prefer to use this one as it's more specific.

---

### Post by Paddy Landau on 2018-08-23
> **j.folwer said:**
> Did you try on a computer that enforces efi loader signing and has proper secureboot sequence?
Unfortunately, I don't have access to that type of hardware. I am testing on [VirtualBox]("https://www.virtualbox.org/"), as my computer is too old, and in preparation for when I (finally) scrape together enough money to replace it!

I think that you know rather more than I do about this. I should also point you to [comment #25]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457/comments/25") on the [bug request]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457"), where Jonathan Polom explains Ubuntu's shortcomings in signing. I suspect that that is what causes you your problem. I would love to raise a bug request for this, but unfortunately I have insufficient knowledge about what specifically to report.

You are welcome to repost this on the main thread, if you wish, in the hope that someone with significantly more knowledge than I have will answer.

---

### Post by j.folwer on 2018-08-26
Hi,
I have some more information, but unfortunately not a ready solution.
With secureboot enabled shimx64.efi loads grubx64.efi and this works. 
However grubx64.efi is signed with canonical's key and is not available in source code. 
Grub has module loading, and it's own openpgp way of signing and verifying loaded modules. Unfortunately the ubuntu's version of grub (including the signed one) contains a patch, inherited from debian, that disables module loading in grub when secureboot is enabled. They don't even try to load them signed or not. This looks like a quick fix to avoid backdoor loading on a secureboot system.

As you might have guessed, the luks.mod and cryptodisk.mod modules are not included in the grubx64.efi binary and cannot be loaded from disk because module loading is disabled with secureboot enabled.

So, the solution seems to be to compile and sign a custom grub version, which includes the required modules and/or enables module signature verification and loading with secureboot (this could be just a quick patch to existing debian patch).

This solution would, off course, require either a custom PK/KEK/DB key and certificate management (i.e. proper secureboot, removing microsoft and canonical key trust from the bios), or a simpler solution involving the generation of a custom user MOK and it's enrollment in the BIOS via the MokManager

Speaking of current MOK generated by Ubuntu at install time, it cannot be used to sign grub. It's generated with a specific limitation to kernel drivers only (so that ubuntu can load nvidia/wireless etc drivers) but will not be honored by the bios for loading the grub binary at boot.

We end with a mixed bag of news and solutions. At once it is foolish to rely on full-disk encryption in it's current form without secure boot because anybody can modify the efi and insert a backdoor/keylogger. Once the root is unlocked, it's trivial to unpack the initramfs, patch it and repack it in an undetectable way. The initramfs is not even checked (perhaps until now) by the kernel.

On the other side, the proper implementation means patching grub2, signing own keys and installing them in the uefi bios. This is not hard but time consuming and cannot be simulated easily in virtualbox (altough vmware esx has support for secureboot, I'm not sure if the esxi free version has it).

It seem that canonical/ubuntu folks are aware of the issue. There's quick a lot of documentation here: [https://wiki.ubuntu.com/UEFI/SecureBoot/Testing](https://wiki.ubuntu.com/UEFI/SecureBoot/Testing) 
There's also some more information to be found from the ppl at Arch Linux and Gentoo (who are used to signing their own kernels and binaries).

I'm however very constrained on time and not sure how much more of it I can dedicate to this issue :(

Hope this information is enough to get the ball rolling.

---

### Post by Paddy Landau on 2018-08-27
> **j.folwer said:**
> I have some more information…
Thank you for all of that. Most of it is, unfortunately, beyond my level of competency.
> **j.folwer said:**
> … grubx64.efi is signed with canonical's key and is not available in source code. …
Hmm, I though that Canonical had purchased the Microsoft key specifically for UEFI. Am I mistaken, or is it more complicated than that?
> **j.folwer said:**
> We end with a mixed bag of news and solutions. … the proper implementation means patching grub2, signing own keys and installing them in the uefi bios. … It seem that canonical/ubuntu folks are aware of the issue … [https://wiki.ubuntu.com/UEFI/SecureBoot/Testing](https://wiki.ubuntu.com/UEFI/SecureBoot/Testing)
The link that you gave refers to a bug report about [Grub loading an unsigned kernel]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532"). Is this related?
If so, should we add a comment referring to your post?
If not, should we raise a new bug report using your post as a base?
> **j.folwer said:**
> … cannot be simulated easily in virtualbox
VirtualBox has UEFI implementation, but I don't know how faithful it is to the UEFI specifications. What is a straightforward way to test it?
> **j.folwer said:**
> Hope this information is enough to get the ball rolling.
Unfortunately, as mentioned earlier, I'm rather ignorant of how the whole thing works. I would be happy to raise this further, but I really need the support of someone who knows what they are talking about, because I don't!

I wonder if I can elicit help from this forum, perhaps in the Security subforum? What do you think?

---

### Post by piontec on 2018-09-07
Have you made any progress with this? I'm stuck on exactly the same problem and using full disk encryption without secure boot is just a fancy way of delaying your system startup :(

---

### Post by Paddy Landau on 2018-09-07
> **piontec said:**
> Have you made any progress with this? I'm stuck on exactly the same problem and using full disk encryption without secure boot is just a fancy way of delaying your system startup :(
Unfortunately not. You can support the [bug request]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532"), but until Canonical fixes the secure boot, all that we can do is encrypt what we can. The bug request has been rated as "high", so I'm feeling quite hopeful about it.

---

