---
title: "Cant install VMWare"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by Dave232 on 2007-08-20
I'm new to Linux and Ubuntu, but I'm very comfortable with command-line, vi, etc.  (Long time Unix user, but not admin.)

I'm trying to install VMWare.  I'm trying to ease my dependence on another (unnamed) operating system.  Tired of virus, hijacking, BSODs.

I've (tried to) follow directions from a different thread.
- something about updating:
> sudo apt-get install linux-headers-`uname -r` build-essential xinetd
(whatever the heck that means...)

- went to VMWare website
> [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

- stumbled around and found a server (right one?)
VMware Server for Linux, Binary (.tar.gz)

- downloaded to my machine, ran the archiver, put files into /tmp
- was never asked about registration, email address or any such thing...?

- kicked of installation script
> sudo ./vmware-install.pl

- actually, it didn't work via sudo.  I did su, and tried again, and it started running.  It asked lots of questions (heck, I don't know where I want to install this thing...  How come no one around here talks about putting things in "/opt"?)
- I did change the installation target from /usr/bin to /usr/local/bin...

- During the "make", errors started spewing out:
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

- I got a new menu entry: Applications > System Tools > VMWare Server Console
- but (after a few seconds) it doesn't launch anything

So...., now I'm stuck.

Any hints on how/where to get VMWare running?
The specific instructions (from the other thread) don't accurately match what's on the VMWare website, so I don't even know if I've got an earlier problem...

Thanks,

Dave.

---

### Post by ddrichardson on 2007-08-20
Did you try [this]("http://www.howtoforge.com/ubuntu_vmware_server") guide?

---

### Post by Sye d'Burns on 2007-08-21
ddrichardson's linked tutorial works like a charm on the install. Follow it.

'uname -r' in the console to determing the kernel you are running and that's what headers you'll download.

---

### Post by basilf on 2007-08-21
I keep getting a loop problem with VMware I tried to install it in Automatix2 and it keeps re-trying to install VMware:

Setting VMware (1.0.2-2) ...
Now configuring VMware Player
 
Configuring a bridged network for vmnet8.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)

then asks to replace dirs and then does it after EVERY program is there a @#%$#@$# fix!!!

---

### Post by ddrichardson on 2007-08-21
> **basilf said:**
> I keep getting a loop problem with VMware I tried to install it in Automatix2 and it keeps re-trying to install VMware:

This might be better posted in Installation and Upgrades if it's an Automatix2 problem.

---

### Post by Dave232 on 2007-08-22
(I think my problem is Fiesty Fawn?)

Okay, I've tried the guide that ddrichardson posted.  Yes, the guide is much more complete and looks great.  However, it didn't work for me.  I get through a lot of it, through about a dozen of the questions (properties).  Then, it gets to the "trying to find a suitable vmmon..." at which point it should say something like "...found Ubuntu6.06...".  But, I have 7.04.  I assumed/hoped that I could simply proceed with forward compatibility.  It tries to recompile, and gets compilation errors.  In fact, it's the exact same thing as my original post, but now I understand more of what's happening.

Has anyone tried installing VMware on 7.04?  I have a typical 3.0GHz Dell, 2GB RAM, lots of disk (450MB, all available), ATI x600, etc...

Thanks, Dave.

---

### Post by Dave232 on 2007-08-22
Perhaps, a related question is: what is an "appliance"?  I'm looking for a VMware *server*, but found "appliance".  Are they the same thing?

---

