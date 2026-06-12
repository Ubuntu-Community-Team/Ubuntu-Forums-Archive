---
title: "No boot 16.04 on a HP laptop Intel core duo"
date: 2017-12-14
forum: Installation &amp; Upgrades
---

### Post by axelsword on 2017-12-14
Live CD works. Installation successful. System is 64 bit.

When trying to boot, it says "Non-System disk or disk error, replace and strike any key when ready"

Screen-shot of system configuration
[https://www.dropbox.com/s/2zfc9ka79pv5i6o/Screenshot%20from%202017-12-14%2015-34-17.png?dl=0](https://www.dropbox.com/s/2zfc9ka79pv5i6o/Screenshot%20from%202017-12-14%2015-34-17.png?dl=0)

---

### Post by oldfred on 2017-12-14
If you installed, then grub should be in MBR and boot.
But sometimes it does not install fully/correctly. Reinstall of just grub may be all that is required.
But lets see configuration first.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kansasnoob on 2017-12-14
I suspect either the BIOS is looking for a bootable disc in the wrong place or GRUB didn't install in the right place. Please post the link to a boot info summary after running Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can use the second option, installing Boot Repair in Ubuntu, using the live media you used to install Ubuntu.

---

### Post by axelsword on 2017-12-16
Report generated to
[https://paste.ubuntu.com/26193247/](https://paste.ubuntu.com/26193247/)

---

### Post by oldfred on 2017-12-16
Do you have UEFI Secure boot on?
System is installed in BIOS boot mode, which will not work if Secure boot is on.

Report says this:
> SecureBoot maybe enabled.

---

### Post by axelsword on 2017-12-20
There was no "secure boot" option in BIOS.

I don't know what mode system was installed in. I put in the live CD and everything was in auto mode.

Is there a way to use Ubuntu on the laptop?

---

### Post by oldfred on 2017-12-20
If Core2 Duo before UEFI, so no UEFI Settings, but you may still need BIOS settings.

Newer HP have checks by Description, but BIOS boot did not have those type of settings or capability to check on what was in MBR.
Is system set to boot from drive seen as sda?

While I have used gpt with BIOS on similar configured system, perhaps your BIOS does not like gpt partitioned drives?
Did system originally come with 1TB drive. Sometimes BIOS does not like larger drives unless updated to newest BIOS if available. Is drive seen correctly in BIOS?

---

