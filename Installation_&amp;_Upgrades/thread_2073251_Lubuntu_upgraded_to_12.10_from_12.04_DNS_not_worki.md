---
title: "Lubuntu upgraded to 12.10 from 12.04 DNS not working"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by SwiftPengu on 2012-10-19
Hello, I upgraded my Lubuntu 12.04 (which was working fine) to 12.10 today and I've encountered the following problem:

DNS does not seem to be working correctly,  it looks like the DNS settings I set in Network-Manager are not saved/used correctly.

If I type ```
nslookup [www.google.com]("http://www.google.com")
``` in a terminal window I get a timeout.

If I type ```
nslookup [www.google.com]("http://www.google.com") 8.8.8.8
``` in a terminal window I get a response.

Everything dependent on DNS is not working (firefox etc.)

It thought my router might be the culprit because sometimes DNS fails using the router, however if I type ```
nslookup [www.google.com]("http://www.google.com") a.b.c.d
``` (router ip) I get replies.

Anyway, I tried to change the DNS address in the network-manager configuration to 8.8.8.8 with DHCP enabled for the IP-address.
After reconnecting/rebooting nslookup shows the same behaviour.

I've found some info on the internet mentioning dnsmasq which might cause trouble:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1031350](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1031350)

However, I am not sure if this is the problem in my case because I do have the dnsmasq.d folder mentioned in the bug report.

Does somebody have an idea of what might be wrong?

---

### Post by SwiftPengu on 2012-10-19
As a temporary fix I was able to install wicd from the 12.04 repositories, and update it to the 12.10 version with my renewed connection.

I needed at least the following packages (I tried sudo apt-get build-dep on a ubuntu 12.04 install, and then obtained the remaining packages):
-po-debconf
-python-wicd
-wicd-daemon
-wicd-gtk

---

### Post by yngvewb on 2012-10-19
I have the same problem after upgrading Lubuntu to 12.10. Could you pleace describe in more detail how you resolved the issue? Thanks

---

### Post by SwiftPengu on 2012-10-19
Hi, unfortunately I cannot be very precise. What I did was as follows:

1.Boot into my ubuntu 12.04 install
2.Run ```
sudo apt-get build-dep wicd
```
3.Do not install anything (by selecting no when asked), but note the package names mentioned under "the following packages will be installed"
4.Use ```
sudo apt-get download [package name] [package name]
``` to obtain the .deb files for those packages
5.Boot into Lubuntu and try to install all the .deb files
6.Note any missing packages (in my case the aforementioned 4 packages)
7.Boot back in to ubuntu and download the missing packages too
8.Boot into Lubuntu and install the new packages

9.From this point it worked on my end and installed wicd instead of network-manager-gnome

The reason I cannot be very specific on the packages needed is because I used two systems with random extra software installed, so you might also need e.g. build-essentials.

Also be aware of the fact that this is only a temporary solution as this does not fix any problems but only replaces a misbehaving network manager with a different one.

---

### Post by darkod on 2012-10-19
When you set it manually in the connection options it should work. Are you sure you configured it correctly?

Also, did you change the option to Automatic (address only)? That is needed so that it accepts the manual entries for DNS servers.

PS. And, which is always a good idea, you don't have to upgrade to a new version the first day it comes out. Wait and see if people start reporting issues with it. Besides, running 12.04 which is LTS and has 5 years support, I don't understand why are you upgrading to 12.10 which has only 18 months of support anyway. Unless it has some options that you can't install or add to 12.04 (which is very rare), you don't even need to upgrade ever.

---

### Post by kevinbeard on 2012-10-23
Looks like this is a known issue.  The instructions here worked for me:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1051348]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1051348")

---

### Post by SwiftPengu on 2012-10-23
I reinstalled gnome-network-manager and removed (not purged) wicd.
My DNS is now resolving, so it might be that this had been fixed.

My /etc/resolv.conf is saying this, which is the same as it said with wicd:
```
domain lan
search lan
nameserver 192.168.1.254

```

Which points to my router (dns forwarder), however in my settings
I am using 8.8.8.8 (google dns for testing), and nslookup reports not using 8.8.8.8 but 192.168.1.254:

```
me@PC:~$ nslookup www.google.com
Server:		192.168.1.254
Address:	192.168.1.254#53

Non-authoritative answer:
Name:	www.google.com
Address: 173.194.66.103
Name:	www.google.com
Address: 173.194.66.105
Name:	www.google.com
Address: 173.194.66.147
Name:	www.google.com
Address: 173.194.66.99
Name:	www.google.com
Address: 173.194.66.106
Name:	www.google.com
Address: 173.194.66.104

```

