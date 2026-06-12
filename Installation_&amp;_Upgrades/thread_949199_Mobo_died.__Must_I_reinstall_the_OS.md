---
title: "Mobo died.  Must I reinstall the OS?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by TheSaxon on 2008-10-15
I have an install of Ubuntu Server on an old computer.  Its motherboard just died.  The data on the server was not important enough to backup (so i dont have backups), but important enough to where rather than reinstall linux on new hardware and recreate the old Setup, I'd rather just plug the intact hard drive into a new set of hardware.
My question is that with windows, I know it is usually wise to start off a fresh install when changing the motherboard as there can be driver issues.  Is there a similar recommendation with Linux, or will I see issues if I change out hardware w/o reinstalling the OS

---

### Post by ryanhaigh on 2008-10-15
I have previously moved a couple of Ubuntu/Debian installs between computers and there are only a couple of issues that you need to worry about.

The name of your ethernet device will be different eg. eth0 > eth1. If you care about this remove the entry for eth0 from /etc/iftab

If you have X set up (which you probably don't seeing as this is a server install) then you may need to change the selected grahics card driver, I generally just change it to vesa for compatibility and then adjust as necessary on the new hardware.

---

### Post by rdoolen on 2008-10-15
I recently changed the MOBO, CPU and RAM. I didn't notice any issues at all. I was running Ubuntu 8.04 desktop.

Your situation may be very different, but I know it can work just fine.

---

