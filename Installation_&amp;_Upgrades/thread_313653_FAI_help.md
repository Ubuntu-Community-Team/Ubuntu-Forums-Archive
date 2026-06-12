---
title: "FAI help"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Ecthelion on 2006-12-06
Hi, I'm an University student who's active in a project to install Ubuntu on the University computers. The idea is that this would stimulate student's to try it out.

So we are planning to install Ubuntu on all the university computers using FAI.

I was trying to configure it using [this]("http://www.debian-administration.org/articles/240"), since it's explained more easily than [the official guide.]("http://www.informatik.uni-koeln.de/fai/fai-guide.html/")

But I'm stuck. When I do fai-chboot -l I get no host...
I did adapt the /etc/dhcp3/dhcp.conf And added the hosts their Mac adresses.
But even when I try to do
sudo fai-chboot -iFv demohost
I get host unknown.
The demohost is default.. (I copied /usr/share/doc/fai/examples/etc/dhcpd.conf to /etc/dhcp3/dhcpd.conf )

Anyone who can help me?
I think I made some obvious mistake somewhere but I can't find it...
(btw I'm using VMware to test it)

Thanks in advance,

Ecthelion

---

### Post by Ecthelion on 2006-12-07
I've done it all over again (made a new virtual machine, installed ubuntu, then fai etc...) and this time I followed the official guide.

But I'm still stuck at the same place.

I think that I'm making my mistake here:
[QUOTE=fai-guide]* Add your host (try to name it demohost) to dhpd.conf and /etc/hosts (=your DNS) on the fai-server.[/QUOTE]

But how should I exactly do this?
I've simply added the mac address at the bottom of /etc/hosts like this:
> 00:0C:29:94:0A:10 demohost

And in dhcpd.conf I changed the ethrnet adress that was there by default by the same (00:0C:29:94:0A:10) (which is the macaddress of the VM that i'm trying to install using FAI)

Anyone who can tell me how I should add my host if this isn't the right way?

Thanks in advance :)

---

### Post by Ecthelion on 2006-12-16
Anyone?

Any suggestion can help since I'm really stuck.
How obvious it can like to you, don't hesitate to say it!

Thanks!

---

### Post by Ecthelion on 2007-01-12
Still no answer & still no solution...

---

### Post by GGJ19 on 2007-01-18
Hello,

I'm installing debian on serveral computers using fai. I can't help you with your questions  in a direct way but I can tell you how I dit it. 

First I've installed fai on a debian system. 
After the installation I installed the necessary packages using the official fai guide.
(The common was apt-get install fai-quickstart). It was necessary to add the repositories of the FAI download location to /etc/apt/sources.list ('deb [http://www.informatik.uni-koeln.de/fai/download](http://www.informatik.uni-koeln.de/fai/download) sarge koeln') because not all of the FAI packages were in the Debian distribution.

I added a few configurations into:
:confused: 
/etc/fai/fai.conf
/etc/fai/make-fai-nfsroot.conf
/etc/fai/menu.lst
/etc/fai/sources.list

I didn't make a local Debian mirror but I used the apt-proxy mirror that was already running in the network.
Because I use an DHCP-server I didn't make any changes to the network configuration or to any hosts.

After the configuration I called the fai-setup
So far, So Good! The fai-setup was completed correctly.  :) 

After the setup I made a bootfloppy using the common make-fai-bootfloppy.
First time I booted there where a few problems with my DHCP because in the local network there was already an DHCP-server. So after I solved the problems the client boot correctly and a few partitions where made. The client asked for a reboot so I removed the floppy and rebooted the system. 

While experimenting for the correct boot- and root server options I experienced a strange thing: I could preconfigure the root server by adding the IP to the kernel boot options in the menu.lst file, but could not find a way to alter the boot server IP. For the boot server, the FAI installer always used the same IP as the DHCP server it connected to. To overcome this problem, I made sure the installer connected to the FAI master for the DHCP request, so it could find the boot server under the same address.

When the system restarted everything workt fine an the fai-system took us to the login screen. This is the point where I got stuck.

I get the line: [COLOR="Red"]Plan your installation, and FAI installs your plans.[/COLOR]

I would like to try to copy the complete fai-server to the client but I don't know how to do this. Does anyone know if fai have any scripts to duplicate the whole system??

regards,

( I've also posted to: [http://gathering.tweakers.net/forum/list_messages/1067619///fai](http://gathering.tweakers.net/forum/list_messages/1067619///fai) )

---

### Post by Ecthelion on 2007-01-18
Finally a reply to my thread.
For the moment I can't try and help you since I have examinations.
These will end begin februari and then I'll give FAI my full attention again.
Maybe I can then ask you how some of your configuration file looks like etc (if you don't mind of course).
Maybe I can help you solve some of your problems (this is rather unlikely, since I really don't have much experience in network)
I'll do my best anyway :-)

I hope you get FAI working!

---

