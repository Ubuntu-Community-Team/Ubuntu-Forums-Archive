---
title: "How do I install from a floppy disk?"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Donkor on 2007-09-22
I've got two computers:
[LIST]
[*]A computer with an unpartitioned hard drive
[*]A laptop with the ubuntu 7.04 i386 iso downloaded (running Windows XP SP2)
[/LIST]

For some reason I can't burn a CD with the laptop that will actually be booted from.  It burns it, but the md5 once it's burned doesn't check out (though the iso file itself does) and I get the dreaded "invalid or corrupt kernel image" while doing anything (checking the cd, trying to install) with the CD.  Whether it's bad discs (they're pretty old) or a bad drive, I'm not sure.  I can't do anything about it either way since I live in the boonies and there's nowhere nearby to buy them.  Waiting 4-6 weeks for the free cd to arrive isn't really an option either.  

The computer with the unpartitioned hard drive does have a floppy drive it can boot from.  It also has a cd burner, so if it's my laptop drive that's bad  and not the discs a distro that would give me cd burner/lynx capabilities would work. 

Any suggestions would be appreciated.

---

### Post by Pumalite on 2007-09-22
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by Gremlinzzz on 2007-09-22
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
maybe you can burn minimal 8mb
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Dark Hornet on 2007-09-22
just a quick question...when you burn the 386 image, are you sure you are burning the correct image for your computer?

---

### Post by Pumalite on 2007-09-22
386, 586, and 686 are OK for modern computers. Doing an md5sum on the iso is not to be forgotten.

---

### Post by Donkor on 2007-09-23
> **Pumalite said:**
> 386, 586, and 686 are OK for modern computers. Doing an md5sum on the iso is not to be forgotten.
Did it twice (as the OP says).  Once on the ISO file and once when I burned it.

The mini version didn't work and my NIC drivers don't appear to be on the list for solution 2.  I ended up doing a netboot (Using the Windows daemon) and got it to install, though it froze at 6% with the "Please wait" message for about 15 minutes.  It's at about 30% now though, so hopefully all goes well.  Thanks everybody.

For people who may be searching in the future and find this thread:
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot) shows how to set up the server on a Windows Machine

Replace the Breezy image with:
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/netboot.tar.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/netboot.tar.gz)
for i386 and extract it, otherwise your download will fail since breezy is no longer supported.

Netboot floppy:
[http://downloads.sourceforge.net/thinstation/network_boot_floppy%2Bcd%2Bhd_540.zip?modtime=1112785268&big_mirror=1](http://downloads.sourceforge.net/thinstation/network_boot_floppy%2Bcd%2Bhd_540.zip?modtime=1112785268&big_mirror=1)

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:

[http://www.len.ro/work/tools/life-to-an-old-i8000-1/view]("http://www.len.ro/work/tools/life-to-an-old-i8000-1/view")

---

