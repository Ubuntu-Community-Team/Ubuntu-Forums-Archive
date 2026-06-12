---
title: "Move installation to new hardware, is there a conclusion?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by WebJakob on 2010-08-12
I want to move my existing UbuntuInstallation to new hardware, and googled for solutions.
It's obvious that many have had the same need, and the issue has been discussed at length, so I apologize if I act crudely by bringing it up here.

However the threads I read, were all rather inconclusive, and with lots of caveats, leading me to the conclusion, that the best option might be the tedious one, of completely rebuilding my config, which would be a most unwelcome chore, so before I take that leap, I would ask here, if some relatively straightforward and failsafe method has been identified?

Some specifics:
The installation functions as my lanServer, and has been modified with thirdparty-repositories and probably also directly downloaded debs, also some packages have been compiled from cvs.
Some of the services it provides are: dns, dhcp, ssh, ftp, http(ssl), blog, caldav, mldonkey, vnc, vpn (and appleshare in disorder). Probably some I forgot.

The old and the new hardware are quite similar, moving from Dell Latitude D600 to D610, so I wonder if it would be possible to simply boot the new hardware from the old installation?
Is there a way to reinvoke hardware-recognition?
[http://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D600](http://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D600)

The RAM will double to 1 GB.

System hostname	dell
Operating system	Ubuntu Linux 10.04
Webmin version	1.510
Time on system	Thu Aug 12 10:06:04 2010
Kernel and CPU	Linux 2.6.32-24-generic on i686
Processor information	Intel(R) Pentium(R) M processor 1.60GHz, 1 cores
System uptime	1 days, 10 hours, 03 minutes
Running processes	176
CPU load averages	0.09 (1 min) 0.09 (5 mins) 0.09 (15 mins)
CPU usage	1% user, 2% kernel, 0% IO, 97% idle
Real memory	497.08 MB total, 188.85 MB used

---

### Post by JustinR on 2010-08-12
The default Ubuntu installation of the Linux Kernel contains drivers for pretty much every generic-ish and some proprietary system components out of the box- not just your PC's hardware. So moving the installation over should cause no problems. 

The easiest way to do this would be swapping hard drives out.

---

### Post by robert shearer on 2010-08-12
Got a spare hard drive ?

Clone the old install to the spare drive and move it to the new hardware and see if it boots.
If it does then good and if it doesn't then you have lost nothing but time. (1/2 hour job)

I have been surprised at how often this works, even on wildly varying hardware including going from a intel cpu to an AMD.

Graphics cards have been the sticker in the past but now with probing at boot and no static xorg this seems to be solved.

---

### Post by WebJakob on 2010-08-12
Fantastic! Thank you guys, that's the best reply I could hope for.
I will either simply swap the drive, or do the cloning.

If there are no grave dangers of doing the swap, such as never being able to go back to the old hardware, then I'd prefer to simply test the hd-swap.

---

### Post by WebJakob on 2010-08-12
What would a good way to do the cloning?
There is probably a bonus of a larger, and somewhat newer hd in the new machine, which would be an argument for the cloning. Especially if it's possible to clone to a larger partition, or enlarge the partition after cloning.

---

### Post by howefield on 2010-08-12
Clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by WebJakob on 2010-08-12
Thank you for the tip regarding clonezilla, which worked fine.

Two snags:

1: After booting from the new machine, the dhcp server no longer worked.
2: After using clonezilla in beginnermode, the bootpartition only used half the disk.


1) dhcp:
dhcp failed with a weird errormessage:
"WARNING: Host declarations are global.  They are not limited to the scope you declared them in."
It turned out that this errormessage was oddly misleading. The problem was that new machine, with it's different mac-address, got its eth0 changed to eth2, and this threw the dhcpd.
My solution was to edit the file "/etc/udev/rules.d/70-persistent-net.rules", and remove all the registered network-interfaces, and then reboot. This reverted the ethernet port to eth0, and the dhcpd worked again.

2) partitioning:
Clonezilla in beginnermode made a bootpartition the original size, rather than using the whole new disk. It then made a swappartition, and the rest of disk as unallocated.
Rather than figuring out how to move the swappartition, and resize the bootpartition, i simply ran clonezilla again, and this time chose the expertmode.
In expertmode, it is possible to chose to fully utilize the targetdisk. This took a couple of tries, because - apparently - after choosing to expand, you ALSO subsequently have to choose something with 'proportionally' making something with the partition-table.

---

