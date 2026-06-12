---
title: "dual boot install from hdd (like wubi)"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by ghosttr on 2014-02-04
I just got a new SSD and moved my windows installation to it, leaving me a free hdd to install ubuntu on. I tried wubi before but it seems that its no longer supported.:mad:So now i have to find some way to accomplish the same thing.:confused:

---

### Post by Frogs Hair on 2014-02-04
This is for UEFI and might not apply but it is a starting point.

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by ghosttr on 2014-02-04
> **Frogs Hair said:**
> This is for UEFI and might not apply but it is a starting point.

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

That's close, however I want to install the OS without external boot media.

[http://www.instructables.com/id/Install-Windows-7-without-USB-or-DVD-without-upgra/](http://www.instructables.com/id/Install-Windows-7-without-USB-or-DVD-without-upgra/)

Is what I did to load win7 onto my ssd (or something very similar). I loaded the files onto the new drive, booted into the installation from the windows boot manager, installed the os, once everything was good I switched the boot order in my bios so the new installations bootloader would take over (both appeared in the bootloader fine, but i intended to repurpose the old drive).

I was hoping there would be an easy way to do the same thing with ubuntu.

---

### Post by sudodus on 2014-02-05
Are you using conventional BIOS or UEFI? It makes a big difference, you need different methods to install dual boot in these cases. If you don't know, please check in to BIOS/UEFI menus that you enter with a hotkey right at the beginning at boot (or reboot).

Please give us the specs of the computer:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

*If you have not downloaded Ubuntu yet, wait for advice* until we know the specs of the computer.

It will also make it easier to help, if you run the following command from a terminal window, when you are **trying** Ubuntu (running it when booted from a CD/DVD/USB drive without installing).

```
sudo parted -l
```

and post the output text (copy and paste) in a reply. [COLOR=#ff0000]**Go Advanced**[/COLOR], mark the text and put it within code tags with the **#** icon at the top of the editing window.

---

### Post by Frogs Hair on 2014-02-05
> [COLOR=#000000]That's close, however I want to install the OS without external boot media.[/COLOR] I think Wubi was the only way to do that and there is 12.04 available ,but remember it is for temporary/trial use . Wubi has 30 Gb max and installs on the C drive by default . Moving it to or getting it to install on a another drive , expanding the partition and creating a real swap partition instead of file would be more complicated than a more traditional dual boot.

---

