---
title: "Update manager ans Synaptic will not connect to the internet..."
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by danyro on 2007-01-10
Hey all!

I am very much new at this and so far so good until today.I tried the newbie forum and no luck so far so I am posting here to see we can find a solution.

In a nutshel...Update manager ans Synaptic will not connect to the internet... 

I tried several different software packages and got the same result.

Also I have the exact same problem with update manager and I think that the two issues are related.

FYI... I can browse the internet just fine with Firefox.

I will greatly appreciate any help I can get.


](*,) 


below is a few files that may be relevant.



/etc/apt/apt.config
looks like this...


Acquire::http::Proxy "false";





Now here's source.list
_________
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
______


and the error messages that i get once I cancel the update. 

____

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/...tu1.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...061004_all.deb](http://us.archive.ubuntu.com/ubuntu/...061004_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...060927_all.deb](http://us.archive.ubuntu.com/ubuntu/...060927_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/...tu0.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tu18.2_all.deb](http://us.archive.ubuntu.com/ubuntu/...tu18.2_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/...u18.2_i386.deb)

---

### Post by K.Mandla on 2007-01-10
It's probably worth trying from the command line. It might give you a clue as to what's wrong with Synaptic.

Open a  terminal and ...

```
sudo aptitude update
```
If that works, you should be able to go back into Synaptic and start installing like you wanted to. If you're still not getting a reply, try ...

```
ping www.google.com
```
If *that's* not working, you might try ...

```
sudo /etc/init.d/networking restart
```
And then try those first two steps again. That's about all I can think of for now. :-k

---

### Post by danyro on 2007-01-12
I should note that I can access the internet just fine so pinging an domain names works. 
I also tried to restart the networking and the problem stil persist.

I tried sudo aptitude update and the progress stops at 57% "waiting for header" and have to cancel everything by hitting ctl-c.

](*,) ](*,) ](*,)

---

### Post by NeoLithium on 2007-01-12
Comment out the CDROM line as well; so it doesn't look to try to pull packages from the Ubuntu disk.

---

### Post by danyro on 2007-01-12
commented out the cd rom section.

Same result. Still does not work.

---

### Post by kbarrett on 2007-01-13
I'm seeing similar behaviour today from the repositories.

And yes, I have full IP access.


Either something is broken, or they are really getting hammered by folks doing distribution upgrades today ...

---

### Post by danyro on 2007-01-13
I have not been able to either update or get any new sofware package for well over a week now..

---

### Post by Philmc on 2007-01-21
Is this an ongoing problem as I seem to have the same symptoms, and none of the above solutions resolved it.

Phil

---

### Post by Philmc on 2007-01-22
[/QUOTE]```
sudo aptitude update
```[/QUOTE]

This results in:

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                               
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                                
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out

[/QUOTE]```
ping www.google.com
```[/QUOTE]

This works fine

[/QUOTE]```
sudo /etc/init.d/networking restart
```
[/QUOTE]

The result of this is: 

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3992
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:72:c4:62:e2
Sending on   LPF/eth0/00:13:72:c4:62:e2
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:72:c4:62:e2
Sending on   LPF/eth0/00:13:72:c4:62:e2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 1744 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by marmaladejackson on 2007-12-17
I'm having the same problems.  Can browse the internet fine, but synaptic, pacakge manager, and update manager can't connect.  Has anybody solved this yet?  Update manager worked fine to update everything after initial install.  The notebook has been sitting on the shelf for a while and I decided to play with it tonight and the above doesn't work anymore.

Thanks
-B

---

### Post by NeverM$4Me on 2007-12-26
Please try the following:

```
more /etc/apt/apt.conf |grep Proxy
```

If there's anything showed up like this:

```
Acquire::http::Proxy "http://127.0.0.1:8080";
```

Please rename that file to something else like "apt.conf.backup.

Then try:

```
sudo apt-get update
```

to see if it works now.

---

