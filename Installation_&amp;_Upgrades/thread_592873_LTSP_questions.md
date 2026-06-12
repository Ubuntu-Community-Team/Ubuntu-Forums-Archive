---
title: "LTSP questions"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by dwf_starband on 2007-10-26
Can the server still be used as a desktop?
Can it be installed on an existing desktop?

I saw a drawing showing internet comming into the server which was then connected to a switch which connected to the clients.  Does the server have to be the one assigning dhcp addresses?  

I have my internet comming into an xp computer which is sharing the internet into my wired/wireless router. (I have starband and it requires software on xp for my internet to work)

If my ubuntu server is connected to the router with a static ip will the clients be able to use dhcp assigned by the router?

thanks,

dennis

---

### Post by SpiritIsReality on 2007-10-26
howdy
I'm workin' on a similar setup.
edit: got ltsp working here:
[http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166)


2 nic cards on server
1 card is server access to internet
1 card is to be a subnet to thinclients, cable to switch.
going by these pages, 
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
[https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)
getting started, 
> Getting Started
NOTE: If you plan to use the server as gateway/nat/firewall machine, it is strongly suggested to configure all the network interfaces before proceeding with the following steps. 
but I am not sure how to set up the nic card to the ltsp clients
I'm guessing that a different subnet would work.
the answer lies here I reckon
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)
subnetting.

> Can the server still be used as a desktop?
Can it be installed on an existing desktop?
affirmitive. I've got that far. but sound does not work on server.
edit: sound on ltsp server desktop works. I did not change anything,
so it was probably an update fix. tx

> Does the server have to be the one assigning dhcp addresses? 
it doesn't have to be, but I ran into problems with the router giving out dhcp
and then not having the ltsp to go with it. If you can set the router to hand off the thinclienthttp://ubuntuforums.org/showthread.php?t=494242
booting to an alternate, that's supposed to work,
[http://www.google.ca/search?hl=en&q=ltsp+multiple+dhcp+servers&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=ltsp+multiple+dhcp+servers&btnG=Search&meta=)
 but I'm trying to go for a internet to router, router serving lan as well as the server, then a subnet with
the server handing out dhcp to the thinclients.
I reckon the steps on changing the ip's handed out here is worth a shot
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

other helps
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ltsp&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ltsp&titlesearch=Titles)
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring)

