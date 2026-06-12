---
title: "Trouble installing on AspireOne za3"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by sasrail on 2012-04-11
I am running into a problem when installing on my netbook. I have tried both a usb install and an external cd install.

For both methods it says that 'starting restore sound card(s') mixer state(s)    Fail' after which it just hangs.

---

### Post by cortman on 2012-04-11
In the BIOS, set the boot order to nettwork boot FIRST. Then boot from your external media. This has to do with the wireless card... Without this, it will hang within a few seconds of booting. With it enabled, it boots flawlessly.
I'm not sure if this is the problem with your Aspire One, but I know it was with mine and with many Aspire One models.

---

### Post by sasrail on 2012-04-11
Mine doesn't seem to have a netboot option. 
It doesn't have a problem actually booting up. My problems seem to start after I select install.

---

### Post by cortman on 2012-04-11
Yes, it's when you try to install that it freezes up. Net boot first is supposed to fix that.
Sure you don't have an option? If not, then my suggestion won't work, I suppose.

---

### Post by sasrail on 2012-04-11
My boot options are:

PCI BEV: Realtek Boot Agent
USB HDD
USB CDROM
IDE HDD
IDE CD
USB FDC
USB KEY

In that order.

On a side note 10.4LTS is currently installing just fine.

---

### Post by cortman on 2012-04-11
> PCI BEV: Realtek Boot Agent

That's the network boot option. Glad to hear it's installing fine now! Mark [SOLVED] if this solves your issue.

---

