---
title: "How to install ubuntu on dell vostro 1500 with vista already installed?"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by tamal on 2008-01-10
Hi, 

I partitioned my disk using the vista's inbuilt partitioner. It shows 10 GB unallocated space in vista. But ubuntu does not recognize vista at all!
It just wants me to use the whole hard disk for its install.
Could this be because I have used vista's partitioner for partitioning?
How can I make ubuntu recognize vista which is already installed?

Has any one installed ubuntu with vista already existing on vostro 1500?

Tamal

---

### Post by tamal on 2008-01-10
I used these steps for partitioning my disk in vista:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

and then used these steps to reach till the ubuntu install icon on vostro:



Out of the box the first thing I did is test the laptop under XP. Everything seemed to be working satisfactorly. WiFi connected to my router and I was able to browse. Buttons all work. Fan's work well. 

On my computer I had 3 partitions from the factory. One partition for XP. 2 other partitions existed on my HD. One looks like a XP install disk mirror and another looks like maybe it holds utilities. I didn't mess with those. With the one large partition holding XP I defragmented the drive 2x to make sure all the files were as close to the front of the partition. Next I partitioned the XP partition roughly in half. I used a gparted live CD to do this but there are other programs like Ghost and Partition Magic. 


+++++++++++++++++++++++++++
Installing Ubunto Feisty 7.04 32bit 
+++++++++++++++++++++++++++

The Ubuntu Live CD or the alternate install CD will NOT WORK. To install using the Live CD, I found this set of instructions invaluable:

amber_474 wrote:

Pre-Install:


Boot from the Live CD
Press F6 to edit the command line and
remove: splash quiet (actually on my screen it quiet splash, but just delete it from the end of the line)
add: break=top (to the beginning of that line)
from the command line and press Enter

Ubuntu will boot and get you to the Busybox shell

/bin/sh: can't access tty; job control turned off(sh)

Give the commands:

$ modprobe piix
$ exit

Ubuntu boots and X server fails to start, so do:

$ sudo dpkg-reconfigure xserver-xorg

Select: 'vesa' instead of 'nv' as the driver
Select /dev/psaux for mouse

and rest is default. (use the options the program highlights)

$ sudo /etc/init.d/gdm start
or
$ sudo /etc/init.d/gdm restart

--might have to do that last step twice, I don't know why. The live CD will run and start up the desktop. You will notice that the desktop looks wierd. Thats because it is not in the native resolution of your screen. We will fix this later.

Click your install icon and follow the prompts. I didn't do anything weird except when it gets to the partition manager make sure to choose manual to show the installer where your empty drive space is.

---

### Post by tamal on 2008-01-10
But I can not make ubuntu see vista :-(

---

### Post by slarrabe on 2008-01-10
You could just get a second hard drive and install Ubuntu on that.  I recommend using an external USB drive so you don't have to mess with the jumper settings.

---

### Post by tamal on 2008-01-10
there's gotta be a way to do this. has no body tried this?
could the problem be with me using vista partitioner?
or could it be that there is a problem with the hdd that they gave with vostro 1500?

this has become really frustrating now.

---

### Post by Geek_In_Training on 2008-01-11
I installed Ubuntu in Virtual PC 2007 on my Vostro 1500.

---

