---
title: "EFI Boot problems"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by saal17 on 2017-08-04
My computer is a thinkpad T460p. It had windows 10 installed on it  that I had been using for months, no issue. I had also installed and  used Ubuntu on it prior to that, no problem. But when I tried to install  Ubuntu this morning, I ran into problems.

  I made a bootable stick, ran installation, everything fine. Prompt  told me to restart device to complete installation, and upon restart, what I believe is the GRUB prompt came up, asked me to choose between my SSD, "ubuntu" (even though there is no stick inserted into  the machine), and PCIE. Choosing the SSD option results in the screen turning black except for the following error message, after which the GRUP prompt returns:

  Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start MokManager: Not Found
Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found

I tried all of this I also ran Diskrepair, "repaired" boot, told me everything was fine, went to reboot, told me to remove stick and press enter, and then same thing above happened after reboot. this is the text: [URL="https://pastebin.com/F6APxku7"]https://pastebin.com/F6APxku7 
[/URL]
I tried all of this with Secureboot disabled. No luck.


  Any help would be appreciated!

---

### Post by ubfan1 on 2017-08-04
Did you mean to overwrite the Windows partitions?  Doesn't sound like the grub menu you saw, maybe the EFI boot menu, in which case, the "ubuntu" choice should boot grub.

---

### Post by ubfan1 on 2017-08-04
Did you mean to overwrite the Windows partitions?  Doesn't sound like the grub menu you saw, maybe the EFI boot menu, in which case, the "ubuntu" choice should boot grub.

---

### Post by saal17 on 2017-08-04
Actually, I don''t think it was either, comparing my screen to google images results. Selecting the ubuntu choice does nothing, screen goes black for a second, then the prompt returns, no error messages even.

---

### Post by vocx on 2017-08-04
> **saal17 said:**
> Actually, I don''t think it was either, comparing my screen to google images results. Selecting the ubuntu choice does nothing, screen goes black for a second, then the prompt returns, no error messages even.
I don't have experience installing with UEFI, as my T450s came with a legacy BIOS.

From your output I'd say everything looks pretty okay. However, it does says the SecureBoot in enabled. I'd make sure this is disabled.
```

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

```

I remember there is also some technology from Intel which is used to fast start the system, maybe it's in the BIOS options. IntelSRT, I think. Make sure everything like that is off.

Also, since you are apparently doing a fresh install, you may want to try the 17.04 version. I know you probably want the 16.04 LTS, but maybe it works better the newer system; who knows, you can try.

---

### Post by ubfan1 on 2017-08-04
What video hardware do you have, Nvidia may take a "nomodeset" on the linux line if you can get to a grub menu, edit the line starting with "linux" and add the "nomodeset" where the "quiet splash" words are.  Edit instructions on the bottom of the grub screen. then boot with ctrl-x.  When running, add the proprietary Nvidia drivers.

---

### Post by oldfred on 2017-08-04
I do not understand those errors. But have seen several other posts with similar issues.
But are you trying to boot the ubuntu entry?
Not sure what SSD entry is in UEFI, it could be a BIOS entry or something else?

The only boot file in /EFI/Boot should be bootx64.efi as /EFI/Boot/bootx64.efi. That is a fallback or hard drive boot entry. If it already exists on a system it usually is just a copy of the Windows .efi boot file. Boot-Repair will back that up and make it a copy of shimx64.efi. Many systems seem to only boot the Windows or the fallback entry. 

All the other grub .efi boot files are supposed to be in /EFI/ubuntu.

Note sure if any of these have similar UEFI and therefore same issues or not?
 T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

