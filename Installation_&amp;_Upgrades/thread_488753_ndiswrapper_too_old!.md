---
title: "ndiswrapper too old!"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Dangit on 2007-06-30
I don't know how this happened.  I'm certain that last night I had ndiswrapper in good working order.  Today I see this about it.  

ndiswrapper -vmodinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Ugh.  My wireless isn't working either, not sure it has anything to do with this.

I'm new.

---

### Post by bl-info on 2007-10-19
I got the same message on my Fedora 7 x86_64. What I did to lose this message was to recompile the ndiswrapper-utils and the ndiswrapper-driver. How? Downloaded ndiswrapper source 1.48 from sourceforge and put the source somewhere. 

Started terminal, went to the driver and util dir. There I issued these commands as root:
make clean
make configure
make install

This convinced the system to compile the ndiswrapper bunch. If make does not work for you, you should yum development stuff into your system with all dependencies:
yum install gcc cpp kernel-devel

Now I get this message after issuing ndiwswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22.9-91.fc7/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.22.9-91.fc7 SMP mod_unload

---

