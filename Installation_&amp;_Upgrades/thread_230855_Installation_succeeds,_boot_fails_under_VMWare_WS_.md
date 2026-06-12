---
title: "Installation succeeds, boot fails under VMWare WS 5.5.1"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by Roland of Gilead on 2006-08-06
After hearing much todo about Ubuntu, I decided I'd give it a look-see and pulled down the 6.06 Server ISO image.

My host machine is an IBM Thinkpad T41 with 2GB RAM running RHEL 4 Workstation and VMWare Workstation 5.5.1.

I created a new guest VM with 256MB RAM, 8GB SCSI HD, IDE CDROM, NAT network...selected Ubuntu as the guest OS type, chose the ISO image file as the device for the CDROM, and powered it up.

As expected, I got a text-mode installation sequence that walked through what I would consider the "normal" data gathering screens.  The installation completed within about 10 minutes, and I was prompted to reboot.  I disconnected the CDROM device in VMWare and set it back to /dev/hdc (the physical device on the host machine), and hit Enter to reboot.

The boot looked normal, except it hangs here.  Permanently.

[IMG]http://christopher.gotdns.org/images/ubuntu.jpg[/IMG]


After some research, I came across several threads that appeared to have similar issues, so I wiped out the VM, made some changes and began again.  This time, I gave it 512MB RAM and switched to  an 8GB IDE virtual HD.  Again, the installation proceeded normally, and again, the boot process hung in the same place.

Another series of threads seemed to indicate some issues with ACPI, so I tried disabling it during the boot process.  Same result:

[IMG]http://christopher.gotdns.org/images/ubuntu2.jpg[/IMG]


I've also tried adding the "noapic" and "nolapic" directives to the boot command string, as well as removing the "splash" and "quiet" directives.  No effect...boot still hangs at this point.

Anyone have any ideas on how to proceed from here?

---

### Post by Roland of Gilead on 2006-08-07
Interestingly enough, I found the answer on the VMWare forums.  Seems that several brands of notebook PCs require the 686 kernel to be installed in order to function properly.

[http://www.vmware.com/community/thread.jspa?messageID=448392&#448392](http://www.vmware.com/community/thread.jspa?messageID=448392&#448392)

---

