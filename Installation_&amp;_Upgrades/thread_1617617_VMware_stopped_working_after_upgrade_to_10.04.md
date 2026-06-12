---
title: "VMware stopped working after upgrade to 10.04"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by myurkiw on 2010-11-09
I upgraded from 9.10 to 10.04 and my VMware stopped working.  I got a message to recompile into the kernel.  I followed the prompts and it was unsuccessful.  I tried to uninstall and reinstall VMware getting the same error.  See below an extract from the log file.  

----------------------------------
Before you can run VMware, serveral moduels must be compiled and loaded into the running kernel.  

stopped vmware services - ok
compiling
 - virtual machine monitor - ok
 - virtual network device - warning
 - vmware blocking filesystem - ok
 - virtual maching communication interface - ok
 - vmci sockets - ok
starting vmware services  -  error
    Unable to start services
See log file /tmp/vmware-root/setup-9590.log for details

-----------------------------------------
Error in log:
Nov 09 07:59:34.560: app-3077531328| Trying to find a suitable PBM set for kernel 2.6.32-25-generic.
Nov 09 07:59:34.560: app-3077531328| Building module vmnet.
Nov 09 07:59:34.560: app-3077531328| Extracting the sources of the vmnet module.
Nov 09 07:59:34.576: app-3077531328| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-25-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Nov 09 07:59:36.257: app-3077531328| Failed to compile module vmnet!

---

### Post by cybergnome on 2010-11-09
Any reason you use VMWare instead of Virtual Box OSE which is supported by Ubuntu?  Yes, the virtual machines ARE kernel specific.  :confused:

---

### Post by myurkiw on 2010-11-10
VMware only because that is what we use at work.  I installed Virtual Box and am trying that now.  It is working fine except that I can't get it to full screen.  I changed the windows display property between 800x600 and 1024x768.  Anything over the 800x600 has scroll bars.  None of them go full screen.  It does seem faster and cleaner than VMware other than that and I can connect to my work VPN, which is the only reason for it.  But that still doesn't explain why I couldn't uninstall and reinstall VMware.  Thanks for the input.

---

### Post by myurkiw on 2010-11-10
Never mind.  I read up and found Guest Additions.  Now full screen and mouse is working great.  I think I will stick with Virtual Box.  Thanks.

---

### Post by lechien73 on 2010-11-10
You'll find that 10.10 has the same problem with VMWare. I blogged about the solution here:

[http://blog.mattrudge.net/2010/10/11/vmware-player-on-ubuntu-10-10-maverick-meerkat/](http://blog.mattrudge.net/2010/10/11/vmware-player-on-ubuntu-10-10-maverick-meerkat/)

Hope this helps :)

---

### Post by myurkiw on 2010-11-10
Thanks for the info.  great blog.

---

