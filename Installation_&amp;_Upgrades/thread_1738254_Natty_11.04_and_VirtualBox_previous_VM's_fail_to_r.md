---
title: "Natty 11.04 and VirtualBox: previous VM's fail to run"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by Yakiman66 on 2011-04-24
VirtualBox 4, non-OSE:
Worked under Maverick 10.10 with kernel 2.6.35-25.
Upgraded machine (64-bit Dell Zino 410) to Natty beta 11.04.
Upgraded VirtualBox from its website to the Natty version.
My VM's, Win7 and WinXP, both fail because they apparently want to see the older kernel and it is no longer the running kernel.
[B]Is this supposed to happen? Is there a workaround short of
a. reinstalling my whole Linux environment and going back to 10.10
b. reinstalling my VM's so they get installed under the same kernel the host is now running?[/B]

**Here is what I get when I do what the error message suggests:**
root@Zino410:~# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxhost/4.0.2/source/dkms.conf does not represent
a valid dkms.conf file.
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxhost/3.2.10/source/dkms.conf does not represent
a valid dkms.conf file.
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.35-25-generic cannot be found at
/lib/modules/2.6.35-25-generic/build or /lib/modules/2.6.35-25-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
root@Zino410:~# 

I can't find the older kernel headers anywhere on my filesystem, and can't seem to install the older ones using apt.

Thanks for any and all help!

Yakiman66

---

### Post by Hedgehog1 on 2011-04-24
You will need to install the 4.0.6 version of Virtual Box for Natty (this has only been available for a few days): [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

I got a 'Dirty Install' warning, but it did install and works correctly on natty:

[IMG]http://img546.imageshack.us/img546/3093/vboxinnatty.png[/IMG]

***The Hedge***

:KS

---

### Post by birdy on 2011-05-02
I had the same error, and found that I needed to remove all VB related stuff in /var/lib/dkms. So, I removed 

varlist.txt
vboxdrv
vboxhost
vboxnetadp
vboxnetflt

and then the installation of 4.0.6 from the Oracle repo works fine.

---

