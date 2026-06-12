---
title: "VMware tools problem with ubuntu 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tudorlivada on 2008-04-27
Hello,

I am using vmware 5.5.1 on a Windows XP sp2. I've installed ubuntu 8.04 and I've tried to install the vmware tools. The installation works smoothly but when it comes to configuration, I need to write the path to the directory that contains the C headers. In my case that path could be '/usr/src/linux-headers-2.6.24-16/include' or '/usr/src/linux-headers-2.6.24-16-generic/include' I've tried both of them and i get the same error. This is what i get:

The installation of VMware Tools 5.5.1 build-19175 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] yes


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for 
your system (you need to have a C compiler installed on your system)? [yes] tudx@tudx-desktop:~/Desktop/vmware-tools-distrib$ 

And it says something about my C compiler. Someone suggested to use: sudo apt-get install build essential and sudo apt-get install linux-headers-`uname -r`. But still, it doesn't work. What I ask is a step by step installation (presuming that I have a problem with C and it needs to be reinstalled or smth.) If my request is annoying, I apologize, but I am a beginner. Thank you in advance.

---

### Post by tudorlivada on 2008-04-28
Could it be vmware's fault?

---

### Post by trmentry on 2008-04-29
I'm having the same issue getting the tools to install on 8.04.  

I'm trying to install vmwaretools-3.0.2-52542.  This is on a guest running on a ESX 3.0 server.  

I didn't have issues getting the tools to install on 7.10.  

I did install build-essential and linux-headers-`uname -r` before hand.

---

### Post by tudorlivada on 2008-04-29
I had upgraded to vmware workstation 6. And after that worked. Probably was a bug of my old version of vmware.

---

