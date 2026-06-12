---
title: "Major problems with RocketRAID 2310 under Ubuntu /.04"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by hans.hook on 2008-01-02
I have previously had an excellent experience with the RocketRAID 2310 controller - under Open SuSE 10.1.
With Ubuntu 7.04 kernel 2.6.20-16-server (32 bit) I am in no luck!
I have compiled the kernel according to HighPoint's instruction after patching it with version 2.1 driver from HighPoint and did also remove the sata_mv driver.
The boot process just hangs on the Rocket RAID driver. I get no additional info.
With the sata_mv driver (as an alternative) I also have no luck since it complains about a PCI ERROR.
With identical hw and Open Suse kernel 2.6.16.53 all is fine!
Has anybody been down this road and installed the RR 2310 in Ubuntu 7.04 (or 7.10 for that matter).

(HighPoint states in its README that kernel verison up to 2.6.24 are supported and they explicitly 
mentions fixing problems in Ubuntu 7.04.)

Extremely gratefully for any assistance!

Hans Höök

---

### Post by hans.hook on 2008-01-03
Problem solved

I finally solved this issue and may conclude that the rocket RocketRAID 2310 is operational under Ubuntu server 7.04 (performing at >150GB/s disk bandwidth with ordinary SATA Disks in raid 1/0 !?)

The way to do it is to build a patched kernel.
I used server kernel source 2.6.20.3 and the HighPoint driver v2.1.12.03.
Follow the instructions in the HighPoint README and be sure to exclude the sata_mv driver from the
kernel.
I do not know if I was lucky or if everything is actually stable but these versions of the 
driver and the kernel 
are the only ones that work for me (and I have tried a few others combinations by now 
   - do not even try driver v2.1 2007-8-22!!)

Hope this might help anyone else that gets stuck on this.

Hans Höök

---

### Post by randknu on 2008-02-03
I am trying to get this card to work, but i am helplessly new to linux and i am learning the hard way, by the command line!

So i have extracted the contents of the driver package in my home directory under a rr231x_0x-linux-src-v2.1 subdirectory

it says in the readme:
As long as the system has kernel headers setup under /lib/modules/`uname -r`/build, you can simply run "make" to build the driver.

Well i don't have the build directory... Is that where the "uncompiled" kernel is supposed to go? and where do i find that? and can i just put it in there and it should work?

I'm running 7.10 server btw.

---

### Post by AbeJarano on 2008-02-14
yeah   that's where it goes. I know synaptic is easyer when you cna't remember the file name  which I cant'.  do in System>Administration...the name  is something  like "kernel-headers"

---

### Post by CyberDean on 2008-02-25
Just found this thread, just received my RocketRAID 2310 controller. I am also new to Linux about a month ago.  I have a server I am getting ready to install 7.10 server Linux software into. This server has never been operational, it is totally new.

I quess my first question is, does the server software need to be installed on the server before installing the RocketRAID controller and controller software?  Or does the controller software need to be compiled with the kernel first?

Another question I have is, the mother board in the server has an onboard RAID controller, when I install the RocketRAID controller, I am assuming that the onboard controller will have the first drives seen by the server, sda and sdb I believe.  And the RocketRAID controller will have the next drives, sdc, sdd, sde and sdf.  Am I correct or am I wrong?

Please excuse my ignorance about Linux, I am learning and have much to learn.

Thanks for any help, this will help to get the server started.

---

