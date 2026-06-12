---
title: "can't &quot;make&quot; with wireless drivers"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-09
launchpad has asked me to compile/install the latest wireless from wireless.kernel.org.

I can't get past the "make" in kernel 31-2 or 31-1 but it works fine with kernel 30-10.  But my wifi works fine with 30-10 too and don't need it on that kernel.

I have ensured several times that i have headers installed, they are currently installed for each of the kernels I currently have installed.  I have ensured also that build-essential is installed.

When I load the 31-1 or 31-2 kernel and try to run make I get the following error.
> buzzmandt@buzzmandt-laptop:~/Desktop/compat-wireless-2009-07-09$ make
make -C /lib/modules/2.6.31-1-generic/build M=/home/buzzmandt/Desktop/compat-wireless-2009-07-09 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-1-generic'
make[3]: *** No rule to make target `/home/buzzmandt/Desktop/compat-wireless-2009-07-09/drivers/misc/eeprom/max6875.c', needed by `/home/buzzmandt/Desktop/compat-wireless-2009-07-09/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/buzzmandt/Desktop/compat-wireless-2009-07-09/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/buzzmandt/Desktop/compat-wireless-2009-07-09] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-1-generic'
make: *** [modules] Error 2

can't quite figure why it would with one kernel but not the other.
anyone help?

---

### Post by MacUntu on 2009-07-11
Just tried to compile compat-wireless-2009-07-11 - same problem. Also tried to make the stable compat-wireless-2.6.31-rc1 without any luck.

---

### Post by buzzmandt on 2009-07-11
glad I'm not the only one, surprised no one can offer a suggestion here.  Thanks for trying it out and making me feel a little less inadequate lol

---

### Post by budluva04 on 2009-07-11
straight from wireless.kernel.org
> 
You need two things:

    *

      A Kernel >= 2.6.27
    * Your kernel headers installed 

Please be very sure you have your kernel headers installed before reporting any sort of build issues with this package. This usually will mean having this symlink point to a valid directory with kernel headers in it:

/lib/modules/`uname -r`/build

but im sure you guys did this already?

---

### Post by buzzmandt on 2009-07-11
headers and build-essential are installed, I've verified that several times, and yeppers on the /lib/modules/`uname -r`/build as far as I know> /lib/modules/2.6.31-2-generic/build
taken straight from the file browser address

---

### Post by wayne_cat on 2009-07-11
> **budluva04 said:**
> straight from wireless.kernel.org


but im sure you guys did this already?

it also fails on my system ... kernel headers are available:

```
root@macbook:~# ls -la /usr/src/
total 40
drwxrwsr-x 10 root src  4096 Jul 12 03:27 .
drwxr-xr-x 11 root root 4096 Jun 30 20:19 ..
drwxr-xr-x  3 root root 4096 May 29 16:56 kqemu-1.4.0~pre1
drwxr-xr-x 22 root root 4096 Jun 24 02:59 linux-headers-2.6.30-10
drwxr-xr-x 22 root root 4096 Jun 13 22:43 linux-headers-2.6.30-9
drwxr-xr-x  7 root root 4096 Jun 13 22:43 linux-headers-2.6.30-9-generic
drwxr-xr-x 23 root root 4096 Jul  2 23:28 linux-headers-2.6.31-1
drwxr-xr-x 23 root root 4096 Jul 11 16:34 linux-headers-2.6.31-2
drwxr-xr-x  7 root root 4096 Jul 11 16:34 linux-headers-2.6.31-2-generic
drwxr-sr-x 16 root src  4096 Jun 22 18:02 oss-devel



```

---

### Post by buzzmandt on 2009-07-11
> buzzmandt@buzzmandt-laptop:~$ ls -la /usr/src/
total 40
drwxrwsr-x 10 root src  4096 2009-07-08 15:11 .
drwxr-xr-x 10 root root 4096 2009-06-30 16:19 ..
drwxr-xr-x 22 root root 4096 2009-06-30 16:27 linux-headers-2.6.30-10
drwxr-xr-x  7 root root 4096 2009-06-30 16:27 linux-headers-2.6.30-10-generic
drwxr-xr-x 22 root root 4096 2009-06-10 14:58 linux-headers-2.6.30-8
drwxr-xr-x  7 root root 4096 2009-06-10 14:58 linux-headers-2.6.30-8-generic
drwxr-xr-x 23 root root 4096 2009-07-04 11:34 linux-headers-2.6.31-1
drwxr-xr-x  7 root root 4096 2009-07-04 11:34 linux-headers-2.6.31-1-generic
drwxr-xr-x 23 root root 4096 2009-07-10 23:23 linux-headers-2.6.31-2
drwxr-xr-x  7 root root 4096 2009-07-10 23:23 linux-headers-2.6.31-2-generic

