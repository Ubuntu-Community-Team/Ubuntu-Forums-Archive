---
title: "failure to fetch from archives"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2007-01-17
I have been unable to download updates, software from the archives. When I used Synaptic I received the following error message:                                                                               
                                                                                                                                                                      W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.10-0ubuntu11.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.10-0ubuntu11.1_i386.deb)
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)                                                                                                                                                                                                                                                                                                                                                                                                                          When I used Add/Remove I received the identical error message and using Update Manager the message was as follows:                                                                                               W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.06_i386.deb)
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)                 If there is anyone out there that might have come across this and has a remedy I would appreciate some help on this one. oh yeah, I still have Super User administrative rights (sudo) and my password is accepted by all applications, Synaptic, Add/Remove, and Update Manager. This really has me puzzled, please help.](*,)

---

### Post by bapoumba on 2007-01-17
Hello,
do you have a proxy installed ?
What is the output to ```
cat /etc/apt/apt.conf
``` and ```
cat /etc/environment
``` ?

---

### Post by dsimpson on 2007-01-17
I don't really understand what proxy settings are and how to change them. I have the following on my outputs, hope this will tell something that is helpful, in the meantime I will check the post concerning proxy settings and see if I can discover a solution there.                                                            

Here is my output from; cat /etc/apt/apt.conf

Acquire {http::proxy "http://127.0.0.1:8080/"}


and from; cat /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en"
:-?

---

### Post by bapoumba on 2007-01-17
How are you connected to internet ? Is this your private router or a corporate or school connection ?

If you are sure there is no proxy, then your /etc/apt/apt.conf file should be :
```
ACQUIRE {http::proxy "direct"};

```

To edit, open the file with nano (a small text editor) : **sudo nano -B /etc/apt/apt.conf**. -B will backup your file with ~ extension.
Replace the content with the line above. CTRL + O (like in Ocean) to save the file with the same name, CTRL + X to exit.

It sometimes gets a couple **sudo aptitude update** (or **sudo apt-get update**) for package manager to pick it up (I do not know why, happens quite often to me).

---

### Post by dsimpson on 2007-01-17
I tried the change you suggested, opened nano saved the changes and when it came to control-x, nothing seemed to happen, was I supposed to save it to file before exiting? Can this be accomplished through a gui on Ubuntu such as system/preferences/network proxy? When I look in there is says "Proxy Configuration" - Direct connection, and in "Advanced Configuration" - localhost, */local, and 127.0.0.1..

I am trying but will need to be walked through most of the changes, sorry for the lack of knowledge but I am learning slowly.:(

---

### Post by bapoumba on 2007-01-17
No problem :)
In nano, once you have made the changes to the file, CTRL-O (like in Ocean) will save the file, hit <Enter> to save with the same name. Then CTRL-X.

---

### Post by dsimpson on 2007-01-17
Success!!! Thank you very much.... and all this without me remembering to give you all the details. I just remembered that it seemed to start when I uninstalled automatix, which wasn't supported by Dapper, or the other way around, anyway it didn't work with my distro, and after I did that it seemed to go awry. Thank you, Bapoumba, now on to the next problem, ha! ha!, it seems neverending...:D

---

### Post by bapoumba on 2007-01-17
You're welcome :)
And the problems will end, eventually, you can trust me on this. When I installed warty (first Ubuntu release), I had very very little knowledge about all of this ;)

---

### Post by dsimpson on 2007-01-18
Bapoumba, the problems are hanging around, I will probably post this under a new heading tomorrow, but following the fix, I lost my opendns settings and my internet connection was lost, I reset to the default and am back online but things are running a little slower again as a result of losing my opendns settings. On to the new problems, tally ho!:-?

---

### Post by bapoumba on 2007-01-18
Hi,
DNS are set up in /etc/resolv.conf. What do you have in that file ? (**cat /etc/resolv.conf**) ?
What kind of router do you have ?

---

### Post by ovat on 2007-01-18
Sorry to ask you , but I have similar problem , not sure it is the same ...
It doesnt matter is it from update ot Synaptic I am getting error like:

[B]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_386.deb)
Could not resolve '192'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt-mt_3.3.6-1ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt-mt_3.3.6-1ubuntu6.1_i386.deb)
Could not resolve '192'
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.2-0ubuntu1_i386.deb)
Could not resolve &#8216;192.&#8217;
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.10-0ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.10-0ubuntu3.4_i386.deb)
Could not resolve &#8216;192.&#8217;[/B]

I think update is giving me as a result

[B]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb)
  Could not resolve &#8216;192.&#8217;


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.1-2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.1-2ubuntu2.1_i386.deb)
  Could not resolve &#8216;192.&#8217;[/B]

On _cat /etc/apt/apt.conf_ I am getting :
ACQUIRE {http::proxy "direct"};

and on  cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"

I tried what u said before..and for some reason I am not sure that I could find the back up file...:) 

I will be glad if you could give me some advice ...
 :D

I am using router SAR-110 , personal

---

### Post by bapoumba on 2007-01-18
If running GNOME, check System > Preferences > Network proxy, should be set to direct. If running KDE, well you'll have to look for the proxy menu ;)

