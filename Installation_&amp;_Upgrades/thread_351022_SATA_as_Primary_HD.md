---
title: "SATA as Primary HD"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by miseljt on 2007-02-01
Actually, no question here, this is what I did, in case anyone ever wants to try. I'm sure there is an easier way, but this is my set up:

320 GB Western Digital SATA (Primary)
60 GB Western Digital IDE
20 GB Maxtor IDE

For a while, I was having issues getting the Grub to be installed on my SATA, even after I installed Windows on that HD. It obviously already had a boot sector as I was able to unhook both IDE drives and boot to Windows. I ended up just leaving the other two HDs unhooked and going through the live cd. 

The way I set up my partitions is:

50GB NTFS (SATA)
25GB ext3 - root (SATA)
2GB ext3 - swap (SATA)
Whatever's left ext3 - /home (SATA)

60GB ext3 Vbox images (IDE0 Master)
20GB ext3 Haven't decided (IDE0 Slave)

There were more problems involved which led me to unhooking them during install because I had a Windows partition on the 60GB and an Edgy install on my 20GB. All of which were competing w/ the SATA boot sector. Hope this helps anyone.

---

