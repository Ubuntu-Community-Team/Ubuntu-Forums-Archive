---
title: "clean install and need bootloader repaired"
date: 2021-01-21
forum: Installation &amp; Upgrades
---

### Post by wildman36 on 2021-01-21
Here is the [pastbin]("http://paste.ubuntu.com/p/R7S34k2hRk/")

Did a *clean install of Win 10* to **sda** and **ubuntu to sdb** in the ultrabay of the [I]Thinkpad t440p
[/I]
I am now gettting a grub menu but win 10 is not an option.

Please help, need to get into windows for something important.

---

### Post by Impavidus on 2021-01-21
I only had a quick look at your output, but I think you should be able to access the UEFI menu (coming before the grub menu) to try the Windows boot loader. That will load Windows.

---

### Post by tea for one on 2021-01-21
There is something unusual in your set up.
If you did a clean install of Windows 10 to sda, then your EFI partition should be on sda also.

Your EFI partition is on sdb1 [COLOR="#0000FF"]Line 117[/COLOR]

It may well be a clean install but possibly a bit untidy.

I do not think that this is ideal for the future because if your sdb drive fails (or is inaccessible) you will not be able to boot Windows on sda.

Your are in a good position with your hardware because each OS on a separate drive is sensible.

However, it would be better to set them up [COLOR="#0000FF"]independently[/COLOR] to avoid one drive failure affecting the other drive.

UEFI mode, GPT (partion table), EFI partition on each drive and choose each OS via UEFI boot menu.

---

### Post by oldfred on 2021-01-21
Your UEFI boot entry for Windows shows it using same GUID/partUUID as Ubuntu or the ESP on sdb.
But now you have no /EFI/Microsoft folder in the ESP.

Windows may have installed its boot files to an ESP on sdb, if sdb was set as default boot drive in UEFI.
And then you may have erased ESP. Normally grub would just install into the same ESP as Windows, so not sure what happened.

Often easiest to make sure each system is totally on its drive, is to disconnect the other drive either physically  or disable in UEFI settings, so not seen.
You then just have to be sure to install both in UEFI boot mode.

---

