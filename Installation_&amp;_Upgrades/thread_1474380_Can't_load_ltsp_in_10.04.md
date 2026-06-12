---
title: "Can't load ltsp in 10.04"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2010-05-06
Does anyone know how ltsp is supposed to load in a 10.04 Edubuntu install? The live CD worked beautifully, providing me with a gui under "applications/other" with which I could successfully test my thin clients. But once I actually installed Edubuntu (through the live CD), there was no ltsp configuration at all, the gui was gone and there was no visible way to install ltsp. There wasn't even an option in the DVD install routine the way there was in previous versions.
I know I'm not the only one who has had this problem.
What is it supposed to look like?
Thanks,

---

### Post by dbclinton on 2010-05-06
The solution has been found (via the #edubuntu irc channel). For what it might be worth for other people, Edubuntu couldn't download certain resources because it couldn't authenticate my account to the satisfaction of my proxy server. To solve the problem, first install (via synaptic) ltsp-server-standalone, then from terminal (under sudo - i), run:

export http_proxy=http://<myaccountname>:<mypassword>@<proxyserveraddress>:<port>/

and then 

ltsp-build-client

Also, you might have to remove an pre-existing but largely empty
/opt/ltsp/i386
before ltsp-build-client will work (the ltsp-build-client debug will let you know).

Make sure that your client-side NIC is configured properly in /etc/network/interfaces.
Mine looks like this:
=======================
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
	address 192.168.0.254
	netmask 255.255.255.0
=======================
Finally, you may need to reset your keys. Enter these two commands in terminal:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

---

### Post by haddog on 2010-06-21
Thanks. I have had ltsp working on 8.04 but it has been so long since I setup ltsp, I forgot about the commands you mentioned. Wanted to do a clean install using Edubuntu 10.04.

---

### Post by haddog on 2010-06-23
*NOTE: Read this in it's entirety before attempting. It is a step-by-step of how I got a Lucid Lynx 10.04 LTSP server up and running and the thin-clients able to connect to the LTSP server and run.

On 06/19/2010 I wanted an LTSP server running on Ubuntu 10.04 Lucid Lynx. First I installed Lucid Lynx using the Ubuntu alternate CD which includes an LTSP installation.

[http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent")

Once you boot up the CD, hit F4. The "Modes" menu will pop up. Select "Install an LTSP Server". Now just move on with the install and complete the installation.

Next I got all my updates installed for the server using:

sudo apt-get update

sudo apt-get upgrade

After all updates were installed I rebooted the LTSP server. Next I set up the LTSP client image using the following command:

sudo ltsp-build-client

Despite getting no error messages during installing and configuring, at the end I got this error:

LTSP client installation ended abnormally

And then it stopped. I searched around and found a solution. The solution was to use the following set of commands instead of sudo ltsp-build-client command:
	
sudo -s

su -

ltsp-build-client

sudo ltsp-update-sshkeys

ltsp-update-image


I rebooted the LTSP server, started up a thin-client and all was good.

---

