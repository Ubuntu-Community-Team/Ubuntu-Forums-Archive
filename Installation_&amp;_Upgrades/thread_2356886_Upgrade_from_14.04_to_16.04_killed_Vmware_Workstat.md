---
title: "Upgrade from 14.04 to 16.04 killed Vmware Workstation 12: Guest OS can't open. ."
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by ahears on 2017-03-27
I can't get the VMware Workstation 12 to open any guest. If I create a new guest, clone a guest, or open a guest in which I already have I always get the following error:

> 
Could not open paging file for 2048 MB: "Permission denied".
An error occurred while restoring the virtual machine state from file "/media/nemisis/VM-Data/vmware/Windows 10 Professional Build 10240 32-bit/Windows 10 Professional Build 10240 32-bit-Snapshot16.vmsn".
An error caused the restore operation to fail. Cancel the restore operation and correct the error, or discard the snapshot's state and power off.  The saved snapshot will not be affected.


and

> 
Could not open paging file for 2048 MB: "Permission denied".
Failed to allocate main memory.
**Module 'MainMem' power on failed**.
Failed to start the virtual machine.


Output of: 'cat /tmp/vmware-USER/vmware-ui-5352.log': [https://paste.ubuntu.com/24264897/](https://paste.ubuntu.com/24264897/)

I don't know if this has anything to do with some warnings I get at boot which are:

> 
Failed to load Kernel Modules:

systemctl status systemd-modules-load.service
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-03-27 17:03:33 PDT; 2h 14min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 437 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 437 (code=exited, status=1/FAILURE)


Mar 27 17:03:33 Linux-PC systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Mar 27 17:03:33 Linux-PC systemd[1]: Failed to start Load Kernel Modules.
Mar 27 17:03:33 Linux-PC systemd[1]: systemd-modules-load.service: Unit entered failed state.
Mar 27 17:03:33 Linux-PC systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.



I think this is an Ubuntu question because it seems to be a problem with the OS and not with VMware. I can open the guests (all of them) with the VMware Player and they open normally, but not with the VMWare Workstation 12 application. It seems like some kind of Hardware Abstraction Layer problem, that started after I upgraded from Ubuntu 14.04 to 16.04. Also note that I have uninstalled VMware completely, rebooted, cleared all cache files, and reinstalled, and am still stuck with the same problem.

Any help would be appreciated, thank you:)

---

### Post by TheFu on 2017-03-27
[https://pubs.vmware.com/Release_Notes/en/workstation/12pro/workstation-1251-release-notes.html](https://pubs.vmware.com/Release_Notes/en/workstation/12pro/workstation-1251-release-notes.html) might be helpful.
See the *known issues* section. 

Another option is to consider using the Linux-centric KVM+QEMU hypervisor. It is extremely excellent.

---

### Post by Keith_Helms on 2017-03-28
16.04 uses a newer Linux kernel - 4.4.   Does VMWare workstation 12 support that kernel?  You might need to download a newer version of workstation or you might need to reinstall 12 again.

I upgraded to the 16.04 HWE last week and my VMWare Player 12.1.1 would not work on the new 4.8 kernel.   I downloaded VMWare Player 12.5.4 and installed it and it works fine.

---

### Post by ahears on 2017-03-28
I have fully researched everything from this point here -up- on this post. I manually removed the old install according to this link here: "https://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=38'\", rebooted, reinstalled again, still nothing. I will look into the 16.04 HWE update more to see if this might fix the problem but they are vague as to what exactly the benefit of the HWE kernel actually is, that isn't already in the standard point releases when they come out. Specifically what is the improvement, what hardware, or how it affects the systems currently running a fully updated LTS system like mine, etc... Until then, any other ideas?

---

### Post by Keith_Helms on 2017-03-29
HWE justs takes the kernel and graphics drivers from newer releases of Ubuntu and makes them available in the LTS releases.  Currently, Ubuntu 16.04.2, which uses the HWE packages, uses the Linux 4.8 kernel from the 16.10 release in place of the 4.4 kernel that 16.04 and 16.04.1 use.  I didn't mean to imply that HWE might fix your VMWare problem.  I was just giving an example where going to a newer kernel also required me to use a newer version of VMWare Player.

Edit: Oh, and the reason behind HWE is so that the LTS versions can support new hardware that wasn't out when that LTS version was originally released.  In the case of VMWare where the software itself has to catch up with new Linux kernels, there is no advantage to moving to leading edge kernels and graphics.

---

