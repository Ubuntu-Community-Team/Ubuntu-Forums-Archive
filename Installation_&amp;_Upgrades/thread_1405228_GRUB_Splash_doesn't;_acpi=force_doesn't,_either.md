---
title: "GRUB Splash doesn't; acpi=force doesn't, either"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-12
On my new installation, I've tried to get a GRUB splash image (I'd attach it, but I don't have the final GZIPped file handy at the moment, and the forum won't accept a naked xpm), but all I get is an error message.

With grub, and the splash image, in (hd0,8)/grub, and the splash image named grubsplash.xpm.gz, and a link to it called splash.xpm.gz,

splashimage=(hd0,8)/grub/grubsplash.xpm.gz

splashimage=(hd0,8)/grub/splash.xpm.gz

splashimage (hd0,8)/grub/grubsplash.xpm.gz

splashimage (hd0,8)/grub/splash.xpm.gz

all produce the same result: "Failed to read splash image (hd0,8)/grub/<name>.xpm.gz"


With a 1998 BIOS, (Dell Dimension D300 motherboard) I get a message on kernel launch, saying that the BIOS is earlier than the cutoff date, and I need "acpi=force" for acpi support. But if I tack that on to the end of the kernel parameters, I get another error message (which I didn't write down yet) following the "acpi=force needed" message, and then when I shut down, it still fails to actually shut down the power. This in spite of the fact that both Red Hat 8 and a freeware acpi shutdown program for DOS have no trouble shutting it down.

---

### Post by hbquikcomjamesl on 2010-02-12
The splashimage I want to use is attached.

As to the ACPI error message, it's something about "ACPI unable to load system description tables"

---

### Post by hbquikcomjamesl on 2010-02-13
More on the acpi=force issue:

The DOS shutdown utility (shutdown.exe, v1.2, by Blacklight, available from the "Interesting DOS Programs" site, [http://www.opus.co.tt/dave/utils.htm](http://www.opus.co.tt/dave/utils.htm)) that works on this motherboard uses APM, rather than ACPI.

Can the 8.04LTS kernel be told to use APM instead of ACPI?

---

### Post by hbquikcomjamesl on 2010-02-13
A member of the local user group gave me a GOOGLE search, that in turn led me to here:
[http://www.togaware.com/linux/survivor/APM_Power.html](http://www.togaware.com/linux/survivor/APM_Power.html)

Based on that page, I tried "apm=on apm=power_off" in the kernel parameters. No joy.

Then I tried "sudo modprobe apm power_off=1" in a terminal window. No joy again. There's definitely an "apm" loadable module in there. But for some reason, even though RH8 and the DOS utility are able to successfully power down the system, Ubuntu 8.04LTS doesn't.

On the "grubsplash" front, I happened to notice that even though I save the image as an xpm with 14 indexed colors, every time I open it in GIMP, it comes back as an RGB image. I think I'll try it tonight in Lemkesoft GraphicConverter, on my old Mac 5215.

---

### Post by hbquikcomjamesl on 2010-02-18
Interesting development on the Ubuntu's seeming inability to shut down the power: we powered up a Win2k box around the office with the same model motherboard, and I happened to notice that Win2k couldn't shut it completely down either.

Yet RH8, and the DOS shutdown utility, both seem (seemed, in the case of RH8) to have no trouble shutting it down.

---

