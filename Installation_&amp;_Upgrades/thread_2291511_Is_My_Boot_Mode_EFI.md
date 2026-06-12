---
title: "Is My Boot Mode EFI?"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2015-08-20
Hello  how can i find out if my boot is in EFI mode or what boot mode? Thanks

---

### Post by Quarkrad on 2015-08-20
Reboot your pc and look carefully at the boot text on the screen - there will be some text about what key to press to enter Setup or Bios, a common key is the Delete key.  Instead of booting to your Desktop the pc will take you to your BIOS screen(s).  You should be able to tell from these screen if you are in EFI mode.

---

### Post by Bashing-om on 2015-08-20
tomsubt; Hello:

Here is a way to have the system tell you what the booting mode is:
From an Ubuntu installed on the HDD (neither liveCD nor liveUSB), open a terminal (Ctrl+Alt+T), then type the following command:
```

 [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

```
If the result is "Legacy boot on HDD", then either the BIOS is not UEFI type, or the BIOS is not set up to boot the HDD in UEFI mode.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by tomsubt on 2015-08-20
ok, it says its gfxmode! so can i proceed to installing windows 10 along side ubuntu? I wont be doing it until tomorrow.

---

### Post by oldfred on 2015-08-20
gfxmode is related to video, not UEFI nor BIOS.

Post this, it MBR(msdos) then it is BIOS boot, but if gpt it may be UEFI boot or BIOS boot:
sudo parted -l

But that is not conclusive as you can boot a gpt partitioned drive with BIOS. But Windows only installs to gpt drives with UEFI and only to MBR drives with BIOS.

---