My Network-Manager configuration is as follows:
[IMG]http://s10.postimage.org/hl0vc85l5/2012_10_23_232727_1600x900_scrot.png[/IMG]

I am thinking I am now still using my old wicd config file (I have already rebooted), and somehow it is still not overwritten.
I will try the symlink mentioned in the launchpad bug report tomorrow.

---

### Post by SwiftPengu on 2012-10-26
Since the last time I replied here, I noticed the following things:
1.If I edit /etc/resolv.conf and put the DNS server I want to use there, it is used.

2.After symlinking /run/resolvconf/resolv.conf to /etc/resolv.conf
my system uses the NetworkManager settings

```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
```

---

### Post by jdthood on 2012-10-29
> **SwiftPengu said:**
> Since the last time I replied here, I noticed the following things:
1.If I edit /etc/resolv.conf and put the DNS server I want to use there, it is used.

So to begin with /etc/resolv.conf was a plain file.

> **SwiftPengu said:**
> 2.After symlinking /run/resolvconf/resolv.conf to /etc/resolv.conf
my system uses the NetworkManager settings

```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
```

Having created this symlink you have given control of /etc/resolv.conf back to resolvconf which NetworkManager uses for maintaining resolv.conf contents.  Keep it this way.  Resolvconf is now part of the Ubuntu base system and is expected to be present. If resolvconf does not seem to be working properly in some instance then report a bug against the resolvconf package and we will investigate the issue with you.

---

### Post by Androzani1 on 2012-10-29
I had a similar problem on Windows XP. When the DNS WAS working, I copied it onto notepad. I then tweaked the settings to always use that DNS, rather than finding it automatically. If you can do something similar on Lubuntu, it may fix it.

---

### Post by SwiftPengu on 2012-10-29
> **jdthood said:**
> So to begin with /etc/resolv.conf was a plain file. created this symlink you have given control of /etc/resolv.conf back to resolvconf which NetworkManager uses for maintaining resolv.conf contents.  Keep it this way.  Resolvconf is now part of the Ubuntu base system and is expected to be present. If resolvconf does not seem to be working properly in some instance then report a bug against the resolvconf package and we will investigate the issue with you.

1.The /etc/resolv.conf file is probably a file created by wicd, and not removed after removing wicd. The settings in there were my most recent wicd settings (my home DNS server).

2.DNS seems to be working normally (automatic) now, so the only question left is why the symlink was not created during the upgrade (or why resolvconf does not simply write in /etc/resolv.conf.

---

### Post by jdthood on 2012-10-29
> **SwiftPengu said:**
> 1.The /etc/resolv.conf file is probably a file created by wicd, and not removed after removing wicd. The settings in there were my most recent wicd settings (my home DNS server).

Wicd is in universe and so it wouldn't surprise me if it (1) wasn't integrated with resolvconf and (2) even deleted the symlink at /etc/resolv.conf. I have never examined wicd so I don't know. Now on my TODO list.

> 2.DNS seems to be working normally (automatic) now, so the only question left is why the symlink was not created during the upgrade.

Resolvconf only creates the symlink /etc/resolv.conf -> ../run/resolvconf/resolv.conf on initial installation. If resolvconf were to create this symlink again on upgrade then the people who like to delete the symlink would complain.

To force the resolvconf package to create the symlink, run "dpkg-reconfigure resolvconf".

> (or why resolvconf does not simply write in /etc/resolv.conf).

Writing to files in /etc is a violation of the filesystem hierarchy standard and needlessly prevents the root filesystem from being mounted read-only.

---

### Post by piemonkey on 2012-12-02
Putting in the symlink fixed dns for me. The weird thing was that this was on a brand new (customised using Ubuntu Customisation Kit) Lubuntu live usb.

I dunno if it was broken out of the box or if UCK broke it. Once I get a fully working laptop (broken hdd, hence live usb) I'll investigate.

---

### Post by jdthood on 2012-12-04
> **piemonkey said:**
> Putting in the symlink fixed dns for me. The weird thing was that this was on a brand new (customised using Ubuntu Customisation Kit) Lubuntu live usb.

I dunno if it was broken out of the box or if UCK broke it. Once I get a fully working laptop (broken hdd, hence live usb) I'll investigate.

Custom Ubuntu builds based on Precise frequently have this problem. See bug #1000244,

[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)

for example, comment #82.

[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82)

---

