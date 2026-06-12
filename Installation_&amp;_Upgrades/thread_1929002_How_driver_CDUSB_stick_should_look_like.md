---
title: "How driver CD/USB stick should look like?"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by yau on 2012-02-21
Hi,

I am installing Ubuntu server 11.10 64-bit. Installation reached the step "No drive was detected". I have from manufacturere .ko driver compiled for 11.10 server 64-bit. I copied it to USB stick to the root directory and select: "Driver needed for your disk drive: none of the above", "Load missing drivers from removable media? Yes". The result: "Cannot read removable media, or no driver found". dmesg full of "end_request: I/O error, dev fd0, sector 0", and nothing about loaded driver.

1. How to force Ubuntu installer to load this .ko driver from USB stick or CD without switching to Alt+F2 console?
2. How to tell him to load helper scsi modules first `modprobe scsi_transport_sas`, `modprobe raid_class` - before loading this .ko driver.
3. How to notify installer that this driver should be in initrd image for successful boot afterwards?

Thank you.

---

