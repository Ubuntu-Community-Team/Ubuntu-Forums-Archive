---
title: "Network Manager and vmxnet"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by elryno on 2007-05-31
I have installed Feisty 7.04 as a guest vm in a Windows XP vmware host.  I have followed the instructions for fixing the vmware tools install and have successfully installed the vmware tools.  My problem is that with the vmxnet module loaded (using given steps: /etc/init.d/networking stop, rmmod pcnet32, rmmod vmxnet, depmod -a, modprobe vmxnet, /etc/init.d/networking start), Network Manager shows "No network connection".  Even though it shows this, I DO have network connectivity.  When using the default module, pcnet32, everything works as it should (network connectivity and network manager status).  How do I get Network Manager to work properly with the better vmxnet module?

Details:
vmware workstation 5.5.3
ubuntu 7.04 with all latest updates (ie. network manager 0.6.4-6ubuntu7)
no wireless devices present
Network Manager - Wired Connection enabled - using dhcp

---

### Post by elryno on 2007-06-04
Does anybody else experience these problems, or am I the only one??  If I am the only one, I can understand the lack of help here.  However, if this is an issue that others experience also, I am surprised that the community has not even responded once.

---

### Post by cyberdork33 on 2007-06-08
I ran into this problem today on vmware fusion beta4 (Mac). I will post back if I can figure anything out.

well, after ugrading kernel, rebuilding vmware-tools and getting the vmxnet driver working, the system still loads the pcnet32 driver on bootup as well as vmxnet. pcnet32 seems to take over though, and that is what is used by network-manager. I tried blacklisting the pcnet32 module, but that didn't help, still loaded (huh?). the device works if i stop networking, rmmod pcnet32 and vmxnet, reload vmxnet, then start networking, but this of course doesn't fix network manager. Still working on it... I guess I could just go delete the pcnet32 module so that it CAN'T load, but that is kind of a cop-out.

EDIT:
Ok, well I think that pcnet32 is not actually loading, but is just an alias for the vmxnet module. See /etc/modprode.d/vmware-tools
I am not sure on this though, so I would appreciate someone's confirmation that that is even possible...

---

### Post by elryno on 2007-06-12
I would like to know what you have come up with.  I tried the #ubuntu channel on IRC to no avail.  They kept saying that if you are able to get network access, don't worry about the incorrect functioning of network manager.  This is not a satisfying answer to me.  In this configuration, any program that checks for network connectivity via network manager will think that network access is unavailable, even though it is available.  This is a frustrating problem.  I'm anxious to see if anyone can provide a solution.

---

### Post by cyberdork33 on 2007-06-21
as i said, the vmxnet module is loading normally on bootup if you follow the install instructions. it is just aliased as pcnet32. when you attempt to unload and reload, it breaks network manager, but there is no need to do this.

---

### Post by leo_m on 2007-09-19
Could not find /etc/modprode.d/vmware-tools though /etc/modprode.d/ exists.
Also, how do I know if the vmxnet module is presently handling eth0 or pcnet32 is handling it?

After installation of vmware-tools and modifications by me, the /etc/modules.conf is as follows:

```
 # Added by VMware Tools
alias eth0 vmxnet
probeall vmnics vmxnet pcnet32
alias char-major-14 es1371
```


Before modifications by me but after installation of vmware-tools, the modules.conf was like:

```
 # Added by VMware Tools
alias eth0 vmnics
probeall vmnics vmxnet pcnet32
alias char-major-14 es1371
```


And before vmware-tools, it (/etc/modules.conf) was empty.

So, back to the question, how do I make sure vmxnet module is loaded and not pcnet32?

Also, is there any way to get the vmhgfs module working under Ubuntu 7.04 (Feisty Fawn)?

---

