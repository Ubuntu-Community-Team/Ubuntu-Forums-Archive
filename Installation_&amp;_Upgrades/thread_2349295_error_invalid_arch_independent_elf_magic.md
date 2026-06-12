---
title: "error invalid arch independent elf magic"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by davzd on 2017-01-13
Sorry to be a bother folks. Was hoping someone might be able to help me. I have a Ubuntu 16.04.1 install. Haven't done anything unusual of late other than the usual apt upgrades, but when I rebooted this time I got the above error message.

Dug around on the forums and found some old posts dating from 2011, but was a bit worried as there were different instructions on how to fix grub. One post referred to the boot-repair live image, so I downloaded that and gave it a try - twice actually - but each time I finished and tried to reboot, there was still that dreaded elf magic.

As suggested by the boot-repair utility, I'm posting a [link to the boot info from running the utility]("http://paste.ubuntu.com/23791019/") in the hopes that someone might be able to help me out of this mess. This was from the second attempt at running boot-repair.

Any suggestions or advice would be most appreciated!

---

### Post by oldfred on 2017-01-13
Usually that error is related to incorrect version of grub and one version is UEFI and other is BIOS/CSM/Legacy.

Boot-Repair says UEFI Secure Boot is on?
Is then system trying to boot in UEFI mode, but you have a BIOS install in sdc?

---

### Post by davzd on 2017-01-13
Thanks very much for the note oldfred. No, I don't believe UEFI Secure Boot is on. The computer in question is circa 2008 and I think uses plain old BIOS. The board is an Intel S5000PSL. Just took a quick peek at the manual, and there aren't any references to UEFI or Secure Boot, only BIOS, so I don't believe it's trying to boot in UEFI mode.

---

### Post by oldfred on 2017-01-13
UEFI only became popular with PC when Windows 8 came out in 2012.
So your system would not be UEFI.

But issue can still be related to incorrect versions of grub.

From Boot-Repair run the full uninstall/reinstall of grub in Boot-Repair's advanced options. That should fully resync version of grub installed.
Make sure Internet is working as it totally erases grub which would prevent booting and has to download new copy of grub to reinstall.

---

### Post by davzd on 2017-01-14
Thank you again oldfred. I tried the full uninstall/reinstall as you had suggested. Just FYI, it seemed in the advance options they were already selected. I also checked off the option to install the latest version of GRUB. It went through the steps and looked like it all worked - at least no error messages - but unfortunately on booting up the system I still get the same error message. Here is the boot-info from this most recent attempt: [http://paste.ubuntu.com/23796575/](http://paste.ubuntu.com/23796575/).

Please do let me know if you might have any further suggestions.

---

### Post by oldfred on 2017-01-14
I do not see anything wrong. 

The only different version of grub is in the PBR partition boot sector of sdc1, which should never be accessed or used. Or that should not matter.

Not sure what else to suggest.

---

### Post by davzd on 2017-01-14
OK. Thanks anyway.

---

