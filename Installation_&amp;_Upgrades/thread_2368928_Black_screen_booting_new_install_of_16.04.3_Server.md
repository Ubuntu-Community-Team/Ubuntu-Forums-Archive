---
title: "Black screen booting new install of 16.04.3 Server on NUC6i7"
date: 2017-08-16
forum: Installation &amp; Upgrades
---

### Post by hamzamian on 2017-08-16
I've just installed Ubuntu Server 16.04 LTS (downloaded this morning) onto an Intel NUC6i7KYK. It starts to boot fine but then I suddenly just get a black screen. (connected via HDMI)

If on the GRUB boot menu I choose the recovery mode and then select to resume boot from there (it warns me that some graphics drivers require a full boot and might fail) then I can boot to a prompt ok. Once I did that I did a sudo apt-get update / sudo apt-get upgrade to ensure everything is up to date but I still get the same behaviour.

On the boot screen the last line before I get a black screen (and the monitor goes to sleep as it thinks it has no input) I can see says the following:
switching to inteldrmfb from VESA VGA

So it looks like there is some kind if graphics problem. I've tried searching for a fix but most reports of similar issues seem to indicate this should not be a problem on 16.04 LTS (kernel version 4.4).

I had already upgraded the BIOS to version 00049 which is the latest available for this NUC on Intel's DownloadCentre.

I'd appreciate any pointers on what to try next.
Thanks!

---