Ha, guess I could do that too, thanks for that command wayne_cat

---

### Post by wayne_cat on 2009-07-11
> **buzzmandt said:**
> Ha, guess I could do that too, thanks for that command wayne_cat


```
/lib/modules/2.6.31-2-generic/build 
```is just a link.

```
root@macbook:~# ls -la /lib/modules/2.6.31-2-generic/build
lrwxrwxrwx 1 root root 39 2009-07-06 18:25 /lib/modules/2.6.31-2-generic/build -> /usr/src/linux-headers-2.6.31-2-generic
root@macbook:~# 
```I'm on the Linux-Wireless IRC channel at the moment ... but no response to my question ... I think they all sleep. ;)

---

### Post by wayne_cat on 2009-07-12
buzzmandt,

good news ... I was able to talk to Hauke from the linux-wireless IRC channel. He made a "fixed" version for us ... could you please try to compile it?

[http://www.hauke-m.de/fileadmin/openwrt/compat-wireless-2009-07-12.tar.bz2](http://www.hauke-m.de/fileadmin/openwrt/compat-wireless-2009-07-12.tar.bz2)

Please post your result here? 

More background information in the attached IRC log file .. the file is a little bit hard to read ... and there are some german words in it ... forgot so "export LANG=C" before starting xchat.

---

### Post by buzzmandt on 2009-07-12
Thank you sooooo much wayne_cat

Partial success anyway, 
was able to make, make install, make unistall, make undo, etc......  then rebooted

Still no internet :( .  I went to the help with debug at the end of your chat log and installed iw, but it's way over my head.  I have no clue how to use it.  

After reboot and there was no internet I tried the modprobe -r -f ath5k then modprobe ath5k several times (sudo of course) but still didn't work.  Network manager just says wireless disabled.  This is so depressing.  I'm still using .30-10 for everything.

Lets see if we can get something from launchpad now that I can tell them that it didn't work.  I'll be in irc linux-wireless... I'll leave it connected, might be inside getting a bite to eat but will be back shortly.

again, thank you for all the help.  I really like the progress of karmic so far and hope we can get this ironed out.

---

### Post by wayne_cat on 2009-07-12
what do you get from iwconfig .. nothing?

```
root@macbook:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr1    no wireless extensions.

ppp0      no wireless extensions.

```

---

### Post by buzzmandt on 2009-07-12
Ok, did it twice.  The first one is in the working .30-10 kernel while connected to days inn
```
buzzmandt@buzzmandt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Days Inn"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:12:17:E2:37:A9   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/70  Signal level=-91 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

buzzmandt@buzzmandt-laptop:~$ 
```


and this second one is with the not working .31-2 kernel.  Didn't move, days inn connection should still be accessible.
```
buzzmandt@buzzmandt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

buzzmandt@buzzmandt-laptop:~$ 

```

---

### Post by wayne_cat on 2009-07-12
Can you "see" the access point when you use the 2.6.31 kernel:

```
root@macbook:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:32:96:4B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Core"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005ce6fbfd
                    Extra: Last beacon: 6304ms ago
                    IE: Unknown: 0004436F7265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:18:4D:46:69:90
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Scheffer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000068817b6981
                    Extra: Last beacon: 5748ms ago
                    IE: Unknown: 00085363686566666572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010024FF7F

root@macbook:~# 
```

---

### Post by buzzmandt on 2009-07-12
> buzzmandt@buzzmandt-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

that doesn't look good

---

### Post by MacUntu on 2009-07-15
Just for the record: compat-wireless-2009-07-16 builds fine again.

---

### Post by buzzmandt on 2009-07-15
sorry, guess I could have noted that the problem with atheros has been solved and a temp work around noted.  A fix should be coming down the pipe in the future.

---

### Post by wayne_cat on 2009-07-15
maybe useful to understand the background:

[https://bugs.launchpad.net/ubuntu/+bug/395565](https://bugs.launchpad.net/ubuntu/+bug/395565)

---

### Post by buzzmandt on 2009-07-15
yeah, thought about putting that in but the link is also under the first post. 

thanks again wayne_cat

---

