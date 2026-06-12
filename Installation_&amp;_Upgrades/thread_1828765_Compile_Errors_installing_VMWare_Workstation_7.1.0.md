---
title: "Compile Errors installing VMWare Workstation 7.1.0 under Ubuntu 11.04"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by controlfreak007 on 2011-08-19
I am pretty much a newbie to  Linux.  I have played around with Fedora for a few years and recently  switched to Ubuntu.  I am installing VMWare Workstation version 7.1.0 from a retail  packaged CD.  When I attempt to install VMWare Workstation and  VMWare Player I get the following error:
 
Aug 15 16:24:54.826: app-3078788800| Your GCC version: 4.5
Aug 15 16:24:54.837: app-3078788800| Your GCC version: 4.5
Aug 15 16:24:54.889: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:54.895: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:54.902: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:54.905: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:54.907: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:55.078: app-3078788800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 15 16:24:55.079: app-3078788800| Building module vmmon.
Aug 15 16:24:55.079: app-3078788800| Extracting the sources of the vmmon module.
Aug  15 16:24:55.091: app-3078788800| Building module with command:  /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build  SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-10-generic/build/include  CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Aug 15 16:24:56.163: app-3078788800| Failed to compile module vmmon!
 
I tried installing the patch for kernal 2.6.38-8 found here - [http://communities.vmware.com/thread/312086](http://communities.vmware.com/thread/312086) - but it did not resolve the issue.
 
Has anyone run across this issue and if so have you found a work-around?  Is there a patch for kernal 2.6.38-10?


I also found this posting for the same problem:

 
     [http://ubuntuforums.org/showthread.php?t=1825707&highlight=VMware+7+2.6.38-10+kernel](http://ubuntuforums.org/showthread.php?t=1825707&highlight=VMware+7+2.6.38-10+kernel)
 
I followed the following instructions as advised in the post  .  .  .
 
sudo apt-get update
 
 sudo apt-get install make
 
 sudo apt-get install gcc
 
 Then enter: 
 uname -r
 
 My kernel was: 2.6.38-10-generic
 
 sudo apt-get install build-essential linux-headers-**2.6.38-10-generic**
 
 Now run the vmware-install.pl script.
 
Everything  ran without error. However, I continue to get the same error.  



Another  post suggested uninstalliung and reinstalling the software, but this had  no affect either.  
 
Another post suggested that after running the above update to them run the /usr/bin/vmware-config.pl script.  However  I do not seem to have the vmware-config.pl in my /usr/bin directory.  I  checked the various VMWARE directories in /etc and the /tmp/vmware-root  directories but no vmware-config.pl
 
Any suggestions?  .   .   . 



Thanks in advance!
 
-controlfreak007

---

### Post by ViRMiN on 2011-08-20
I can't remember which version of VMware Workstation supports Ubuntu 11.04 (could be 7.1.3?) but, you'd be best to download the latest release and see if that helps.

---

### Post by controlfreak007 on 2011-08-22
That worked.  I deleted my current install and downloaded 7.1.4 from VMWare and installed the bundle.  Everything works like a champ.  

Thank you for your help ViRMiN!!!

---

