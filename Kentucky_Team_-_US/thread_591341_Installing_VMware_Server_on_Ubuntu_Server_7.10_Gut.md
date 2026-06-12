---
title: "Installing VMware Server on Ubuntu Server 7.10 Gutsy Gibon"
date: 2007-10-25
forum: Kentucky Team - US
---

### Post by bkingx on 2007-10-25
While there have been many How-To's regarding installing VMWare server on Gutsy, our experience was it was not on an Ubuntu Server platform.  When getting to the part of entering the serial numbers, we kept getting this error:

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

We determined that this must be an X issue, so we fixed the issue by installing xorg-dev (sudo aptitude install xorg-dev)

The entire process:
(thanks to this post for the initial setup steps: [http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/) )

***Installing VMWare Server on Ubuntu Server 7.10 (Gutsy Gibbon)***

1. Download VMware Server source from the [VMware website]("http://vmware.com/download/server/"). 
2. Download this [installer patch]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz"). ([source]("http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html") reference) 
3. Extract all the archives to some location on your system (tar -zxvf VMware-server* ; tar -zxvf vmware*) 
4. Ensure that you have some prerequisites installed in order to compile these sources (sudo aptitude install build-essential xorg-dev) 
5. Run sudo ./vmware-install.pl located within the vmware-server-* unpacked archive. 
6. Select all the default options *EXCEPT* do not compile the modules at this point. (Do you want this program to try to build the vmmon module for your system? NO) 
7. Run sudo ./runme.pl located within the vmware-any* archive. This will launch step 8. 
8. Select the default options and this time answer YES to compile the proper modules. 
9. Install the xinetd server (sudo aptitude install xinetd) 
10. Run vmware-server using the command vmware or via your Applications Menu.

---

### Post by MemoryDump on 2007-10-25
thanks for the info.. trying it now

---

