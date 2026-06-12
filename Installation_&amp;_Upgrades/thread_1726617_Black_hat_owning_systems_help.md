---
title: "Black hat owning systems help"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by sweet pea on 2011-04-11
I currently have a black hat that has already  written custom code tailored to my hardware, they have been owning my  systems since Thanksgiving 2010 & I have already returned 3 new  laptops that got hacked since then.

I'm pretty sure they altered the entire bios program for my main computer. The only  thing I can do is boot from Ubutnu 10.04 Live cd.  Not any windows  opertaing systems or any other version of linux for the matter.

Just yesterday they had to have flashed my bios with a new update.  Now  when I use synaptic package manager or command line to try to install  anything, I get the following error message

**Selecting previously deselected package ndiswrapper-common. ***(or any package for that matter) *
[B](Reading database ...  dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'pulseaudio-module-bluetooth' : Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

Regardless of any package I try to install, the error is always**  unable to open files for package 'pulseaudio-module-bluetooth'.**


I can't install anything.  Not even flashrom to try to flash the bios  from ubuntu linux.   I used to have other network cards and graphic  cards in my box, I had to take them all out. If I try to boot from a usb  drive or any sata or ide hard drive - I get a bios error saying there  is no bios at all.

Not only did they do that.   They also hacked my Cisco business 851w  router, my linksys wrv210, and Verizon fios Actiontec MI424-WR, all to  have open ports or some type of rootkit for my devices to connect to  them as soon as I connect to the internet. I  I already returned 2 fios  routers back and got replacements.   I would do things like configure  the security setting and block as many ports as possible.  10 minutes  later I would have several random ports open that don't even come on by  default in the routers. 


I even called the FBI & IC3 about this and they really don't care.  They told me I am not an important business or anything to threaten the  nation. L0L0L0L... 

What to do? other than throw away the box or reserve it for computer forensics?  I was looking into replacing the replacing the reading database and it just directed me to the file in /**etc/apt/sources.list.  ** Even when altering things in the sources.list I still get the same error message when trying to install any programs.


To make matters worst, the bios utility for my motherboard is only flashable from windows software.  It would be nice to find a way to flash my bios completely from ubuntu and then look into bringing the system back up .

---

### Post by Bakerconspiracy on 2011-04-11
> **sweet pea said:**
> 
**Selecting previously deselected package ndiswrapper-common. ***(or any package for that matter) *
[B](Reading database ...  dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'pulseaudio-module-bluetooth' : Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]


This seems to be a dpkg error. 

[ This link maybe yields an answer.]("http://ubuntuforums.org/showthread.php?t=1154174")  

Anyways man, why would anyone want to compromise your system that bad. I think you should look into ufw for starters, then look into app armor if you really think security is the problem. (just basic security stuff)

A lot of the time a generic browsers will use a bunch of high ranged ports to connect to websites. I believe this has to do with optimization...

Sometimes it is good to be a little paranoid, but this

> **sweet pea said:**
> 
I even called the FBI & IC3 about this and they really don't care. They told me I am not an important business or anything to threaten the nation.

says to me, maybe you are spending a little bit too much time in the house. Go outside and hang out with your local LUG.

Cheers man.

---

### Post by tgalati4 on 2011-04-11
Invest in some quality tin foil.  Silver hats can protect you from black hats.

From what you have described, random ports do get opened for several services that get started at boot time.

Other than your assertion, nothing that you have presented is proof that your system has been compromised.

I can't help you with the Windows problem.  I haven't used Windows in several years.  For linux, what are the suspicious entries in /var/log/auth.log?

---

