---
title: ":-( Still can't install :-("
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-03-16
I've tried several things to try to just install ubuntu on the entire drive.  I still am not able too.  

The main problem is when I put in the CD in it loads the way you would expect it, except after I hit the normal boot/install button. That's when it just hangs with the Ubuntu Logo and a load bar that keeps loading forever.

I found a decent reference that may of helped me get a tad more information about what could be potentially be blocking the installation.
So, I tried hitting F6 on the screen as well and deleted the "Quiet - splash" and replaced with "break=bottom" to boot me into a command line so I can configure xorg.conf.

Now, before I even get that far... the screen is black with alot fo white txt.  More then 5 of these txt say something like

[B]Buffer I/O Error, Dev HDD, Sector####

Buffer I/O Error on Device HDD< Logical Block ###

HDD MEdia Error(Bad sector): Status = ox51[/B]

Can you explain to me what that means? Is this an problem?  How can I resolve these?


Soo, After all that I type in chroot /root nano /etc/X11/xorg.conf
which loads me into this configuration file.

The reference I'm using tells me to go to a heading called "device" I go down and this is what it says... 

Section "Device"
Identifier - "Intel Corp 828456/Brookdale-61#######
Driver - I810
Bus ID PCI: 0:2:0

I switched I810 to Vesa just to see if I can get anywhere with this.
I exited the xorg.conf

It loaded some more and then after 2 minutes.. I thought it was really going to load something graphical and got excited.. But then a blue screen came up telling me that X wasnt configured properly.  

Soo, I don't know what else to do from this point on.  I'm coming to a conclusion that Ubuntu isn't registering my video card whatsoever.  

Here is my system stats:
Intel® Pentium® 4 CPU 2.80GHz @ 2799MHz (Intel Corporation D845GVSR mainboard)
(RAM) 1GB
(HDDs) 120 GB
(VGA2) NVIDIA GeForce FX 5500 


I hope someone can get me somewhere with this.. Ubuntu is the distro I been trying to play with for months now... 

Thanks in advance,

Dominick

---

### Post by confused57 on 2007-03-16
Maybe this thread will help you:

[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=5500](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=5500)

---

### Post by al1b1 on 2007-03-16
Or you could try this howto which is more upto date and comprehensive [http://ubuntuforums.org/showthread.php?t=380790](http://ubuntuforums.org/showthread.php?t=380790)

---

