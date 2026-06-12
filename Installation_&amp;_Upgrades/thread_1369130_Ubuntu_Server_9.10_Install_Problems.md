---
title: "Ubuntu Server 9.10 Install Problems"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by reg.ottawa on 2009-12-31
First time Ubuntu installer here. :confused:

1) trying to install Ubuntu Server 9.10 64-bit with VMware player onto my DELL XPS Studio desktop.  The desktop is a Intel i7 CPU with a 64bit Windows7 operating system.  It is a new machine.

2) Using Easy Install to install Ubuntu. Install from the ubuntu-9.10-server-amd64.iso on my desktop.

3) Seems to progress nicely until... I get a control panel asking me " To run a command as adminstrator (user "root"), use "sudi <command>".  There was also a ACPI: I/O resource piix4_smbus conflicts with ACPI region SMB_

My question is how do I proceed ?  I was expecting the nice graphical interface I saw on the youtube training videos.

Any help with this would be greatly appreciated... 

Reg

---

### Post by reg.ottawa on 2009-12-31
got some local help... 2 commands in the command line did the fix.
posting in case anyone else runs into this.

* sudo apt-get install ubuntu-desktop  
this adds the GUI interface

* sudo /sbin/shutdown -r now
this restarts the virtual machine and the Ubuntu Graphics appear

---

