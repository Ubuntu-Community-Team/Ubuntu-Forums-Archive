---
title: "Intrepid boot time"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nisuspi on 2008-10-26
Hi all,

Since upgrading to the RC I've had a problem with booting into Ubuntu. Basically, the boot hangs at 'configuring network devices' for a couple of minutes before continuing as normal. I'm guessing it's a network manager issue, but not entirely sure if there's a workaround.

It's a wired connection, same on both eth1 and eth0 regardless of which is connected, on an NVIDIA 790 board (I know...) 

 Best

---

### Post by mrjohnston on 2008-10-26
Well the easy option, assuming you know how to connect your lan card manually (sudo dhclient eth0 usually I think, double check that though) you can uninstall network-manager and see if it boots fine.  If it does then its likely there is some initialization issue with NM.  You can either live with it I suppose as I don't know how to fix that or use WICD instead to take care of network connections (I suppose you could just install WICD as that remove network-manager anyway to see what the error is).

---

### Post by ktp on 2008-10-26
> **Nisuspi said:**
> Hi all,

Since upgrading to the RC I've had a problem with booting into Ubuntu. Basically, the boot hangs at 'configuring network devices' for a couple of minutes before continuing as normal. I'm guessing it's a network manager issue, but not entirely sure if there's a workaround.

It's a wired connection, same on both eth1 and eth0 regardless of which is connected, on an NVIDIA 790 board (I know...) 

 Best

I have noticed this when I had things in /etc/network/interfaces. I commented out and let NM do things and things were faster.  I still which I could configure in interface without deal since I want to setup bridge.

---

### Post by Nisuspi on 2008-10-26
Thanks for the help guys - commenting out the old connections did the trick. It looks like the old iface commands were left in the file and 'auto eth1' 'auto eth2' just added at the bottom during the upgrade. Works like a charm now.

---

