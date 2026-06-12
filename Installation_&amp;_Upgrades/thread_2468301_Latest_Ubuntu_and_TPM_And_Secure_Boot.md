---
title: "Latest Ubuntu and TPM And Secure Boot"
date: 2021-10-25
forum: Installation &amp; Upgrades
---

### Post by hennmann on 2021-10-25
I presently have the next version of Ubuntu upgraded from Bionic Beaver running in dual boot along side Windows 7 Pro on my 2015 vintage MSI 970A SLI Krait Edition AM3+ and FX8370 8 core capable of TPM V2.0 and Secured Boot indicated as Windows 8 Features in BIOS
I was going to upgrade to Win 10 and now discovered I have 11 as an option. 
My motherboard supports Secure Boot and TPM V2.0 with use of a TPM Module I have to add to a connector port on motherboard and enabling "Windows 8 Features" in bios along with generating keys stored in this now required module. 
This is required to prevent Windows 11 from aborting installation and YES I'm aware of CPU requirements but there is a Microsoft website clearly indicating they are providing leeway of CPU as long as your hardware supports TPM V1.2 and TPM V2.0 along with secure boot!
Are there any problems associated with TPM 2.0, the generated keys stored in the required module and Secure Boot enabled while using Ubuntu especially dual boot with Windows? I have the same version of Ubuntu installed in other hardware along with Win 10 but not supporting TPM or Secure Boot.
Also is there going to be similar requirements with Ubuntu requiring TPM and Secure Boot hardware in the future?

---

### Post by ubfan1 on 2021-10-25
I cannot speak to TPM issues, but Ubuntu's shim approach to secure boot has been working for almost a decade.  Third party modules, like Nvidia proprietary video drivers are a problem, but if you do your own keys and signing, even that can be made to work with secure boot.  I'd suggest going with Windows 10, and avoid any TPM issues and let Windows 11 shake down a bit.

---

### Post by grahammechanical on 2021-10-25
I think the question you should be asking is: "Does Linux require an enabled Trusted Platform Module (TPM) chip? Ubuntu is kept up to date with Linux kernels. I am very certain that my 2007 motherboard does not have a TPM chip or a header that a TPM module can be connected to. I am running an up to date version of Ubuntu with an up to date Linux kernel.

I found this explanation in PCMag (25 June 2021) educational.

[https://uk.pcmag.com/components/134144/what-is-a-tpm-and-why-do-i-need-one-for-windows-11](https://uk.pcmag.com/components/134144/what-is-a-tpm-and-why-do-i-need-one-for-windows-11)

I note this comment:

> **Will a TPM Prevent Me From Running Linux?**

Conversely, plenty  of PC enthusiasts have computers that do support TPMs but who have  chosen to disable them for a variety of reasons. If this is you, Windows  11 brings good news and bad news. 


The good news is that pretty  much anything you want to do with a PC these days can be done with TPMs  enabled. Yes, there are exceptions, but they&#8217;ll only affect a tiny  percentage of users. For example, the TCG has long specified TPM [requirements]("https://trustedcomputinggroup.org/resource/tcg-software-stack-specification-tss-1-2-faq/")  for the open-source Linux operating system, which means that people who  want to switch their PCs between running Windows 11 and various Linux  distributions should be able to do so. Support will vary depending on  which Linux distribution you're using, and how the TPM requirement may  interact with dual-boot environments is not yet 100% clear.


And then there is this older and definitely more technical article from the Linux Magazine.

[https://www.linux-magazine.com/Issues/2018/206/Trusted-Platform-Module](https://www.linux-magazine.com/Issues/2018/206/Trusted-Platform-Module)

I searched for trusted platform module at Ubuntu.com and got this list of documents

[https://ubuntu.com/search?q=trusted+platform+module](https://ubuntu.com/search?q=trusted+platform+module)

Reading through that lot and trying to understand it all will take years off my life and I do not have that many years left. A Quick glance tells me that TPM has to be enabled in the Linux kernel and Ubuntu core can take advantage of TPM.

Any Linux distribution that enables TPM in the kernel by default will shut out the users of millions of PCs that possibly might want to run Linux as their hardware becomes more and more out of date. Microsoft is willing to lock out users of older hardware with the release of Windows 11 but previous version upgrades of Windows have often left users of older hardware unable to upgrade to the latest Windows. Forcing users to buy newer hardware. And Microsoft has to do something to change the perception that Windows is an insecure OS.

That has not been the approach of the Linux developers. I do not think that Linux developers will change their approach. They will make it possible for commercial organizations and others with compatible hardware to benefit from DPM if they choose. I do not think that Linux developers will deliberately lock out potential users of Linux.

Regards

---

### Post by MAFoElffen on 2021-10-26
Double post. Dang...

---

### Post by MAFoElffen on 2021-10-26
Well... LOL. Sort of round-about as SecureBoot, because you are still on Bionic.

20.04 was the first Ubuntu LTS to openly support installing in SecureBoot Enabled. Before that Debian said they wouldsupport SecureBoo, then backed off, saying they would get back to it. (I think they left that for Ubuntu to sort out...) saying they would support it in the future. To do it in Ubuntu, most here tell people to turn SecureBoot off, but there was/is a way (needed before 20.04) to gen secure keys with the mokutil utility to get previous versions to work with SecureBoot as being trust/digitally signed... In 20.04.x, then you have grub-efi-<arch>-signed, which will boot in SecureBoot and take care of all that.

TPM... Linux does not care about it as a minimum hardware requirement. It will use it if you install something that can use it, but for the most part it isn't going to prevent anything.

I myself... Well, MS put out their preview of Win11 as somewhat open, to hook people in. Then in the retail release made a few locks to TPM, UEFI and SecureBoot... and a very short list of recent CPU's that they then said the required, That if not, it would not even install. It is not that bad... Some of those "locks" are just hype, as demonstrated in this thread I demonstrated on old hardware from 2012:
[https://ubuntuforums.org/showthread.php?t=2468297](https://ubuntuforums.org/showthread.php?t=2468297)

I have a few commands in that first post to run in Linux CLI to see if you have TPM and what version it is. Some Vendors have firmware upgrades to upgrade their Intel TPM modules to either 1.2 or 2.0 (Dell, HP, Lenovo), but I do not think MSI is one of those.

Get a legal Win11 license. Download an ISO. Use recent Rufus to create a USB install media. It will install without caring about your CPU or TPM version.

Both recent Ubuntu (20.04.3) and Win11 can live with SecureBoot.

You could run a software emulated TPM 2.0... but why? Even Microsoft themselves, came up with instructions to get around the TPM 2.0 requirement (LOL):
"[Microsoft Shows How To Bypass TPM 2.0 Requirement For Windows 11]("https://www.gamespot.com/articles/microsoft-shows-how-to-bypass-tpm-2-0-requirement-for-windows-11/1100-6496853/")"

---

