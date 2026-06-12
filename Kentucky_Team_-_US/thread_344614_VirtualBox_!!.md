---
title: "VirtualBox !!"
date: 2007-01-23
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-01-23
This VirtualBox sounds awesome!  Running another OS such as Winblows inside Ubuntu for running applications Ubuntu (or WINE) doesn't support.  I do have to question why it doesn't exist in the Universe binary repository though.  I've been warned that applications not in this repository poses security risks, and possible system instability.

Any thoughts on this before I install this?

---

### Post by etank on 2007-01-23
I am not sure what it takes to get something in the repos. It is a good idea not to install something unless you trust where it came from or have looked at the code yourself. That being said I have been running it on two different machines and it seems rock solid so far. I think this one is safe to go with.

---

### Post by garybrlow on 2007-01-23
Apparently its new. They just open sourced their product this January 15, 2007. Its similar to Xen and VMWARE. They basically are the same except that It doesn't have the virtual appliance infrastructure available in VMWARE. Am not really sure if VMWARE is truly open source but some of it is it think. Am not really sure which is easier to install though but Virtual Box has pre-built debs under limited license. I think VMWARE has more advantages in the sense that out of the OSes you install on VMWARE Sever you can create Virtual Appliances that you can somewhat mount and unmount to put it simply via VMPLAYER to save you from installing the said OS again. Just mount it and your good to go to. With Xen am not familar with, it but it also has its advantages i suppose. Virtualization technology is resource hungry, you have to have a powerful machine and lots of memory to fill both the requirements of the Host OS and guest OS. If you just plan to play games on it will be somewhat slow and since it the Guest OS must work with the Host OS,  you'll be limited to to whatever works in the Host OS causing limited OS functionality. If you want full functionality, you're better off dual booting 2 operating systems. Just my 2 cents anyways, but do try it and tell us how it goes. :)

Cheers!

GaryBrlow :P

---

### Post by JarG0n on 2007-01-23
Thanks!  Some of the terminology is a bit new to me.  I hope they have good documentation. :confused:

I only have 256MB of RAM right now, so it looks like I won't be using this until I upgrade to at least 1GB.

---

### Post by etank on 2007-01-23
Yeah you are really going to want more ram than that. The docs for virtualbox seem to be pretty good but so are the docs for VMware. I have 512Mb in my box and it seems to run ok with giving the vm about 192Mb. Much more than that and things start to slow down a bit.

---

### Post by jkeyes0 on 2007-01-26
Wow. This is exactly what I've been wanting to do here at work for a year now. I have to have a copy of Windows on my workstation to deal with Domain issues (resetting user passwords, adding/removing systems from the domain, etc.), but I've always thought it would be nice to have windows running on a Linux underside.

---

### Post by El Viejo Lobo on 2007-06-02
I have Virtualbox on Ubnutu 7.04 My machine is not that strong so I try to have it light and installed Windows 98.  Some thing is wrong, it is slow slow slow. Can I get a tip how to make run?

---

