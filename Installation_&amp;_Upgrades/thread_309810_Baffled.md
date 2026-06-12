---
title: "Baffled"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by klittzzer on 2006-11-30
I recently installed Ubuntu 2.6.17-10, 2.6.17-10-generic on my laptop to dual boot with windows. It is all working ok except for 1)I cannot get my Sagem Fast800 operational
2) And thus canot browse the web.
I have followed Aces [http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem](http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem)

easily understood how to a number of times yet have had no success.

I feel I have to do the following ::confused: 

remove the linux headers generic package and the directory in /lib/modules
-remove the 2.6.17-10 directory in /lib/modules
-install the linux-headers-2.6.17-10 & linux-headers-2.6.17-10-386 packages

- make sure the build link in the /lib/modules/2.6.17-10-386 points to /usr/src/linux-headers-2.6.17-10-386

recompile and install ueagel-atm and reboot:confused: 


The above removal of headers etc was copied from 

[http://forum.eagle-usb.org/viewtopic.php?t=4499](http://forum.eagle-usb.org/viewtopic.php?t=4499)

Is this right?

If this is so, 
do I need to download the headers mentioned above along with the dependencies and install them? :confused: 

Or are the headers already on my installation disc (Ubuntu Edgy 2.6.17-10-generic live cd)? ;) 

Are the dependencies for these headers already on my machine, ie, did they get installed when I installed Ubuntu on to my partitioned hard drive?:confused:

Or do I have to download them (and if so, what ones do I need)?

Lastly, if I do have to do the above, (which I will try anyway seeing as I am not on the net through Ubuntu so have nothing to lose) can someone point me toward a how to(s) that explains how to perform the above tasks, ie romove headers, install headers, remove directory, and how to tell if...


/lib/modules/2.6.17-10-386 points to /usr/src/linux-headers-2.6.17-10-386

Can the above be done with Synaptic and live disc?

Please Help me if any one can. I would love to be able to eventually ditch Windoze.

Thanks

Klittzzer



 

(copied from > [http://forum.eagle-usb.org/viewtopic.php?t=4499](http://forum.eagle-usb.org/viewtopic.php?t=4499))

---

