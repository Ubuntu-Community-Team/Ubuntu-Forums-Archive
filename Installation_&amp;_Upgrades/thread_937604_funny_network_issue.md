---
title: "funny network issue"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Edifier1007 on 2008-10-04
Hi 

I had to reinstall ubuntu 7.x since my harddisk was faulty.

Post reinstallation I have following issues. One of which I had faced earlier as well.

1. I can not update or install any packages from archive.ubuntu.com or security.ubuntu.com unless I first ping these addresses. So, I dont use the package manager but always have to open two terminal windows and first start a ping in one of the terminals to one of these addresses (depending on where the package is getting installed from). 

If I choose multiple packages and they are alternatively fetched from archive or security - I need to start the ping at appropriate time :(

2. After the reinstallation, firefox refuses to let me browse the net !!  When I enter address, the status changes to 'connecting to...' and then after a while 'time out' error is given.

I can reinstall the OS but I dont want to since I have run upgrade for quite a few packages. 

My machine is AMD Sampron based and now has a 40GB drive for ubuntu. The net connectivity is thru eth0. From other posts I have checked resolv.conf and network interfaces and dont see anything wrong with it.

Any help will  be appreciated.

Thanks.

---

### Post by Partyboi2 on 2008-10-04
Try turning off IPv6 in firefox. Open up firefox and type in the address bar
```
about:config
``` then on the filter line type in
```
IPv6
``` then change the value to true by double clicking on it if it is not already.

---

### Post by Edifier1007 on 2008-10-04
Thanks Partyboi2!!

That did the trick. 

Any pointers on the first issue :)

---

### Post by Partyboi2 on 2008-10-04
No I am not sure why you have to ping before you can install or update packages.
Are you using a proxy? When you sudo apt-get update from the terminal what is it saying about archive.ubuntu.com and security.ubuntu.com?

---

### Post by Edifier1007 on 2008-10-05
I have no idea why I have to ping first :)

No, I dont go thru a proxy. Its direct connection to the net.

Here is what happens when I try to say update .

"trivedis@trivedis-desktop:~$ sudo apt-get update
[sudo] password for trivedis:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
42% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com
"

Note the connecting message - usually it should start the download but does not.

What I have to do is to open another terminal window - ping security.ubuntu.com and after the pinging starts - run the update command. It works like a charm after that !!

In the following transcript if you notice, after pinging it started the download from security.ubuntu.com

"trivedis@trivedis-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=1 ttl=49 time=246 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=2 ttl=49 time=246 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=3 ttl=49 time=246 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=4 ttl=49 time=244 ms

--- security.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 244.263/245.866/246.838/0.964 ms
trivedis@trivedis-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [111kB]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5280B]                                                                 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [82.8kB]                                                                  
99% [Connecting to archive.ubuntu.com (1.0.0.0)]                            
"

but stopped for archive :( Now what I have to do is to ping archive ... and

"trivedis@trivedis-desktop:~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=1 ttl=49 time=246 ms
64 bytes from archive.ubuntu.com (91.189.88.31): icmp_seq=2 ttl=49 time=241 ms

--- archive.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 241.976/244.432/246.888/2.456 ms
trivedis@trivedis-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN                                    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Fetched 192B in 1s (117B/s)
Reading package lists... Done
"

Bingo - all is well. Beats me as to why this is happening :)

---

### Post by Partyboi2 on 2008-10-05
Try changing your download server to main under Software Sources (System>Admin>Software Sources>First tab) and see what happens.

---

