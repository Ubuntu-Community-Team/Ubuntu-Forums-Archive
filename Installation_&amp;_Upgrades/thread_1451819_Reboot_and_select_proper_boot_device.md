---
title: "Reboot and select proper boot device"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by the.ronn on 2010-04-11
After several years, I've FINALLY taken the plunge into Linux.  I just got an Asus 1001p netbook so I figured this would be a great opportunity to get my feet wet.  With that said, please bare with me - while I'm fairly comfortable with various flavors of Windows installations, this is my first time trying to set up any Linux distribution.

Short of it is, when I try to boot, I get the message "Reboot and select proper boot device" message.

I downloaded "ubuntu-9.10-netbook-remix-i386.iso" and burned it to a CDR which I used to install onto the netbook.  I chose the regular install option as opposed to the try ubuntu option (or something along those lines).  As far as I could tell, the install went fine.  I got to the desktop and noodled around some of the sections.  But I noticed while I was checking out the sections, it was still reading from the external DVD/CD reader.  As mentioned, when I try to reboot, I get the "Reboot and select proper boot device" message.

The boot priority is set appropriately in bios, the turbo boot has been disabled, I tried setting the SSD both to AHCI and IDE.  In case it matters, I just upgraded my 1001p with 2GB of RAM (checked to make sure it worked fine before attempting the UNR install) and also replaced the HDD with a 60GB Vertex SSD.

Thanks for any advice.

---

### Post by oldfred on 2010-04-11
Is the error message from the BIOS. Windows requires a boot flag on a primary partition, linux/grub does not, but some BIOS check that a primary partition has a boot flag as it thinks the system is not bootable.

The * is the boot flag is you already have one. From terminal in LiveCD.
```
Sudo fdisk -l
```

If you need one you can use gparted from live CD & right click on the partition to manage flags.

---

