---
title: "Bizarre wireless ESSID bug with 2.6.19 kernel"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by moxfyre on 2006-12-04
I wanted to upgrade Edgy to a 2.6.19 kernel to see if the wireless drivers for the RealTek 8225 card is less buggy than with 2.6.17.  So I edited my sources.list, changing "edgy" to "feisty".  Then I installed the 2.6.19 kernel:

```
apt-get update; apt-get install linux-image-2.6.19-7-generic
```

The kernel installation went fine :)!  I rebooted, and everything LOOKED fine.  However, my wireless connection wasn't connected.

I ran iwconfig, and it showed everything correctly, except that the last character of the ESSID had been chopped off :confused:  I looked in /etc/network/interfaces, and the ESSID id was specified **correctly**.

I tried specifying the correct ESSID at the command line:
```

$ sudo iwconfig wlan0 essid **linksys**
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"**linksy**"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

How weird is THAT?  Whatever I specify as the ESSID, the last character gets chopped off.  In order to get the right ESSID, I had to add an extra nonsense character:

```

$ sudo iwconfig wlan0 essid **linksysZ**
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"**linksys**"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Has anyone else encountered this bug???  I couldn't figure out what to file it under at launchpad.net ... any ideas?

---

### Post by rjjb on 2006-12-05
I got it today with the current CLFS x86_64 multilib build (glibc 2.5, binutils 2.17, gcc 4.1.1, linux-2.6.19) using wireless_tools_28.

Looking through iwconfig.c, I found the following on lines 929 and 930:
if(we_kernel_version > 20)
  wrq.u.essid.length--;

That looked kinda suspicious to me and appeared to account for the cropped off essid so I commented it out.  Probably not a good fix, since it'll break on whatever kernels it was intended for, but it worked for me.

So.. if you change those lines to the following and rebuild the package, you'll be all set (or just use the bogus extra character.. heh):
// if(we_kernel_version > 20)
//   wrq.u.essid.length--;

Regards,
Jeremy.

---

### Post by moxfyre on 2006-12-06
Good find, Jeremy!!!  I've submitted this bug to Launchpad: [https://bugs.launchpad.net/distros/ubuntu/+source/wireless-tools/+bug/74672](https://bugs.launchpad.net/distros/ubuntu/+source/wireless-tools/+bug/74672)

---

### Post by nalm on 2007-04-22
> **moxfyre said:**
> I wanted to upgrade Edgy to a 2.6.19 kernel to see if the wireless drivers for the RealTek 8225 card is less buggy than with 2.6.17.  So I edited my sources.list, changing "edgy" to "feisty".  Then I installed the 2.6.19 kernel:

```
apt-get update; apt-get install linux-image-2.6.19-7-generic
```

The kernel installation went fine :)!  I rebooted, and everything LOOKED fine.  However, my wireless connection wasn't connected.

I ran iwconfig, and it showed everything correctly, except that the last character of the ESSID had been chopped off :confused:  I looked in /etc/network/interfaces, and the ESSID id was specified **correctly**.

I tried specifying the correct ESSID at the command line:
```

$ sudo iwconfig wlan0 essid **linksys**
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"**linksy**"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

How weird is THAT?  Whatever I specify as the ESSID, the last character gets chopped off.  In order to get the right ESSID, I had to add an extra nonsense character:

```

$ sudo iwconfig wlan0 essid **linksysZ**
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"**linksys**"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Has anyone else encountered this bug???  I couldn't figure out what to file it under at launchpad.net ... any ideas?

I'l almost 100% sure it's a problem with the r818x module and so far with the 2.6.20 kernel is still not resolved.

---

### Post by Festor on 2007-07-18
In the with 2.6.20-16-generic  dont work r818x module

---

### Post by DoctorMO on 2007-08-09
rjjb can you post a link to rebuild instructions? using the junk char work around is find for an experienced user but I gave a laptop to friend who I have no intention of teaching how to use the command line for this problem.

[EDIT] Found it, and I attach the feisty deb for anyone else who wants to fix this problem, oh and remember it _will_ break other wifi cards so be damn careful.

---

