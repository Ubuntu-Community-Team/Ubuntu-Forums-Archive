---
title: "apt-get update problems"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by quartzeye on 2006-10-17
2nd try at this.  It would be nice if it didn't kill my post because I didn't have a tag and just let me add one!

I have neen tryiong to get the Ubuntu-Server 6.06 running by following the "Perfect Setup" how to.  No matter what I do I run into problems running the apt-get update command in the how-to.  I have editted the "sources.list" file a number of times.  I have tried both US and DE repositories.  I also have tried the IP address for both the US and DE repositories.  All I get are the following type of errors:

99% [13 Sources bzip2 0] [15 Sources 0]bzip2: (stdin) is not a bzip2 file.
Err [http://141.76.2.3](http://141.76.2.3) dapper/restricted Sources
  Sub-process bzip2 returned an error code (2)

and

Failed to fetch [http://141.76.2.3/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://141.76.2.3/ubuntu/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)


I do not know what to do as I am far from proficient in the 'nix world.  Additionally the how to earlier has me setup the NIC and tells me that when I run the hostname command with and witout the -f argument that I should see server1.example.com.  This has got to be wrong as the how to clearly shows me that I am entering a shortname and a fully qualified URL.  When I run the hostname command I get server1, as I would expect. With the -f argument I get the fully qualified URL, server1.example.com.  Am I right or is there something missing from the how to?

I am pretty certain the NIC is configured properly as I can ping the URL's to get the IP address's.

Any help would be greatly appreciated as I am ready to pitch all this.

Thanks
quartzeye

---

### Post by mssever on 2006-10-18
Could you post the contents of your sources.list, as well as a little more context of your error? It almost appears that you've gotten an invaiid package somehow, but it's hard to say without a little more info.

---

### Post by quartzeye on 2006-10-18
Everything is exactly as shown in the how-to.  Except for the URL in the hosts file.  I downloaded the current release on Saturday afternoon.  I am also attempting to install this into a VMWare Ubuntu virtual machine.

My interfaces look like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

My hosts file looks like this:

127.0.0.1       localhost.localdomain localhost
192.168.1.100   server1.ischeme.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

My sources.list file started out something like this:

#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


I tried using the following :
   "archive.ubuntu.com" instead of "us.archive.ubuntu.com",
   "de.archive.ubuntu.com" instead of "us.archive.ubuntu.com",
   "146.137.96.15" instead of "us.archive.ubuntu.com",
   "141.76.2.3" instead of "de.archive.ubuntu.com",
   "82.211.81.138" instead of "security.ubuntu.com"
I did not try "195.248.98.54" instead of "archive.ubuntu.com".

Each time I received a number of errors similar to the following:

99% [13 Sources bzip2 0] [15 Sources 0]bzip2: (stdin) is not a bzip2 file.
Err [http://141.76.2.3](http://141.76.2.3) dapper/restricted Sources
Sub-process bzip2 returned an error code (2)

The only differnce in the errors was number of sources in that the "13" and "15" was different but the "0" was the same as was the error code  and the "not a bzip2 file" message.

Also received the following errors:

Failed to fetch [http://141.76.2.3/ubuntu/dists/dappe...6/Packages.bz2](http://141.76.2.3/ubuntu/dists/dappe...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

These error messages were pretty much all I received.  There were other non descript messages but not related to any single repository or package  and no packages were found or downloaded.

I cannot upload the actually output as I will not be at that machine till later this evening.  Suffice it to say there didn't seem to be any other information in the output that indicated the cause of this situation just adminstrative messages.  I'll upload what ever anyone wants but you gat all that is relevant right here.

I also tried to use apt-get to install a number of packages like the following:
   apt-get install binutils 
   apt-get install cpp 
   apt-get install fetchmail 
   apt-get install quota

All I got was a message stating that the package could not be found or was obsolete.  I even tried running "aptitude update" and got a similar message about not finding the package

I am obviously not able to properly connect to any repository.  Why, i do not know.  I can ping the URL and get the IP address.  From what I can tell the "update" is connecting to the repositiry but is not reading it correctly.  Once again, I do not know why.  I have followed the tutorial to the letter and have hit this wall.  Something is amiss and I am really uncertain how to fix this problem.  I will upload and try what ever anyone wants but this is all there is at this point.

Thanks
quartzeye

---

### Post by quartzeye on 2006-10-18
Just a side not.  Since I am trying to install the Ubuntu-Server as a guest OS, I know I need to install the vmtools package at some time.  Could the problem I am having be related to the fact that I do not have the tools installed yet?

At what point should you install these tools?  Right after the installation CD is done and you reboot?  After you attempt to configure the OS, like I am doing?  After you have the NIC and hosts file set?

Thanks
quartzeye

---

### Post by mssever on 2006-10-18
I don't think that your problem is network-related. It looks like there's something wrong with bzip2--though I can't say what. Am I correct in assuming that this is a fresh install? If so, then it seems like you must be experiencing some sort of issues with your hardware. It could also be related to running inside a VM. I've never used vmware or similar, so I can't help you there.

In short, I'm stumped. If you continue to have problems with Ubuntu, you might consider changing distros.

---

### Post by kjbetz on 2006-10-18
I'm not sure if this helps or not... but this week I too installed Ubuntu 6.06 Server on a VMware setup. I did not have the problems you are describing and I did not install the "tools" you speak of.

It looks to be an issue with bzip, maybe?

Sorry, not much help.

---

### Post by quartzeye on 2006-10-19
Ok.  I created a new VM.  Downloaded the iso from a different location and I still have the same problem.  Here is the results.

login as: admin
admin@192.168.1.100's password:
Linux server1 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Thu Oct 19 20:10:28 2006
admin@server1:~$ sudo apt-get update
Password:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
97% [1 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdi
n) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
98% [2 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdi
n) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
99% [4 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin
) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Sub-process bzip2 returned an error code (2)
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
99% [6 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Sub-process bzip2 returned an error code (2)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
99% [5 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Sub-process bzip2 returned an error code (2)
99% [8 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
99% [7 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
99% [10 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Sub-process bzip2 returned an error code (2)
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
99% [9 Sources bzip2 0] [13 Sources 0]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Sub-process bzip2 returned an error code (2)
99% [11 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Sub-process bzip2 returned an error code (2)
99% [12 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 fil
e.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
99% [13 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Sub-process bzip2 returned an error code (2)
99% [14 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 fil
e.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
99% [15 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 fil
e.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
99% [16 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
99% [17 Sources bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Fetched 3485B in 0s (6414B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin)
ary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict)
ed/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou)
rce/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict)
ed/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe)
/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe)
/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38)
6/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina)
ry-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou)
rces.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour)
ce/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary)
-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source)
/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/bi](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/bi)
nary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric)
ted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so)
urce/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric)
ted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used
 instead.
admin@server1:~$



Anyone have any ideas???

---

### Post by mssever on 2006-10-19
What happens if you type ```
cp /etc/apt/sources.list crud && bzip2 crud; ls
```If the above command succeeds, then try ```
bunzip2 crud.bz2; ls
```

---

### Post by quartzeye on 2006-10-20
I'll try that tonight when I get home.  I did notice last night, right before I shut everything down, that when I PING any URL outside the firewall I get the gateway IP address returned.  Also when I PING the IP outside the firewall it times out.  I have no problem from the host OS.  It gets out to the internet with out any problems.

I have disabled IPV6 and I can connect to the server form any PC on the LAN.  I can also PING any PC on the LAN from the server.  My router is a Netopia DSL modem/router/firewall/dhcp yadda, yadda, yadda.  That said, my network and hosts are as follows, is there anything here that could be causing this?

My interfaces look like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

My hosts file looks like this:

127.0.0.1 localhost.localdomain localhost
192.168.1.100 server1.ischeme.com server1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by colgate on 2006-10-21
It happened to me when I've tried to change repositories address 
from
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

to
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
or any other *.archive

when I returned to the original line ([http://archive](http://archive)...) It all worked again.
I think it can be a problem related to servers's gpg keys; but I'm not sure.

I hope this can help.

Federico

---

### Post by quartzeye on 2006-10-23
At this point I do not know where the problem lies.  Tonight I am going to set up the host OS as a static IP and pull the DNS entries off the router so that it does not proxy the DNS lookups.

I am then going to reinstall a new guest OS and verify that the IFCONFIG returns the correct addresses.  I will then try to update the Ubuntu guest OS.  

Next I will attempt to change the network settings so that they are static.  Could someone look at my network settings in the above post and tell me what to change so that the primary and secondary DNS entries are present?

Finally I need to verify that the router is seeing the static IP for the Ubuntu guest OS.  The last time I checked I could see all the computers on the LAN except the Ubuntu guest.  I could ping it and connect to it but the router was not able to list it.  Is this a broadcast issue?  Are my network settings correct?  I will do an IPCONFIG on the host OS and verify that the settings are the same in the Ubuntu guest OS.

I will post my findings later and thanks in advance for any help it properly setting up the network interface.

Quartzeye

---

### Post by mssever on 2006-10-23
Your DNS settings live in /etc/resolv.conf. Here's mine for reference: ```
search local
nameserver 192.168.1.50
``` You can have as many nameserver lines as you need. The search line gives your domain. All my machines have domain names ending in .local (initially set up via /etc/hosts; now I run my own DNS server), so if I want to ping my desktop, I type ping scott-desktop.local. The search line allows me to abbreviate it as ping scott-desktop.

If you use DHCP, your router will likely overwrite your resolv.conf with whatever DNS settings it wants to use. You need to configure it not to do that, or do something like ```
sudo chmod a-w /etc/resolv.conf
``` once you've set the proper settings.

I'm not sure if you know how to set up a static IP, so I'll post part of my /etc/network/interfaces: ```
auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
``` The gateway should be your router's IP address. My router didn't balk at all when I used a static address. Your results may vary.

---

### Post by newrhyme on 2006-10-24
I too am having problems with the "apt-get update"!?!
It will NOT allow the actual download AND install of the update files!
I am NOT using VMWARE or trying to administer a server, but, am also using DAPPER (v.6.06)
Could it be that, in the process of CVS, the servers for Edgy ONLY SEE Edgy requests?

Just a thought.

My "work around" has been to enter, THROUGH THE COMMAND LINE, the software packages I wanted, and, then, installing them, w/ SYNAPTIC,.,..once again...THROUGH "su" AND THE COMMAND LINE.

For some reason, my installation of Ubuntu DAPPER does NOT give me "root" access through "sudo".  Here are the errors I get, trying to get "sudo" to be of use with the usual "sudo apt-get update";

Err http: dapper Release.gpg
  Unable to connect to  http:
Err http: dapper-backports Release.gpg
  Unable to connect to  http:
Ign http: dapper Release
Ign http: dapper-backports Release
Ign http: dapper/main Packages
Ign http: dapper/restricted Packages
Ign http: dapper/main Sources
Ign http: dapper/restricted Sources
Ign http: dapper/universe Packages
Ign http: dapper/universe Sources
Ign http: dapper-backports/main Packages
Ign http: dapper-backports/restricted Packages
Ign http: dapper-backports/universe Packages
Ign http: dapper-backports/multiverse Packages
Ign http: dapper-backports/main Sources
Ign http: dapper-backports/restricted Sources
Ign http: dapper-backports/universe Sources
Ign http: dapper-backports/multiverse Sources
Err http: dapper/main Packages
  Unable to connect to  http:
Err http: dapper/restricted Packages
  Unable to connect to  http:
Err http: dapper/main Sources
  Unable to connect to  http:
Err http: dapper/restricted Sources
  Unable to connect to  http:
Err http: dapper/universe Packages
  Unable to connect to  http:
Err http: dapper/universe Sources
  Unable to connect to  http:
Err http: dapper-backports/main Packages
  Unable to connect to  http:
Err http: dapper-backports/restricted Packages
  Unable to connect to  http:
Err http: dapper-backports/universe Packages
  Unable to connect to  http:
Err http: dapper-backports/multiverse Packages
  Unable to connect to  http:
Err http: dapper-backports/main Sources
  Unable to connect to  http:
Err http: dapper-backports/restricted Sources
  Unable to connect to  http:
Err http: dapper-backports/universe Sources
  Unable to connect to  http:
Err http: dapper-backports/multiverse Sources
  Unable to connect to  http:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Fetched 2B in 1s (1B/s)
Failed to fetch [http:///ubuntu/dists/dapper/Release.gpg](http:///ubuntu/dists/dapper/Release.gpg)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/Release.gpg](http:///ubuntu/dists/dapper-backports/Release.gpg)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper/universe/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper/universe/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper/universe/source/Sources.gz](http:///ubuntu/dists/dapper/universe/source/Sources.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz](http:///ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/main/source/Sources.gz](http:///ubuntu/dists/dapper-backports/main/source/Sources.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http:///ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/universe/source/Sources.gz](http:///ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Unable to connect to  http:
Failed to fetch [http:///ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http:///ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Unable to connect to  http:
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Actually...I am glad that I'M NOT THE ONLY ONE, here...with this problem.
I was starting to get paranoid!

Hope this helps, and, if someone finds the answer, please reply to this post, so that I will know there is a "fix" for the problem.

Thanks, in advance...

---

### Post by mssever on 2006-10-24
> **newrhyme said:**
> My "work around" has been to enter, THROUGH THE COMMAND LINE, the software packages I wanted, and, then, installing them, w/ SYNAPTIC,.,..once again...THROUGH "su" AND THE COMMAND LINE.
I don't understand. Could you give an example, providing the commands you use?
> For some reason, my installation of Ubuntu DAPPER does NOT give me "root" access through "sudo".
Make sure that you're a member of the admin group (/etc/group should contain [FONT="Courier New"]admin:x:112:yourusername[/FONT]). Also make sure that /etc/sudoers contains the line ```
%admin ALL=(ALL) ALL
``` (To edit this file, use [FONT="Courier New"]sudo visudo[/FONT] or [FONT="Courier New"]su -c visudo[/FONT])
> Here are the errors I get, trying to get "sudo" to be of use with the usual "sudo apt-get update";

Err http: dapper Release.gpg
  Unable to connect to  http:
Err http: dapper-backports Release.gpg
  Unable to connect to  http:
Weird. Check your apt settings. Also, some people have problems with IPv6 and end up disabling it.

---

### Post by quartzeye on 2006-10-25
Ok.  Why is this harder than it has to be.  Not to whine to loudly but damn Windows is easier to setup.

I still do not have the network working and have scoured this forum trying almost everything I found with out any success.  Here is where I am at.

I created a new Ubuntu guest OS.  When the OS rebooted after the install, I could see the MAC address of the virtual NIC on the router.  I was able to use apt-get and updated the OS.

I then tried to change the interfaces from DHCP and set up a static IP.  Here is my interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 66.112.11.87 64.91.3.46

I restarted eth0 using,  sudo ifdown eth0 && sudo ifup eth0.  I lost internet connectivity but not the LAN.  I also lost the MAC in the router.  I updated the resolv.conf and write protected it with out any success.  The resolv.conf is as follows:

search Linux
nameserver 192.168.1.1
nameserver 66.112.11.87
nameserver 64.91.3.46

I can ping the router and any IP on the LAN and also connect to the Ubuntu guest OS from any PC on the LAN.  I cannot resolve any URL or IP outside the router or see the MAC of the Ubuntu guest in the router. Pinging a WAN URL returns the router, 192.168.1.1, and pinging a WAN IP timesout.

I have tried traceroute6 on URL's and IP's and get the following:

admin@server1:~$ traceroute6 192.168.1.1
traceroute: unknown host 192.168.1.1
admin@server1:~$ traceroute6 [www.google.com](www.google.com)
traceroute: unknown host [www.google.com](www.google.com)

The ifconfig -a returns this:

admin@server1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:29:5A:C5:75
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe5a:c575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:556948 (543.8 KiB)  TX bytes:445960 (435.5 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Obviously something is not right with my networking but I cannot find anything wrong that someone else hasn't said this works.  Anyone really know what is going on or do I keep plugging away at this and hope that I Forest Gump my way into a solution?

Thanks in advance
Quartzeye

---

### Post by mssever on 2006-10-25
Not that this is any consolation, but you're having more trouble installing than most. Don't know why. For many people, Ubuntu is much easier to install than Windows.

As far as your network connectivity problem goes, it does sound like DNS problems. nslookup and dig are good tools to see what's going on DNS-wise.

Just remembered something. You said that you can't resolve any URL or IP outside the router. Does that mean that you can't ping yahoo's IP (66.94.234.13)? If so, I suspect that your router is misconfigured.

---

### Post by quartzeye on 2006-10-25
You are correct.  I cannot ping Yahoo's, Google's, the WAN IP for my router, or any other IP outside the router.  Only the Ubuntu OS cannot do this.  All the other Windows PC's and servers, including the host windows server can do this.  Additionally, I could do this from the Ubuntu OS prior to configuring the interfaced file for a static IP.

All the files are in the prior post as well as the results of the standard troubleshooting commands.

Look, all I did was change the interfaces file as shown in my prior post.  Bam, all the internet connectivity went a way. Logically something is wrong with these settings.  I fail to see where they are wrong but no one else seems to be able to see anything wrong either.

So if the only thing I changed was this file then WHY would it be the router?  I'll enumerate the steps again.

1) install Ubuntu - OK
2) install openssh - OK
3) run apt-get update - OK
4) run - apt-get upgrade - OK
5) check router and find IP for MAC - OK
6) change interfaces file for static IP - OK
7) restart network - OK
8) check internet connectivity - FAIL
9) run apt-get update - FAIL
10) check router and find IP for MAC - FAIL old IP for MAC still present
11) run ifconfig -a  - OK see new static IP everything looks OK
12) open ssh session to new IP - OK
13) ping new IP - OK
14) ping LAN IP's from Ubuntu - OK
15) ping [www.google.com](www.google.com) - OK but get the router IP not the correct IP
16) ping Google’s IP address - FAIL times out
17) ping WAN IP for router - FAIL times out
18) change resolv.conf file to add dns-nameservers - OK
19) write protect resolv.conf file - OK
20) restart eth0 interface - OK
21) reconnect ssh session - OK
22) check router and find IP for MAC - FAIL not present
23) restart Ubuntu - OK
24) repeat step 12 thru 17 and 22 - FAIL same results

So how thorough am I being?  Did I miss anything?  My files and results are in the prior post, is there something wrong with them?  I have tried three separate downloads from three separate mirrors.  There is no problem with the ISO.  There is no problem with the HOST OS.  There is no problem with VMWARE.  There is no problem with the LAN.  There is no problem with the router.  There does not seem to be a problem when using DHCP.  The problem occurs after I try to set up eth0 with a static IP.  I have followed every instruction that I can find step by step and it does not work.  Can a network EXPERT tell me what I am doing wrong or tell me what to do to diagnose the problem?  Do I have to change more files thatn the interfaces file?  Do I need to change the resolv.conf file?  Are my IP settings wrong?  Why would the router still see the old DHCP assigned IP for the MAC after I restarted eth0.  Seems like something did not change, what could that be and why?  IF this is an IPV6 issue why would the router ever see any IP for the MAC and why would apt-get work while using the DHCP assigned IP?  

I have seen a lot of posts on these forums that seem to be folks shooting from the hip to try this or that.  That is all good for doing something, but not real helpful in trying to logically understand the cause and effects of the steps taken  Sorry if I a being little anal about this but the first rule of troubleshooting is identify what has changed.  I have done that, the interfaces file.  The next steo is too see if you can reproduce the problem.  I have done that, reinstalled the OS three times taking the same steps with the exact same results.  Next identify what effects the changes had that contributed to the problem.  I cannot do that because Ubuntu and Unix are not my area of expertise.  I appreciate the try this and that approach but could you at least explain why this or that might work.  

The only way I will ever learn how to do something is to know why you do something.

Thanks
Quartzeye

---

### Post by mssever on 2006-10-25
As you've no doubt realized, I'm no network expert. I hope a network expert will see this thread and reply. These forums are great for common problems, but when you get to the unusual, it's often difficult to find someone who knows enough to provide a difinitive answer. When I shoot from the hip, it's because I don't know the answer right off, but I'm trying to iteratively solve/identify the problem. And I usually look for older unanswered threads that are unlikely to get an answer otherwise.

As far as not posting explanations goes, I can't speak for others, but I can tell you why I often don't explain. I can help more people if I don't take the time to go into the details, and many people seem to care only that their problem is solved. If you ask for an explanation, I'm sure you'll get one.

Your network settings look perfectly fine to me. I use similar settings successfully. The only other troubleshooting step on your Linux install that I can think of is "dig google.com" which will attempt to do a DNS lookup. I'm pretty sure that that will fail, though since you doubtless can't see your DNS servers' IPs, either.

Given that your settings look fine, and given that your problems started when you switched to a static IP, I suspect that your router may be at fault here. Here's why:[LIST]
[*]I'm out of other options ;)
[*]My router has various MAC address-based security settings. It's possible that your router doesn't like to forward connections from MAC addresses that it hasn't assigned via DHCP. Your VM has a different MAC address than the actual card on the host computer, I think.[/LIST]Here's something that might help to isolate the problem--if your router and (DSL|cable) modem are separate units.[LIST=1]
[*]Note your external IP (you can find that fron whatismyip.com)
[*]Connect your Linux machine directly to the modem, bypassing your router.
[*]Set your static IP to your external IP and restart the network interface.
[*]If you can see the outside world now, that proves that the router is at fault. If not, the test is inconclusive. It could mean: a) your modem doesn't like having two netcards connected (due to your VM setup) b) your ISP doesn't like your VM's MAC address; or c) your network settings are indeed wrong somehow.[/LIST]Most of the networking-related problems I've seen here have been the fault of a router.

Just thought of something else: If your router can be so configured, you might tell it to assign a particular IP to your virtual MAC address. Then re-enable DHCP and the result will be nearly identical to having a static IP.

---

### Post by newrhyme on 2006-10-25
I just go into " root" w/ su...
THen, I have to type in, through the root shell, the name of the command application I want...for instance:

   "su ..." "passwd" "synaptic"...brings up the Synaptic Package Manager.


[QUOTE=mssever;1655017]I don't understand. Could you give an example, providing the commands you use?

---

### Post by mssever on 2006-10-25
> **newrhyme said:**
> I just go into " root" w/ su...
THen, I have to type in, through the root shell, the name of the command application I want...for instance:

   "su ..." "passwd" "synaptic"...brings up the Synaptic Package Manager.


[quote=mssever;1655017]I don't understand. Could you give an example, providing the commands you use?[/quote]

su works, provided that you've enabled the root password. But sudo is preferable to su--so unless you broke sudo, no workaround is necessary since this is the way Ubuntu works by default.

To check that sudo is working, type ```
sudo id -un
``` It should say root. If it doesn't, then make sure that your username is listed in /etc/group as a member of the admin group and that /etc/sudoers contains ```
%admin ALL=(ALL) ALL
``` (use visudo to edit sudoers).

---

