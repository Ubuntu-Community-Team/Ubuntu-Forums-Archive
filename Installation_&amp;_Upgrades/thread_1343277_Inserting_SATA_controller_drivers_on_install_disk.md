---
title: "Inserting SATA controller drivers on install disk"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by oxygen on 2009-12-01
Hi all,

I am regularly building servers which are using Rocket Raid 2340 SATA controllers (to provide 16 SATA connections).

At the moment, during (text-mode) installation, I have to mount  USB stick with the drives, run a shell script, switch back to the installation, then before reboot, switch back to the shell and run another command.

This is all because the installer does not recognise the RAID array (because it's compiled with out relevant drivers I assume).

I do have the source for the drivers, which would be fine if I was simply installing them on an existing system, however I need to install OS onto the RAID array.

Is there away I can 'slipstream' drivers onto a Ubuntu install disk - and access a hook in the installation process to call the shell scripts at the relevant times?

Alternatively can I insert the source and get the drivers to be compiled during installation (time is not an issue here)?

Or lastly, maybe I can build the drivers against a freshly installed system (connected to a different RAID controller) and then copy that pre-compiled driver on to the install disk.

If it makes any difference, I also want to completely automate the rest of the installation (auto-partition, standard user/pass, install extra deb packages).

What would be the best way to do this?

For those interested, the driver source is here:
[http://www.support-highpoint-tech.com/Main/rr2340/Linux/opensrc/rr2340-linux-src-v1.7-090925-0900.tar.gz]("http://www.support-highpoint-tech.com/Main/rr2340/Linux/opensrc/rr2340-linux-src-v1.7-090925-0900.tar.gz")

There are pre-compiled drivers available from this page (although none for 8.04.3 or 9.10):
[http://www.highpoint-tech.com/usa/bios_rr2340.htm]("http://www.highpoint-tech.com/usa/bios_rr2340.htm")

However I want to move away from having to depend on the manufacturer to provide pre-compiled drivers.

---

### Post by oxygen on 2009-12-01
A quick addition: The servers will have network access during installation, so if it's possible to pull the drivers over a network (somewhere in preseeding) then I can do that too.

---

### Post by DrDamnit on 2010-12-16
Did you ever figure this out? I just want to put the pre-comiled drivers into the setup disk. I don't mind compiling for the version of Ubuntu I am using, and then creating the disk with the .ko files in there already. Just need to know how to do it.

---

