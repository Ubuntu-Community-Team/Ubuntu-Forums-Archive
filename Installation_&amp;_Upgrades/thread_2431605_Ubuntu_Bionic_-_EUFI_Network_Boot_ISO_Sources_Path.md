---
title: "Ubuntu Bionic - EUFI Network Boot ISO Sources Path?"
date: 2019-11-19
forum: Installation &amp; Upgrades
---

### Post by moogoos on 2019-11-19
I am working on some automation and everything looks to be pretty good except for the speed. I keep downloading packages from the internet, and what I think would help with the speed is to host the sources myself on a web host but I'm having a hard time getting this to work in an Ubuntu environment.

I'm running this config and then have a preseed.cfg that gets pulled from a web host currently that does a bunch of stuff.

```
menuentry "Ubuntu Server 18.04 HTTP" {
        set gfxpayload=keep
        linux  boot/server/linux ip=dhcp gfxpayload=800x600x16,800x600 hostname=unassigned-hostname domain=unassigned-domain --- auto=true url=http://server.host.net/preseed/bionic_preseed.cfg noapic noacpi nosplash
        initrd boot/server/initrd.gz
}

```

I know with redhat a lonnnnng time ago I was able to pull the ISO sources from a web directory in a config for pxeboot, but for the life of me can't figure out how to do this with a UEFI setup and grub.cfg.

---

