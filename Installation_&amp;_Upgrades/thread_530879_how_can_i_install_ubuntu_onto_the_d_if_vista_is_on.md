---
title: "how can i install ubuntu onto the d:\ if vista is on c:\?"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by nweissma on 2007-08-20
please consider these circumstances: an intel processor (e6400) and motherboard (DG965RY) ... c:\250GB hdd ... d:\500GB hdd ... vista-32 as the exclusive resident on c:\ (as far as i know, vista knows nothing of d:\). 
 
i want to install ubuntu and unix on the currently-vacant d:\, and be able to switch between the 3 os's. 
 
 
 
can  i install ubuntu and unix on d:\, and either boot from d:\ or switch to d:\ ?


can (the $free) vmware.com be of use to me?

---

### Post by JReagan1990 on 2007-08-21
First off, your d:/ drive is a Microsoft formatted one, and I believe that you will have to format it (and create swap, ext3, etc.) to install Ubuntu.  

VMWare is a great option, and I recommend using the VMWare Server edition, which has options to create Ubuntu images on which you can install Ubuntu or any other flavor of your choice.  I think you'll find that VMWare is the far more safe and easier to use, rather than risking your harddrive and running into those "invalid partition table" errors.

Hope this helps!

---

### Post by nweissma on 2007-08-22
> **JReagan1990 said:**
> First off, your d:/ drive is a Microsoft formatted one, and I believe that you will have to format it (and create swap, ext3, etc.) to install Ubuntu.  

VMWare is a great option, and I recommend using the VMWare Server edition, which has options to create Ubuntu images on which you can install Ubuntu or any other flavor of your choice.  I think you'll find that VMWare is the far more safe and easier to use, rather than risking your harddrive and running into those "invalid partition table" errors.

Hope this helps!
sorry, but you lost me: what do you mean that d: is ms formatted, and what are the consequences of this?

i have seen the vmware site, and it seems hostile to a newbie. i will need a bit of hand-holding ["create swap," "ext3", "etc." are meaningless jargon to me] and vmare does not seem like the type!

you are the third person to warn me about "risking my hdd" (i assume that you mean by dual-boot) - but several people have recommended dual boot as an option.

---

### Post by merlinus on 2007-08-22
You can install ubuntu onto your second hdd with no problems, and it will not interfere with vista, especially since that is on another hdd.

You can boot with the live cd and try it out before deciding whether or not to install.  It will partition the disk automatically, if you so desire, or you can specify the size of the space it will use.

By unix, what particular operating system are you referring to?

-merlin

---

### Post by donteatsoap7 on 2007-08-22
I need to do this also.
I have Vista on C and I want ubuntu on D.

So...how do I do it?

---

### Post by merlinus on 2007-08-22
> **donteatsoap7 said:**
> I need to do this also.
I have Vista on C and I want ubuntu on D.

So...how do I do it?

Is D a separate hdd?  If so, boot from the ubuntu live cd.  When up-and-running, click the Install icon at the top-left of the desktop.

When you get to the partitioning menu, choose guided and use your second hdd.

If not, then you will have to shrink your vista partition to make room for ubuntu using vista's disk manager.

-merlin

---

### Post by mrfelker on 2007-08-22
> **nweissma said:**
> please consider these circumstances: an intel processor (e6400) and motherboard (DG965RY) ... c:\250GB hdd ... d:\500GB hdd ... vista-32 as the exclusive resident on c:\ (as far as i know, vista knows nothing of d:\). 
 
i want to install ubuntu and unix on the currently-vacant d:\, and be able to switch between the 3 os's. 
 
 
 
can  i install ubuntu and unix on d:\, and either boot from d:\ or switch to d:\ ?


can (the $free) vmware.com be of use to me?

Yes to the installation questions.  Linux doesn't use drive letters anyway.  Hard drives are devices and live in the /dev folder.  For example the first HD drive is /dev/hda the secpmd /dev/hdb etc.  Use the same except sda if you are using SCSI disks - or SATA disks which linux thinks are SCSI.

VMware is NOT free.  You can get a free evaluation copy but if you want to avoid a program expiration you need to pay $199 I think.  Windows and Linux versions are available.  But I don't think this what you want.  What is free is VMware Player - but it will only boot - not create existing Virtual Machines.

---

### Post by maybeway36 on 2007-08-23
[VirtualBox]("http://www.virtualbox.org") is most definitely free.

---

### Post by bulldog060 on 2007-08-23
> **mrfelker said:**
> 
VMware is NOT free.  You can get a free evaluation copy but if you want to avoid a program expiration you need to pay $199 I think.  Windows and Linux versions are available.  But I don't think this what you want.  What is free is VMware Player - but it will only boot - not create existing Virtual Machines.

....VMWare Server IS free and it allows you to create New Virtual Machines

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

~ron

---

### Post by nweissma on 2007-08-28
> **merlinus said:**
> Is D a separate hdd?  If so, boot from the ubuntu live cd.hope you don't get ticked at these questions... yes, d is separate ..what is a "live cd"? why can't i just download rather than use the cd?

is there anyone in new york ciity?

---

### Post by merlinus on 2007-08-28
You download an .iso file, and burn it to a cd as a disk image, not a data disk.

You then boot your computer from the cd, and get a working version of ubuntu so you can play around with it and see if it will work with your hardware before deciding to install.

If you wish to install, then it is a simple matter of clicking the Install icon on the desktop.

-merlin

---

