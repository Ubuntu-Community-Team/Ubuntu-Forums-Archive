---
title: "SPARC Netboot how-to?"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by chris_andrew on 2006-05-31
Hi,

I have been having problems booting Dapper on my Ultra 10 (it fails at "Booting Linux").  This may be an issue with booting burnable media.  It has been suggested that I try a netboot.

I have no idea how to do this.  Can anybody help me?

My Ultra is networked and the image (regular ISO?) will be located in:

*192.168.0.x /home/chris/downloads/sparc*

on an x86 box.

Many thanks,

Chris.

---

### Post by netztier on 2006-05-31
[http://www.hermann-uwe.de/blog/help-how-do-i-boot-debian-on-a-sun-sparc-ultra-10]("http://www.hermann-uwe.de/blog/help-how-do-i-boot-debian-on-a-sun-sparc-ultra-10")

Might just be what you are looking for. Of course, you'll need the boot.img from ubuntu, not from Debian...

Here, this should do the trick:

[http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/]("http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/")

Good luck! :-)

kind regards

Marc

---

### Post by chris_andrew on 2006-06-01
Marc,

Thanks for the netboot advice.  I haven't tried it yet.  The thing that gets me is that I can install Aurora, Debian Sarge and Gentoo, without any problems.  I just can't do Etch or Dapper.  I'm guessing it's not a CD media issue.  Does anybody else have any thoughts?  The netboot idea is good, but if sparc64 is going to get a big following (fingers crossed), then it will need to be able to boot from CD.

Cheers,

Chris.

---

### Post by netztier on 2006-06-06
Hi Chris

You might be running into a SILO issue:

[https://launchpad.net/distros/ubuntu/+source/silo/+bug/40119]("https://launchpad.net/distros/ubuntu/+source/silo/+bug/40119")

Updating the OpenPROM seems to help, and most of the suggestions in that thread mention network booting as a remedy.

If I can't get the issue with the CD-ROM drive in my last Ultra 60 fixed anytime soon, I'll have to netboot too.

regards

Marc

---

### Post by chris_andrew on 2006-06-07
Marc,

Thanks for your advice.  I checked-out the URL.  I am going to see whether a newer image is available, then may try the net-boot.  It seems that if it is in OBP problem, then when the Dapper sparc64 server image is released, it will have to specify a minimum OBP version number.  Will report any findings.

Many thanks,

Chris.

---

### Post by jbalders on 2006-06-08
[QUOTE=chris_andrew]I have been having problems booting Dapper on my Ultra 10 (it fails at "Booting Linux").  This may be an issue with booting burnable media.  It has been suggested that I try a netboot.[/QUOTE]

Condensed version
(assuming   MAC: 00:03:ba:0c:df:5c    IP: 192.168.1.45)
1) (on the x86 box) apt-get install rarpd tftpd
2) mkdir /tftpboot (or somewhere else, just make sure you make the appropriate changes below)
3) cd to the directory created in #2, and get the boot.img from here:
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/)
4) ln -s boot.img C0A8012D
5) echo 00:03:ba:0c:df:5c 192.168.1.45 >> /etc/ethers
6) /etc/init.d/rarpd restart
7) check that the tftpd line in /etc/inetd.conf exists.  Example for this configuration:
tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /tftpboot
restart or SIGHUP inetd, if you made any changes
8 ) on the sun: boot net

The process goes something like this:

1) the sun RARPs for an IP address.
2) the PC sees this, looks in /etc/ethers, and replies with the IP address that matches the mac address from the request
3) the sun attempts to connect via TFTP to the system that replies to its RARP request and tries to pull /C0A8012D
4) the installer grabs everything it needs via the internet, or local mirror.  (apt-proxy is your friend!)

Note that C0A8012D is a hexidecimal representation of the IP address:  192=C0    168=A8    1=01    45=2D.  The calculator in Dapper will help you translate it (in scientific mode) if you can't do it in your head.

This process works well on my Netra X1's and Ultra 5's.  I haven't tried it on anything else yet, although I may be trying it on an e450 soon.

I've had problems with my Suns recognizing a CD-R burned at high speed.  I reburned it at 8x or 4x (don't remember), and it worked.  It's hard to say whether it was the Suns, the CD, a bad burn, or the speed that caused the problem though.  YMMV

A couple of warnings:

1) This method does a desktop install by default -- I'm still trying to figure out a way to get it to do a server install
2) There's an issue in the Linux kernel dealing with the "Host Protected Area" on Seagate ST320413A drives (used in some of my Netra X1's), which essentially renders them useless in kernels greater than 2.6.11.  I added to an existing bug report about this at launchpad.net.

Good luck,

Jeff

---

### Post by jbalders on 2006-06-08
[QUOTE=jbalders]
1) This method does a desktop install by default -- I'm still trying to figure out a way to get it to do a server install
[/QUOTE]

I found the answer:

boot net preseed/url=http://192.168.1.20/ubuntu-server.seed

That assumes that 192.168.1.20 is running Apache and the .seed file (which I obtained my mounting the SPARC ubuntu-server ISO and copying it) is placed in the root of that web server.

Jeff

---

### Post by chris_andrew on 2006-06-09
Jeff,

I like the sound of this, could you be a bit more verbose with your description.  I sort of follow, but would prefer a bit more explanation.  

Thanks,

Chris.

---

### Post by chris_andrew on 2006-06-09
I have a Dapper image for sparc, is this the same as the _*"seed"*_ that you refer to?

Thanks,

Chris.

---

### Post by jbalders on 2006-06-09
[QUOTE=chris_andrew]I have a Dapper image for sparc, is this the same as the _*"seed"*_ that you refer to?[/QUOTE]

