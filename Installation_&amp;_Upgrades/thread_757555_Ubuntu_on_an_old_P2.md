---
title: "Ubuntu on an old P2"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Mets on 2008-04-17
I have an old P2 350Mhz, 192MB of ram, 10gig hard drive, 4mb graphics card desktop that I want to install a version of Ubuntu on.  Right now I'm deciding between Xubuntu, Fluxbuntu, or Ubuntulite.  This will basically be used as a backup computer, and maybe run some random processes through ssh that I feel like running when I'm bored.  What do you think would work best?

---

### Post by analoog on 2008-04-17
have you considered ubuntu-server? [http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)
graphics over overrated ;)

You can also have a look at [FreeNAS](http://www.freenas.org/). If you upgrade your old pc with some harddisks you can make a really nice NAS from it, with extra protection of your data if your run RAID in mirror mode.
You can configure FreeNAS via a web-interface. It's not a linux distro but an unix derivative.

---

### Post by kerry_s on 2008-04-17
none of the above. debian is much better on the old stuff.
do a base install and build up from there. net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at the package selection, uncheck desktop and check the server stuff you want.
log in as root
apt-get install xorg synaptic (a wm) (what ever else)
type> exit
log in as your user
type> startx
open synaptic and build on

you'll get a much better system when you do the work yourself with only what you need.

---

### Post by iaculallad on 2008-04-17
with 192MB of RAM, give it a try for Xubuntu Alternate CD. (If you like using Ubuntu)

---

### Post by hums07 on 2008-04-17
I have similar computer an old Dell PII 350 MHz RAM 256 MB.
Xubuntu is still sluggish (at least in my system), so I run fluxbuntu. If you just want to run ssh, it will be ok to use Xubuntu which is a "standard" Ubuntu flavor.
Or even you can also try this: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by analoog on 2008-04-17
> **kerry_s said:**
> none of the above. debian is much better on the old stuff.
do a base install and build up from there. net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at the package selection, uncheck desktop and check the server stuff you want.
log in as root
apt-get install xorg synaptic (a wm) (what ever else)
type> exit
log in as your user
type> startx
open synaptic and build on

you'll get a much better system when you do the work yourself with only what you need.

You don't know what you are talking about, Ubuntu Server is  very minimalistic when the installation is finished (when using the default settings) It's not a full desktop-system with X-windows like the normal ubuntu.

And I was under the impression that synaptic doesn't work when you only use the shell?
I always use aptitude or apt-get for installing what I want from the command line.
I agree with you that you should start quite minimalistic. 
Debian is a very good server OS, if you want something that has proven itself in the last decade try that. Only downside is that it can take quite a long time before some new versions get into the stable release. 
And yeah, always enable services later or during install that you really need, do not install a whole lot of services that you don't really use, it's a security risk and it slows down your system.

And what's wrong with recommending FreeNAS for the purpose of having an old box that can serve as a backup storage attached to the network?

---

### Post by kerry_s on 2008-04-17
> You don't know what you are talking about, Ubuntu Server is very minimalistic when the installation is finished (when using the default settings) It's not a full desktop-system with X-windows like the normal ubuntu.


how would you know what i know?
i know exactly what it is, how to use, how it runs. debian is still faster, smaller, more stable.
all my installs are custom built from a base up.

> And I was under the impression that synaptic doesn't work when you only use the shell?

true, that's why it's up to him to pick the wm he prefers.

> Only downside is that it can take quite a long time before some new versions get into the stable release. 

you've heard of backports? i prefer just moving up to lenny myself.

> And what's wrong with recommending FreeNAS for the purpose of having an old box that can serve as a backup storage attached to the network?

nothing

i've done thousands of installs, using different setups with different os's.
all i did was recommend debian, as i've found it works much better on the older slower stuff. my systems 450mhz 256mb ram laptop, started out with 64mb and then went to 128, until finally i got enough ram to max it out at 256mb. i do have experience with low resources.

---

