---
title: "Can't install to CF adapter (DMA issue)"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by djm-uk on 2008-11-30
Ok - I'm trying to install Ubuntu to a PATA CF (compact Flash) adapter. This DOESN'T run DMA (PIO4 only). Trying either 8.10 or 8.04 fails early on in the install process with a bunch of ATA1.00 timeouts. I need to do a 'command line system' install as it is only a 2GB drive... I have tried adding ide=nodma, hda=nodma and sda=nodma to the boot options with no effect, After a bit of searching I tried Dapper which is installing right now but will probably run out of disk space.. I suspect the issue is the libata library - quote from libata FAQ ([http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)) regarding 32bit IO support "....Unless you are one of a few rare cases such as PATA CompactFlash, you don't need to care about this. Eventually 32-bit I/O will be supported, but it is very low priority..."

SO... The question is How do I revert back to the 'old' ATA/IDE drivers as used in Dapper - is there a bot time parameter as this is failing at install time so I am running from RO media...

Thanks

David

---

### Post by somnorosul on 2008-12-18
Hope this will be seen by many because there are a lot of threads out there with this proble.
I myself lost a night because of this.
The problem is that all the bootparams that you get on a search for disable dma are for the old ide module of the kernel.
ubuntu uses the new libata module that have diferent parameters.
So to disable udma for an ide device:
look in the dmesg for the device that timeouts (ex. ATA1.00)
edit the file /etc/modprobe.d/options
and "force=1.0:pio4" to the line with libata
then:
sudo update-initramfs -u
and reboot, youre good to go.
for reference:
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html)

---