As I understand it, the ".seed" file pre-populates some of the questions that the installer asks you about.  This should be a tiny text file.

I think the boot.img file is nothing but a kernel and initrd combined in a single file, and is currently in the neighborhood of 7MB.

I actually had a problem with Netbooting my Ultra 5's.  They would get through the install, up to actually installing the packages, and then hang.  I still haven't figured out what the problem was.  I was working from a serial console, so the whole process was extremely slow and time consuming, and couldn't spend any more time with it, so I had to install from CD.  

Jeff

---

### Post by jbalders on 2006-06-09
[QUOTE=chris_andrew]I like the sound of this, could you be a bit more verbose with your description.  I sort of follow, but would prefer a bit more explanation.[/QUOTE]

What part(s) would you like clarified?

Jeff

---

### Post by killernurd on 2006-08-16
> **jbalders said:**
> Condensed version
(assuming   MAC: 00:03:ba:0c:df:5c    IP: 192.168.1.45)
1) (on the x86 box) apt-get install rarpd tftpd
2) mkdir /tftpboot (or somewhere else, just make sure you make the appropriate changes below)
3) cd to the directory created in #2, and get the boot.img from here:
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/)
4) ln -s boot.img C0A8012D
5) echo 00:03:ba:0c:df:5c 192.168.1.45 >> /etc/ethers
6) /etc/init.d/rarpd restart
7) check that the tftpd line in /etc/inetd.conf exists.  Example for this configuration:
tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /tftpboot
restart or SIGHUP inetd, if you made any changes
8 ) on the sun: boot net

The process goes something like this:

1) the sun RARPs for an IP address.
2) the PC sees this, looks in /etc/ethers, and replies with the IP address that matches the mac address from the request
3) the sun attempts to connect via TFTP to the system that replies to its RARP request and tries to pull /C0A8012D
4) the installer grabs everything it needs via the internet, or local mirror.  (apt-proxy is your friend!)

Note that C0A8012D is a hexidecimal representation of the IP address:  192=C0    168=A8    1=01    45=2D.  The calculator in Dapper will help you translate it (in scientific mode) if you can't do it in your head.

Argh.

I'm running a SPARCStation 20 (ancient tech, I know, but I like the thing). I'm currently trying to netboot it, but it's failing every time. I followed both the link to Uwe Hermann's blog, and this condensed quickstart, substituting my numbers in the appropriate spots.

The machine running rarpd: lugh (192.168.0.2)
The SPARC: chulchulainne (192.168.0.3)

Using Ethereal, I tracked the network activity, and noticed something odd: chulchulainne is broadcasting its request just fine. It's looking for the correct file (in this case, C0A80003.SUN4M), and its packets are reaching the appropriate machine (lugh).

```

source       |  destination  |  protocol  |  info
192.168.0.3  |  192.168.0.2  |    TFTP    |  Read request, File: C0A80003.SUN4M, Transfer type: octet

```

However, once the packets have gotten to lugh, that machine sends back:

```

source       |  destination  |  protocol  |  info
192.168.0.2  |  192.168.0.3  |    ICMP    |  Destination unreachable (port unreachable)

```

I'm new to this scene, so... ideas?

---

### Post by chris_andrew on 2006-08-19
Guys,

Sorry for the delay in replying...new puppy....my life has been turned upside-down!

Will let you know of my progress.

Cheers,

Chris.

---

### Post by killernurd on 2006-08-20
New puppy! Yay! :D

Also - got my SPARC to actually start taking packets, but I get as far as 76f000 (some counter for data; bytes? I don't know), but then I get 'Illegal Instruction' and it stops. :(

---

### Post by chris_andrew on 2006-08-21
Hi, guys.

I just tried the net-install, as described above....nothing.

Everything seemed to work fine, when working through the process, but I think I got confused when converting the IP addresses, I wasn't sure which IP I was meant to be converting.

The IP of my x86 box is 192.168.0.4, which I translated to C0A804.

In step 5), I copied the hex from the U10 boot screen 8:0:20:a0:66:f8 (Host ID (?) 80a066f8 ) and substituted 192.168.0.4 for the example 192.168.1.45.  I echo'd to /etc/ethers which didn't previously exist.  I checked the .inetd.conf and tftpd looks good.  I rebooted the box (easy option).

I then booted the U10 and typed boot net at the OBP prompt.  Can anybody correct my actions, please?

Cheers,

Chris.

Alice the puppy is well and says "woof" (hi)!

---

### Post by iank2 on 2006-08-27
First, the IP is not the IP of your x86 box.  It is the IP of your sun box.
Second, the IP in hex needs to have all four octets:

192.168.0.4 is C0A80004, not C0A804.  Hope that helps.

---

### Post by tio00 on 2006-09-03
This is my first post, so let me first say: hi all!

I've been following this thread awhile, trying to install ubuntu dapper on my old sparcstation20 just like killernurd. After finally getting rarpd and tftpd (I eventually had to use tftpd-hpa to get it to work...), i'm experiencing the same syptoms as the others here with older sparc hardware: Illegal instruction. I've narrowed it down to the boot.img file. Which from the link posted here is a sparc64 binary. I found an image at:

[http://ubuntu.c3sl.ufpr.br/debian/dists/stable/main/installer-sparc/current/images/sparc32/netboot/2.6/](http://ubuntu.c3sl.ufpr.br/debian/dists/stable/main/installer-sparc/current/images/sparc32/netboot/2.6/)

but it seems like a pure debian image. Does anyone here know about an ubuntu netboot image for sparc32??

Thanks in advance

---