What is the output to :
```
cat /etc/resolv.conf
cat /etc/network/interfaces
ifconfig
```

---

### Post by ovat on 2007-01-18
Hi I have a router , it was in stealth mode , but even when I tried to open the ports didnt work..or at least I think so ; I am using GNOME , Yes already I found that and put it in Direct I-net

oem@dom:~$ cat /etc/resolv.conf
nameserver 82.195.96.46
nameserver 82.195.96.5


oem@dom:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.7.3
netmask 255.255.255.0
gateway 192.168.7.1



iface eth0 inet static
address 192.168.7.2
netmask 255.255.255.0
gateway 192.168.7.1

auto eth0



oem@dom:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:82:44:2B
          inet addr:192.168.7.2  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe82:442b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:622537 (607.9 KiB)  TX bytes:172335 (168.2 KiB)
          Interrupt:193 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:360 (360.0 b)  TX bytes:360 (360.0 b)


But after I made it Direct I-net conection is giving me:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  Could not connect to 192.168.7.1:3128 (192.168.7.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb)

and so on - does that mean that my router is stoping the outgoing and maybe ingoing packets..? If that so - how to open and which ports ..just 3128 or it doesnt matter the Nrr..?

---

### Post by dsimpson on 2007-01-18
Hello again, been gone all day but now will pass on the info you asked about bapoumba, here is the printout from my (/etc/resolve.conf). I am using a Belkin router, and I followed the Linux instructions for Ubuntu for the OpenDNS configurations to set it up. It was up and running fine until I did the updating of files then I lost complete internet access. I rebooted and made the changes to (/etc/dhcp3/dhclient.conf) and opened network-admin and made the changes there but the changes didn't stay permanent, I either missed a step or failed to save properly, and it all defaulted back to the default setting for Belkin DNS. That said here is the info...

search Belkin
nameserver 192.168.2.1
nameserver 12.213.224.61

---

### Post by bapoumba on 2007-01-19
@ ovat, are you using some kind of proxy ? Anon proxy ? (i do not know much about these, but they can give trouble).
I also see that you use eth0 to connect to internet. What is eth1 for (and there is no auto eth1) ? You can just comment out the lines in /etc/network/interface (put a # in front of the line) if not using it.

@ dsimpson : you may want to do a search on the forum (links up to the thread) with your exact router type. They are amny threads for belkin, not sure which one to look at. Is this wireless ?
[http://madwifi.org/wiki/Compatibility#Belkin]("http://madwifi.org/wiki/Compatibility#Belkin")

---

### Post by dsimpson on 2007-01-19
Hi, my router is a Belkin F5D7230-4, ver.6002. This is a wireless router connected to my computer and a wired ethernet connection to my wife's computer, connected to a satellite modem by ethernet. Even if I do get the dns setting to opendns it doesn't stay and will go to the default router dns. Then I am back to square one with the slower internet speed, etc. ):P  Wow! new smilies, just had to pass one on, ha! ha!

---

### Post by bapoumba on 2007-01-19
[http://www.ubuntuforums.org/showthread.php?t=315221]("http://www.ubuntuforums.org/showthread.php?t=315221")
[http://www.google.fr/search?hl=en&q=Belkin+F5D7230+site%3Aubuntuforums.org&btnG=Search]("http://www.google.fr/search?hl=en&q=Belkin+F5D7230+site%3Aubuntuforums.org&btnG=Search")

What is the output to **/etc/nework/interfaces** and **ifconfig** ?

---

### Post by dsimpson on 2007-01-19
here's the output form etc/network/interfaces and ifconfig..Thanks for the links, will check out some of the posts on the 2nd link you sent and see if there is  a related problem with solution. 

iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp



iface eth0 inet dhcp



iface ath0 inet static
wireless-essid belkin54g
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1

auto ath0





ath0      Link encap:Ethernet  HWaddr 00:11:50:D5:8D:2D
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82899 errors:3096 dropped:0 overruns:0 frame:3096
          TX packets:54393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:57575538 (54.9 MiB)  TX bytes:4696465 (4.4 MiB)
          Interrupt:12 Memory:e8980000-e8990000

eth0      Link encap:Ethernet  HWaddr 00:A0:CC:39:90:61
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xbc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8120 (7.9 KiB)  TX bytes:8120 (7.9 KiB)

---

### Post by bapoumba on 2007-01-20
I guess ath0 is your wireless card.
Looks okay to me. Check for disabling IPV6 (many threads on the forum), that might be the problem with your router (another guess ;))

---

### Post by dsimpson on 2007-01-21
Hi again, just thinking over your last post, I did disable ipv6, but it ran well and didn't seem to be the cause of my problems but it may have had a delayed effect, who knows. I now have a new problem which I posted under Installations and Networks and it is one that I believe will cause me to do a complete reinstall of Ubuntu, so here I go again. I will just know more this time and will document all changes and save all config files that are default before making my changes, at least I have learned something the first time around. Thank you for your help and patience, I will still be working on my system and won't give into the reinstall until I have exhausted all other options.:-\"

---

