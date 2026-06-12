---
title: "Second part of install fails"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by karasu on 2005-06-09
Hi.

I'm stuck with an install that won't go anywhere. 

The box is a Pentium III, 803 MHz, Asus CUBX-E mobo, 511 MB RAM, Nvidia Inno 3D RIVA TNT2 video card. 

In the first part of the install, there are a couple of lock-ups and some IDE modules (IDE driver, IDE probe mod, IDE detect, IDE-floppy) fail to load. 

When I get to the second part, it all goes very nicely for a while, lots of churning and gyrating and stuff getting unpacked, but then "Starting Enterprise Volume Mangement System..." comes up, stays there for a while, and then the screen goes a dark brown and stays that way forever. 

When I reboot, the box stalls while loading kernel modules, and that's it.  

I've gone through the install a couple of times, and used "expert noacpi acpi=off noapic pci=biosirq vga=normal apm=off" during the last attempt, to no avail.

Each of those failed installs was excruciatingly slow, stalling for a good fifteen minutes or so while "Loading module 'ide-cd' for Linux ATAPI CD-ROM" and then another ten minutes while starting the disk partitioner. 

Knoppix 3.6 (Kernel 2.4.27) didn't have any problems running on this box. 

Any ideas?

---

### Post by mtron on 2005-06-09
Had this load problems on an old laptop with only 32MB RAM (bug in debian installer), but with 512MB? i dunno...

What you can try:
a)download a sarge (or even woody, then update to sarge) netinstall image, run the base install, and change your sources.list to the ubuntu sources
b) if you have a windows OS you can try a harddisk istall, see [here](http://www.ubuntuforums.org/showthread.php?t=28948&highlight=install+harddisk)

---

### Post by karasu on 2005-06-11
I downloaded the Sarge network installer and tried to install Debian instead. Didn't work either. 

Again, a couple of modules failed to load: agpgart, ide-mod, ide-probe-mod, ide-floppy and ide-scsi.

I get through to the second part of the install, but apt fails to connect to the source repositories. 

When I try to reboot after that, the boot throws a couple of lost interrupts and then hangs permanently.

---

### Post by karasu on 2005-06-11
Also: I haven't managed to find out what the partitioner's smileys and the skull and crossbones mean.

---

### Post by mtron on 2005-06-11
The symbols of the partitioner are explained in the help text ( there's a link "Help with partitioning" )

Next attempt: woody install - change sources to sarge & run dist upgrade - change sources to hoary & run dist upgrade

Alternative: install Ubuntu from withtin Knoppix (needs a broadband internet connection , but you can avoid using the - in your case - not working debian installer)

requires some basic knowledge, but big fun! Howto is [here](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto) 

good luck!

---

### Post by karasu on 2005-06-12
Actually, I managed to get a working base system from the Sarge CD. It takes a very long time to boot because of the lost interrupts while loading kernel modules. During the base system configuration I also got a "temporary failure resolving <source>" for whatever http or ftp archive I tried -- so maybe there's something wrong with the networking. 

But other than that -- and, obviously, except for the absence of applications -- I've got a Debian 3.1 system with a 2.6 kernel: I can login as root and user, and all the directories seem to be in the right place. 

I don't mind if I end up with straight Debian rather than Ubuntu -- how would I go on from here?

---

### Post by karasu on 2005-06-12
I've checked the network settings of my Sarge base install -- looks about right to me. 

/etc/apt/sources.list has only one line, though:

#deb file:///cdrom/ sarge main

I should probably delete that line, add the proper Ubuntu sources there and then try apt-get dist-upgrade. No idea what they are... off to find out.

---

### Post by karasu on 2005-06-12
I've changed sources.list to this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

Then did:

apt-get update

apt-get dist-upgrade

... Couldn't resolve "archive.ubuntu.com"

Must be the networking, then, right?

---

### Post by karasu on 2005-06-12
Here are some networking details. 

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address YYY.67.82.100
	netmask 255.255.255.0
	network YYY.67.82.0
	broadcast YYY.67.82.255
	gateway YYY.67.82.154
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers YYY.67.82.154


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:01:02:F1:B2:C2  
          inet addr:YYY.67.82.100  Bcast:YYY.67.82.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138352 (135.1 KiB)  TX bytes:1770 (1.7 KiB)
          Interrupt:9 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 b)  TX bytes:640 (640.0 b)

---

### Post by mtron on 2005-06-12
nice progress so far! 

for the network: 
see the debian manual [here](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html) it's a very clear and easy explaination how to get it working. after that, use this sources list file:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
```

after that run "sudo apt-get update" and "sudo apt-get install ubuntu-desktop" This is a dummy package that will install a usual ubuntu system, like on the install CD.

And you are done!

Welcome to ubuntu  :)

---

### Post by karasu on 2005-06-12
The Debian manual doesn't make much sense to me yet. Why do I have to go through ifconfig? I can just edit /etc/network/interfaces, no? Ifconfig also doesn't seem to give me a method to enter the gateway, which is probably where the problem is.

In the setup, I entered an incorrect gateway I.P.: the final number, it turned out, is 245 rather than 145. So I modified that in the interfaces file. 

This looks funny, though, in the Kernel IP routing table, where I get two destinations: localnet and default. Localnet has "*" for gateway, "255.255.255.0" for genmask and "U" for flags. Default has "YYY.67.82.254" for gateway, "0.0.0.0" for genmask and "UG" for flags.

---

