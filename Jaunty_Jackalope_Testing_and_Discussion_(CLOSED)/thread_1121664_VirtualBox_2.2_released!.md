---
title: "VirtualBox 2.2 released!"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-04-10
This version is a major update. The following major new features were added:
> 
    * OVF (Open Virtualization Format) appliance import and export (see chapter 3.8, Importing and exporting virtual machines, User Manual page 55 )
    * Host-only networking mode (see chapter 6.7, Host-only networking, User Manual page 88)
    * Hypervisor optimizations with signi&#64257;cant performance gains for high context switching rates
    * Raised the memory limit for VMs on 64-bit hosts to 16GB
    * VT-x/AMD-V are enabled by default for newly created virtual machines
    * USB (OHCI & EHCI) is enabled by default for newly created virtual machines (Qt GUI only)
    * Experimental USB support for OpenSolaris hosts
    * Shared folders for Solaris and OpenSolaris guests
    * OpenGL 3D acceleration for Linux and Solaris guests (see chapter 4.8, Hardware 3D acceleration (OpenGL), User Manual page 70)
    * Added C API in addition to C++, Java, Python and Web Services 


[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

Hope it makes it into Jaunty..

---

### Post by go7Ul1ai on 2009-04-10
Great! But I doubt it will make it into Jaunty now as it's way past feature freeze and this release isn't really a criticle bug fix release.

---

### Post by eyelessfade on 2009-04-10
Although I really would have seen it in jaunty it won't be in before jaunty +1. So we have to rely on a ppa I think :)

---

### Post by xebian on 2009-04-10
> **eyelessfade said:**
> Although I really would have seen it in jaunty it won't be in before jaunty +1. So we have to rely on a ppa I think :)

Direct from VirtualBox. ):P

---

### Post by olskar on 2009-04-10
Correct me if I'm wrong, but the versions in Ubuntu repos is only OSE versions? E.g they do not have support for USB and such, for that you have to download from VirtualBox or add their repo?

---

### Post by feelshift on 2009-04-10
> **olskar said:**
> Correct me if I'm wrong, but the versions in Ubuntu repos is only OSE versions? E.g they do not have support for USB and such, for that you have to download from VirtualBox or add their repo?
I am asking myself the same question. Can anyone make things clear? How different are the version from the repository and the one from their website?

---

### Post by Cenotaph on 2009-04-10
Yes, Ubuntu only has OSE afaik. But you can download a .deb for intrepid and jaunty (not OSE) from Virtualbox website, so its really not that important what version is in the ubuntu repos.

At least for me it isn't

---

### Post by KhaaL on 2009-04-10
VB 2.2 has its own repository anyway (deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free)

has anyone tried the 3d acceleration and got it working well?

---

### Post by FuturePilot on 2009-04-10
> **KhaaL said:**
> VB 2.2 has its own repository anyway (deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free)

has anyone tried the 3d acceleration and got it working well?

Compiz works inside VirtualBox. I've tried it and it's amazing.

---

### Post by Therion on 2009-04-10
> **feelshift said:**
> I... How different are the version from the repository and the one from their website?
VirtualBox website has this to say about the NON-Open Source version, the one that uses the PUEL (Personal Use/Evaluation License).  This PUEL version is not in the offical Ubuntu repo, you have to download it from the VirtualBox website, or add the VB repo yourself to get it:

> The following list shows the enterprise features that are *only present in the closed-source edition* [Emphasis mine]. 
Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

    * Serial ATA controller 

    Like a real SATA controller, VirtualBox&#8217;s virtual SATA controller operates faster and also consumes less CPU resources than the virtual IDE controller. Also, this allows you to connect more than three virtual hard disks to the machine.

---

### Post by feelshift on 2009-04-10
Thanks for clarifying things out here :popcorn:

---

### Post by binbash on 2009-04-10
I also tested compiz and it works fine, however my cpu is around %99 even i disabled most features (3d , usb support etc)

---

### Post by Seventh Reign on 2009-04-10
woohoo Post 100

Oh yea .. The only differences I've been able to notice are the new "Press F12" screen.  I heard XP was supposed to boot faster .. mine boots slower :-(

---

