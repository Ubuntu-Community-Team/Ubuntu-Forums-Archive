---
title: "Dual-boot install without &quot;SecureBoot&quot;"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by yeah-whatever on 2017-03-09
"Secure boot" is disabled in the BIOS of the computer I want to dual boot with Ubuntu.  Is there anything "special" I have to do in order to get it installed?  All the guides I've found seem to indicate UEFI is turned on, but I'm guessing since Secure Boot is turned off, UEFI isn't enabled either.

---

### Post by oldfred on 2017-03-09
There are actually three boot modes, UEFI with Secure boot, UEFI and CSM/BIOS/Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

If system is UEFI, usually best to install in UEFI boot mode. 

I do not use Secure boot, currently. And have no plans to use it. But later it may be necessary and BIOS mode cannot be secure boot.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lots more UEFI info in link below in my signature.

---

### Post by yeah-whatever on 2017-03-10
I'm not sure that really helps :)  On my computer SecureBoot is off.  I can't actually see any reference to UEFI in the BIOS (other than what is implied by the availability of "Secure Boot").  Are there any steps I need to take - maybe there is a guide out there for "BIOS mode"? - if the computer is not using UEFI at all?

---

### Post by Dennis N on 2017-03-10
A computer with an old-fashioned BIOS would not have any mention of Secure Boot, so your firmware must be UEFI. You can install Ubuntu with Secure Boot on or off. Some other Linux distros will not install with Secure Boot on - Linux Mint is an example.

For best results in a multiboot setup, I would leave Secure Boot off.

---

### Post by oldfred on 2017-03-10
Computers have used BIOS/MBR for 35 years. So any old guide works for that.
And basic instructions for UEFI install are essentially the same and in link in my signature. It is how you boot install media UEFI or BIOS on how it installs. And gpt partitioning normally used with UEFI. Windows requires gpt for UEFI boot and MBR for BIOS boot, but Ubuntu can boot from gpt in BIOS boot mode, if correct gpt partitions for grub are available.

If you have a correctly configured flash drive installer, your UEFI should show two boot options. You may have to separately turn on allow USB boot in UEFI.
One option is UEFI:flash and other just 'flash' which then is BIOS boot. And 'flash' is name, label, brand or similar on USB flash drive you are using.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Post this from live installer to know if gpt or MBR partitions, probably gpt if newer system.
sudo parted -l

---

### Post by yeah-whatever on 2017-03-10
> **Dennis N said:**
> A computer with an old-fashioned BIOS would not have any mention of Secure Boot, so your firmware must be UEFI.
Precisely.  But there is no option to turn it on or off, and there is no sign in Win 8 that it knows anything about it being on (as far as I can see).

 > You can install Ubuntu with Secure Boot on or off.
The guides I've seen say to stop following the guide if a GUI-type install screen comes up, which I believe is what happens if UEFI is not active.

---

### Post by oldfred on 2017-03-10
What brand/model system?
Only a few 32 bit UEFI tablet type systems do not have a way to turn off Secure Boot.

Microsoft requires Vendors to use UEFI if Windows 8 or 10 is pre-installed and vendor must let user turn off Secure Boot.
Check your manual, some are not as clear as others.

---

