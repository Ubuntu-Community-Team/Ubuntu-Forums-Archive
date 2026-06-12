---
title: "Virtualbox ver 2.1.0 incl OpenGL support"
date: 2008-12-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-12-17
>     * Support for hardware virtualization (VT-x and AMD-V) on Mac OS X hosts
    * Support for 64-bit guests on 32-bit host operating systems (experimental; see user manual, chapter 1.6, 64-bit guests, page 16)
    * Added support for Intel Nehalem virtualization enhancements (EPT and VPID; see user manual, chapter 1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10))
    * **Experimental 3D acceleration via OpenGL (see user manual, chapter 4.8, Hardware 3D acceleration (OpenGL), page 66)**
    * Experimental LsiLogic and BusLogic SCSI controllers (see user manual, chapter 5.1, Hard disk controllers: IDE, SATA (AHCI), SCSI, page 70)
    * Full VMDK/VHD support including snapshots (see user manual, chapter 5.2, Disk image &#64257;les (VDI, VMDK, VHD), page 72)
    * New NAT engine with signi&#64257;cantly better performance, reliability and ICMP echo (ping) support (bugs #1046, #2438, #2223, #1247)
    * New Host Interface Networking implementations for Windows and Linux hosts with easier setup (replaces TUN/TAP on Linux and manual bridging on Windows)

[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)




[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Testing...


EDIT not included.....:^o

> The hardware-accelerated OpenGL support is deemed experimental in VirtualBox 2.1. **OpenGL support is only exposed to Windows XP and Windows Vista 32-bit guests at this time,** but support for other platforms is expected in the future. Additionally, Sun Microsystems also has plans for supporting DirectX acceleration of guest operating systems in a future release. All the guest OS needs to do is install an OpenGL driver for what is recognized as a virtual hardware device that in turn communicates with the host's GPU. 

---

### Post by carml on 2008-12-17
These news are interesting,but I think it is better to wait some time,so the experimental features will be more tested and stable :p .

---

### Post by plun on 2008-12-17
> **carml said:**
> some time,so the experimental features willl be more tested :p .

I made an EDIT and Windows users test the experimental.....):P

Its a stable release so I file a upgrade request for Jaunty  !


EDIT already done
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/304859](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/304859)

.

---

### Post by Hershey on 2008-12-17
Should also note: 
> 
**Linux hosts.** There are a few problems when compiz is used as the host’s win-
dow manager, notably:
    – seamless mode does not work well (garbled screen display if no windows
      are open in the guest);
    – OpenGL guest acceleration (added with 2.1) is very slow.
If you experience these problems, you way want to try using a different window
manager, such as metacity.


Page 182 of the [User Manual]("http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf")

---

### Post by binbash on 2008-12-18
this is good news, i am gonna test opengl feature :D

---

### Post by sonofusion82 on 2008-12-22
yeah, somebody could probably create a support app/games wiki page like the support hardware or wine appdb page.
i'll try it once i get my new machine working.

---

### Post by james_xxx on 2008-12-22
I just upgraded to 2.1.0 today, after reading the article posted to Slashdot.

One thing that was recommended in the article, was also upgrading 'guest additions', after Virtualbox itself is upgraded.

How does one do that? I am running a 32-bit Vista Ultimate guest on a K/Ubuntu Intrepid host. I have poked around, but have not been able to figure out how to download the new guest additions. The new Vbox user's manual mentions running the installer again, but I am also unsure as to what that means.

---

### Post by dinxter on 2008-12-23
when running the windows virtual machine there should be 'devices->install guest additions' on the main menu at the top,

---

### Post by james_xxx on 2008-12-23
Yes, I already had guest additions installed before upgrading to 2.1.0. I am still using the same guest additions I was using before the upgrade. The article posted on Slashdot suggested that after upgrading Vbox, guest additions should also be upgraded.

How does one do this?

---

### Post by dinxter on 2008-12-23
think reinstalling from the menu should upgrade it automatically, you can always mount the /usr/share/virtualbox/VBoxGuestAdditions.iso image inside windows and do it that way too. thats where 2.1 installs the iso here anyway

---

### Post by dinxter on 2008-12-23
just to add, the guest addtions installer will should say 2.1 on it as it runs anyway but you can also see lots of info on what state your virtual machine is in including the version of additions you're running by using the command line and

VBoxManage guestproperty enumerate "NAME OF VIRTUAL MACHINE HERE"

all the GuestAdd components will show version 2.1 hopefully :)

---

