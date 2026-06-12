---
title: "E: Method http has died unexpectedly!"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by neilp on 2008-07-21
I've just run into a problem that has me stumped.

I just returned from 10 days worth of holidays. I logged onto my machine (which I'm pretty sure was running the whole time.)  and saw in the update manager that the update information is outdated.  So, I tell it to check for updates.  I get a dialog back that it could not download all repository indexes, with details of "Method http has died unexpectedly!"

I tried running both sudo aptitude update and sudo apt-get update, and for both I get:
E: Method http has died unexpectedly!
E: Method http has died unexpectedly!
E: Method http has died unexpectedly!

I searched the forums, and the only other relevant post said that the problem was due to a bad gateway...my network is set up exactly the same as when I left, so I don't think that's applicable to my problem.

I couldn't find any sort of logs or verbosity switches in the command-line commands that point to what the problem is (the last entries in my apt logs was when I ran update manager and installed some updates on July 11th)

Any ideas where else I could look for the source of this problem?  Has anyone else come across it, and resolved it in ways other than reinstalling their system (which was the cure in a couple of other cases I could find.)

Thanks!
Neil

---

### Post by tamoneya on 2008-07-21
try changing the mirror you use by looking in system-> administration -> software sources.

Also can you post the output of ```
ifconfig
```

---

### Post by neilp on 2008-07-21
> **tamoneya said:**
> try changing the mirror you use by looking in system-> administration -> software sources.

Also can you post the output of ```
ifconfig
```

The mirror I had set up before I started having problems was the main US mirror.  I tried changing it to the Canadian mirror before I posted, and I got the same error.  I've even gone through the list of mirrors to find a FTP mirror to see if if produced the same problem, and it did.

Here's my output of ifconfig
```

neilp@spike:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:6c:eb:ee  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29777580 (28.3 MB)  TX bytes:8914541 (8.5 MB)
          Interrupt:17 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48087359 (45.8 MB)  TX bytes:48087359 (45.8 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.183.1  Bcast:192.168.183.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.250.1  Bcast:192.168.250.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```
(I have VMWare server installed on this box, thus the vmnet interfaces.  But VMWare was installed before I started having problems, and I even tried updating with all the virtual interfaces down as well, and it was the same thing.)

---

### Post by upchucky on 2008-07-21
one time i did an upgrade and to get it to complete i had to switch sources to us server, update then try again on main server

never mind

---

### Post by upchucky on 2008-07-21
can u get wireshark or something like it to run? i think your isp is havin trouble

---

### Post by neilp on 2008-07-21
I'm pretty sure it doesn't have anything to do with my ISP.  One of the virtual machines I'm running on this box is running Dapper, and it has no issues running sudo aptitude update.  (btw:  the one having issues is running Hardy).  So if it was ISP issues, one would assume it would be affecting both instances similarly, but it isn't.

Plus, I did try running wireshark...I didn't see any network activity when I ran sudo aptitude update (and received the error), so this leads me to believe that the problem lies within the box itself, rather than having anything to do with the network.

---

### Post by tamoneya on 2008-07-21
if you arent running any VMs at the moment try to shut off the vmnet interfaces like this.```
sudo ifconfig vmnet1 down
sudo ifconfig vmnet8 down
```

Afterwards you can always turn them on like this:```
sudo ifconfig vmnet1 up
sudo ifconfig vmnet8 up
```

---

### Post by upchucky on 2008-07-22
since you got wireshark running, ping someone and see the log, if you still have all errors in packets receive and transmit then the net card needs some love.

---

### Post by neilp on 2008-07-22
> **tamoneya said:**
> if you arent running any VMs at the moment try to shut off the vmnet interfaces like this.```
sudo ifconfig vmnet1 down
sudo ifconfig vmnet8 down
```

Afterwards you can always turn them on like this:```
sudo ifconfig vmnet1 up
sudo ifconfig vmnet8 up
```


It's the same result if the vmnet interfaces are up or down.

---

### Post by neilp on 2008-07-22
> **upchucky said:**
> since you got wireshark running, ping someone and see the log, if you still have all errors in packets receive and transmit then the net card needs some love.

I guess I wasn't more clear about the problem:  my network is working fine.  I can use a browser and hit any of the mirrors with no problems whatsoever, and have had no issues doing anything other than running an aptitude update.

---

### Post by redaben on 2009-01-03
Hi 
Have you solved your issue ? i am having the same problem...the network is ok but i apt-get return that same error E: Method http has died unexpectedly!

---

### Post by neilp on 2009-01-04
I think something got messed up with an upgrade of the apt libraries.  I reinstalled apt from the installation CD, and things worked fine after that (including upgrading apt itself.)

---

### Post by redaben on 2009-01-10
Glad to know you found a solution.
For me, it seems to work now, after i have enabled intel virtualisation on the BIOS of my server (default was disabled, which caused kvm_intel module not to load, though kvm was working !?) 
I'm really a newbie to virtualisation. I don't know if the two issues (virtualisation and apt problem) have something to do with each other, but now it apt-get seems to work.
Any Guru to teach us something ?

---

### Post by doru001 on 2010-10-04
Same problem here, during a GUI "Distribution Upgrade" from Hardy (8.04 LTS) to Lucid (10.04 LTS), no virtual NIC's. I just restarted it 10 times and it finally downloaded all packages. I am not sure how did you reinstall apt from the installation disc, did you use dpkg, which is not in apt, and you did not have any problems with already updated libraries?

---

