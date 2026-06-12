---
title: "Netboot via NFS not working for 12.04.3 desktop"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by jbristow on 2013-10-04
I have a working PXE server with many versions of Ubuntu, including 12.04, 13.04, Desktop, Server, etc.  

Today, I tried to add 12.04.3 Desktop.  
As usual, I copied /casper/initrd.lz and /casper/vmlinuz.efi to my TFTP  server.  I then copied the contents of the ISO to my nfs server.  

As I start booting, it gets to the section where it's trying to mount  the nfsroot to /cdrom, and it thows an error saying "Protocol not  supported".  

Does that mean that the kernel was complied without NFS support? 

I haven't done a pxe boot for any of the other versions of 12.04 since  the original release - I'll try and figure out where this feature was  removed.

---

### Post by jbristow on 2013-10-09
I verifed that everything works fine on 12.04.2 - do I need to submit a bug report for 12.04.3?

---

### Post by cracker on 2014-01-04
I'm experiencing the same problem, not sure what the specific cause is. I set up a PXE boot server with 12.04.3 desktop, and it stops and repeats "mount: Protocol not supported".

---

