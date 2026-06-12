---
title: "VMWare Tools &amp; VMware server 1.0.2 problem"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by REy_ on 2007-04-28
I have installed VMWare server and VMWare tools both 1.0.2 from the feisty repos but cannot figure out how to get VMWare server to recognize that VMWare tools are installed. I keep getting the You do not have VMware Tools installed warning at the bottom of the server console, and everything seems sluggish. Any thoughts?

Thanks in Advance,
  REy

---

### Post by REy_ on 2007-04-29
Not that anyone even bothered to answer, but I had a misconception about what exactly VMware Tools were, they are meant for the Guest OS (virtual machine) and not the Host OS. I had to download Workstation Beta 6 in order to extract the windows.ISO so that I could install VMware tools. Pretty straight forward.

-----------------------------------------
Here's the link that finally helped and the information from it:

[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

 Installing VMware Tools with VMware Player
As other sites have demonstrated, it is possible to create a VMware disk image using free tools and install a full-fledged virtual operating system using the free VMware Player. However, VMware Player does not provide VMware Tools, a set of programs that considerably improve VMware performance.

The following procedure shows how to extract and install the VMware Tools image from the VMware Workstation "tarball" (.tar.gz file). In this example, my guest system is Windows XP Professional, and my host system is Fedora Core 4.

1. Download the latest "Archived Version" of VMware Workstation in ".tar.gz" format at [http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/). You do not need to be registered nor have a VMware Workstation license key to download this version.

Example:
wget [http://download3.vmware.com/software/wkst/VMware-workstation-5.5.0-18463.tar.gz](http://download3.vmware.com/software/wkst/VMware-workstation-5.5.0-18463.tar.gz)

2. Locate and extract the windows.iso VMware Tools image from the tarball.

Locate the windows.iso file (example):
$ tar ztvf VMware-workstation-5.5.0-18463.tar.gz | grep windows.iso
vmware-distrib/lib/isoimages/windows.iso

Extract the windows.iso file (example):
$ tar zxvf VMware-workstation-5.5.0-18463.tar.gz vmware-distrib/lib/isoimages/windows.iso

3. Mount the windows.iso file as a loopback file system, and either share the loopback file system with Samba, or copy the VMware Tools files to a location accessible by your guest system.

$ mkdir /tmp/vmware_tools
# mount -o loop vmware-distrib/lib/isoimages/windows.iso /tmp/vmware_tools

4. In your guest system, run setup.exe from the VMware Tools directory.

---