[http://www.edubuntu.org/Documentation](http://www.edubuntu.org/Documentation)
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)
[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-theory.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-theory.html)
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html)
2 nic
[http://ubuntuforums.org/showthread.php?t=326711](http://ubuntuforums.org/showthread.php?t=326711)
[http://ubuntuforums.org/showthread.php?t=494242](http://ubuntuforums.org/showthread.php?t=494242)

trails
buds

did this  
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
[https://help.ubuntu.com/community/LTSPServerSetup](https://help.ubuntu.com/community/LTSPServerSetup)
Edit /etc/network/options and enable ip_forward. The result would look like:
ip_forward=yes
spoofprotect=yes
syncookies=no
and execute:
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
to enable the kernel ip forwarding functionality immediatly.
from here [https://wiki.edubuntu.org/ThinClientHowtoNAT](https://wiki.edubuntu.org/ThinClientHowtoNAT)

I had to customize the x server to the client,
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html)
but instead of using /opt/ltsp/i386/etc/lts.conf the  /opt/ltsp/i386/etc/lts.conf
file told me to 
fred@piii:~$ cat /opt/ltsp/i386/etc/lts.conf
# This is the default lts.conf file for ltsp 5.
# For more information about valid options please see:
# /usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz
# in the client environment.
#
# Note that things like sound and local device support are
# auto-enabled if the corresponding packages are installed,
# there is no need to manually set these options anymore.
#
# **** THIS FILE SHOULD NO LONGER BE USED FROM HERE !!! ****
#
# With the introduction of the nbd/unionfs/squashfs structure
# the lts.conf file moved to the tftp root please create:
# /var/lib/tftpboot/ltsp/i386/lts.conf instead for your changes
#
# In case you want to use the lts.conf here, this still works,
# but you need to run ltsp-update-image after every change.
[default]
  LTSP_VERSION=5.0.39
_________________________
so I did this:
 cd /var/lib/tftpboot/ltsp/i386/
sudo touch lts.conf
gksudo gedit /var/lib/tftpboot/ltsp/i386/lts.conf and added the HWADDR of the clients nic card
(I reckon I found that when the floppy booted and it couldn't connect to the xserver but I could read the
hardware address off the screen.) and some customizing, from here
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html)
[http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo#head-341afa0033cdef8187af227d9188b4742c47beee](http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo#head-341afa0033cdef8187af227d9188b4742c47beee)
[http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo/NetworkClients](http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo/NetworkClients)

[00:40:f4:51:66:66]
XSERVER = ati
X_MODE_0 = 600X800
X_HORZSYNC = "30-70"
X_VERTREFRESH = "50-130"
------------------------------
it still needs some work, but it works.
_______________________

used dhcp.conf 
fred@piii:~$ cat /etc/ltsp/dhcpd.conf
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.5 192.168.1.20;
    option domain-name "*";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.0.254;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
______________________________
server has 2 nic cards
fred@piii:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:28:E2:BA  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe28:e2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15924787 (15.1 MB)  TX bytes:2181924 (2.0 MB)
          Interrupt:11 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:85:FF:65  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe85:ff65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8088543 (7.7 MB)  TX bytes:44011606 (41.9 MB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16767964 (15.9 MB)  TX bytes:16767964 (15.9 MB)
_______________________
/etc/network/interfaces
fred@piii:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface from server to router to internet
auto eth0
iface eth0 inet static
        address 192.168.0.140
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

# The secondary network interface to switch to clients
auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
         # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
___________________________
error message on client
This workstation isn't authorized to connect to server

ltsp This workstation isn't authorized to connect to server
----------
[http://www.google.ca/search?hl=en&q=%22This+workstation+isn%27t+authorized+to+connect+to+server%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22This+workstation+isn%27t+authorized+to+connect+to+server%22&btnG=Google+Search&meta=)

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296)
... 
 bazz wrote on 2007-09-24: (permalink)

I forgot....I didnt post that "This workstation isn't authorized to connect to server" as a bug because I dont know as if it would be one. I looks to me as if its a control that would need to be set up.

 Oliver Grawert wrote on 2007-09-24: (permalink)

to get rid of that message, run sudo ltsp-update-sshkeys and sudo ltsp-update-image (in this order) it should be gone then
-----
ran 
sudo ltsp-update-sshkeys
sudo ltsp-update-image

fred@piii:~$ sudo ltsp-update-sshkeys
[sudo] password for fred:
fred@piii:~$ sudo ltsp-update-image
Parallel mksquashfs: Using 1 processor
Creating little endian 3.0 filesystem on /opt/ltsp/images/i386.img.tmp, block size 65536.
[==========================================================  ] 19490/19887  98%
Exportable Little endian filesystem, data block size 65536, compressed data, compressed metadata, compressed fragments, duplicates are removed
Filesystem size 160809.37 Kbytes (157.04 Mbytes)
        42.38% of uncompressed filesystem size (379444.06 Kbytes)
Inode table size 201623 bytes (196.90 Kbytes)
        32.76% of uncompressed inode table size (615367 bytes)
Directory table size 177545 bytes (173.38 Kbytes)
        53.63% of uncompressed directory table size (331055 bytes)
Number of duplicate files found 1117
Number of inodes 18679
Number of files 15609
Number of fragments 1907
Number of symbolic links  996
Number of device nodes 86
Number of fifo nodes 2
Number of socket nodes 0
Number of directories 1986
Number of uids 5
        root (0)
        syslog (101)
        fred (1000)
        news (9)
        klog (102)
Number of gids 15
        video (44)
        audio (29)
        tty (5)
        kmem (15)
        disk (6)
        adm (4)
        shadow (42)
        dhcp (101)
        fuse (106)
        utmp (43)
        staff (50)
        src (40)
        mail (8)
        fred (1000)
        klog (103)
Info: port 2000 is already defined with /opt/ltsp/images/i386.img in inetd.conf
Info: taking no action.
fred@piii:~$ 

login from ltsp client
user fred
passwd ******
login to server from ltsp client successful.

login from ltsp client
user user1
passwd ********
passwd fails

possible reason is the user1 was added by
chroot /opt/ltsp/i386 
# adduser user1
_________________

added user2 to server's root

System -> Administration -> Users and Groups 

+Add User

login from ltsp client
user user2
passwd *******
login to server from ltsp client succes

---

