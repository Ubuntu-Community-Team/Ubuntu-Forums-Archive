---
title: "Moved old external NAS drives internally - now not mounting automatically"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by dave132 on 2014-07-27
Hey all,

Just got back into Linux after a long hiatus. I've set up a file/NAS/Media server on Ubuntu server LTS 14.04. Install went ok on the 64GB SSD, so then I added 3 other HDs that where all on my NAS323 running ALT-F firmware and NOT raided but instead JBOD (also installed Lubuntu for a GUI, and PLEX). Now when ever I reboot, I need to manually (using Disk Manager) mount the 3 HDs. Tried using automount and that still doesn't work. Looking at the fstab I don't see the other drives listed, even after using Disk Manager, but the settings in DM seem to be utilizing the UUID (which appear to be LONG LONG LONG strings), when they mount the HDs.  In DM again I see the HDs have 3 partitions SWAP, Unknown/log??, main.  All the drives are EXT4 formatted.

As a second question (which I can create a new thread if needed)...any recommended remote desktop/control apps? I tried a tightvnc install and any windows client trying to connect get a forcefully rejected error.

Help?!

Cheers,

Dave

---

### Post by tgalati4 on 2014-07-27
Check your BIOS and motherboard documentation to be sure your machine can handle the drives.  It's possible that they need a "legacy" mode enabled or a change in the SATA settings to be able to see all drives.  You would think this would be a plug-and-play situation, but obviously, something is not working.  

Check your log files in /var/log and pay attention to any errors related to the disks.  Post only those errors.

For your second question, I use ssh with X-forwarding to bring up a remote desktop.

```
ssh -2 -Y username@machinename gnome-panel
```

Make sure your machinename is listed in /etc/hosts with the correct IP address.  Use of static IP's is helpful for both machines.

---

### Post by dave132 on 2014-07-27
Hello tgalati4,

The board is brand new and has an extra pcie to sata board.  The bios sees all the drives ok and the drives work just fine when I manually mount them in Disk Manager, so I don't think it is a physical or driver issue per se.  I'll take a peak at the /var/logs when I get a chance again, but i think it will come down to an issue with missing fstabs. Could it be a permissions issue as the drives where created on another system or permissions writing into fstab?

> **tgalati4 said:**
> Check your BIOS and motherboard documentation to be sure your machine can handle the drives.  It's possible that they need a "legacy" mode enabled or a change in the SATA settings to be able to see all drives.  You would think this would be a plug-and-play situation, but obviously, something is not working.  

Check your log files in /var/log and pay attention to any errors related to the disks.  Post only those errors.

For your second question, I use ssh with X-forwarding to bring up a remote desktop.

```
ssh -2 -Y username@machinename gnome-panel
```

Make sure your machinename is listed in /etc/hosts with the correct IP address.  Use of static IP's is helpful for both machines.

---

