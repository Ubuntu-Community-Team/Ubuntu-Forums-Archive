---
title: "Ubuntu upgrade and VMPlayer"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2007-10-17
I am expecting to soon upgrade to the new kernel. Gutsy.

I use VMplayer at present on FIesty. Will the upgrade overwrite the contents of the virtual disk.?

Will I have problems running VMWare after the upgrade?

Robin

---

### Post by Robbyx on 2007-10-18
I don't think I am asking a crass question. 

I have noticed that in earlier upgrades to the kernel that have been problems getting VMplayer to work. Does anyone know if I am ilkely to have the same problems this time around, and if so if there are any easy ways to avoid trouble and still use VMplayer.

R

---

### Post by davidshere on 2007-10-19
YES... don't upgrade if you want to continue using VMWare Player.  The upgrade uninstalls VMWare and you can't re-install unless you have a 64 bit processor.

[http://ubuntuforums.org/showthread.php?t=580565&highlight=vmware](http://ubuntuforums.org/showthread.php?t=580565&highlight=vmware)

---

### Post by Robbyx on 2007-10-19
Thank you for your reply.

I have been running Ubuntu 32 bit, but my processor is a Pentium D:   LGA775. I presume this means that my processor is 64bit. How does this help me avoid the need to reinstall vmplayer? The url you cited did not appear to cover this point.

Do you know if anyone has vmplayer working in gutsy?

There was some advice in the other thread about this:

> Presuming vmware-server was installed from source originally (no other way really) then you do not have to remove it and reinstall it.

just go to a terminal prompt and type

Code:

/usr/bin/vmware-config.pl

This will reconfigure/compile vmware server with the new kernel headers.

(and ANY time you have a kernel change you will have to do this again).

If there are errors in the compile and modules like vmmon and vmnet refuse to compile - its likely because the vmware-server source you have doesnt know about the newer linux headers that come with your latest new kernel. So google for the "vmware-any-any" patch. Download the latest one you can find, and follow the readme to apply the patch to your vmware-server source. After this patch is applied vmware-server will compile with "any-any" version of linux headers.

Reading the other thread it implies that VMplayer was comletely removed by the gutsy installation.  How could I recompile it as quoted?

At present there is a file in my directory 

/usr/bin/vmware-config.pl

but I do not know if player put it there are an earlier and temporary installation of server.  I did so as to obtain the tools for player. 

Do you know if gutsy leaves the files in place so that I could recompile?



Robin

---

