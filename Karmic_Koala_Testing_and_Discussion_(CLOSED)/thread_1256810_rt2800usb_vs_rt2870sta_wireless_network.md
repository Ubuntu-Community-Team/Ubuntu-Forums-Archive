---
title: "rt2800usb vs rt2870sta wireless network"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nickmcg on 2009-09-03
Has anyone managed to successfully configure an rt2870-based wireless adaptor using rt2800usb?

I have tried, but assume I must be missing something as I have to revert to rt2870sta.

Currently using network-manager to configure the network. I have noticed that if I set my router to g/b only, the network is recognised but I still cannot connect. If my router is set to b/g/n, the network is not seen (ssid is broadcast).

Any ideas?

Cheers

Nick

---

### Post by nickmcg on 2009-09-09
Bump anyone?

---

### Post by Reiger on 2009-09-09
Dunno. I presume one should use the 2870 drivers for 2870 hardware... ? IIRC the drivers from Ralink are simply the ones you should use (unless they recommend otherwise) because the others aren't as mature yet.

---

### Post by nickmcg on 2009-09-09
Yet Karmic supplies *both* drivers, but it seems that you have to blacklist rt2800usb  which appears to be the latest ?stable? version.

dmesg reports rt2870sta as possibly unstable and in the staging area.

I don't understand.

Nick

---

### Post by Reiger on 2009-09-09
Ah. I take it you have the rt2870sta supplied with the kernel, right? That project was only &#8220;recently&#8221; added to the mainline kernel so it isn't considered mature yet. At any rate Ralink supplies their own drivers under the GPL, they used to be quite reliable for me...

I'd need to fiddle a little with my PC that uses a rt2870 based USB adapter; but I have sadly far too little time on my hands to do that right now. :P

---

### Post by nickmcg on 2009-09-10
rt2870sta was included in jaunty, but rt2800usb wasn't.

According to the [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page") site, the version included in the kernel is rt2x00 (including rt2800usb) which was originally based on the ralink code

I can't build the ralink driver under karmic as I get 
```
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1624: error: ‘struct net_device’ has no member named ‘open’
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1625: error: ‘struct net_device’ has no member named ‘stop’
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1626: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1627: error: ‘struct net_device’ has no member named ‘do_ioctl’
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1633: error: ‘struct net_device’ has no member named ‘get_stats’
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1667: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-generic'
make: *** [LINUX] Error 2

```

I'm still puzzled as to why both versions are shipped, so that the rt2870 no longer works 'out of the box' as it did under jaunty

Cheers

Nick

---

### Post by nickolasemp on 2009-09-14
I can report the same issue...
I have an Asus P5e3 which ships with an rt2870...I presume usb. While 2.6.28 kernel works flawlessly(apparently it uses rt2800sta), 2.6.31 just doesn't work. It tries to connect (it sure does find the network) but fails all the time.

I don't know if this is something the Ubuntu team can take care of. I sure hope so. Anyway, shouldn't we file this bug to the kernel guys?

P.S.: Forgot to mention that I tested both kernels in Jaunty, getting the kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and I'm guessing that karmic is using kernel 2.6.31-020631 from that repository
P.S.#2: Needless to say that as nickmcg has pointed out elsewhere sudo gedit /etc/modprobe.d/blacklist.conf and adding blacklist rt2800usb temporarily makes the card work... But that is not a real solution.

---

### Post by joelsolar on 2009-09-17
I tried to install rt2870usb but i could not.
Can someone help me to install my usb device?

Thanks.

Please, step by step, i have no experience in linux.

---

### Post by nickmcg on 2009-09-18
> **joelsolar said:**
> I tried to install rt2870usb but i could not.
Can someone help me to install my usb device?

Thanks.

Please, step by step, i have no experience in linux.

Assuming you are using Karmic:
Open a terminal session (Applications->Accessories->Terminal)
Type ```
sudo gedit /etc/modprobe.d/blacklist.conf
```This will ask for your password, and open a text editor
Add a line ```
blacklist rt2800usb
```Save the file & reboot.

That should work

Nick

---

### Post by joelsolar on 2009-09-22
I was trying to install rt2870 driver for my  buffalo WLI-UC-GN, the Smallest Wifi N USB Dongle on Earth.
When I executed the command MAKE, the issue is:


joel@compaq:~/Documents/2009$ make
make -C tools
make[1]: Entering directory `/home/joel/Documents/2009/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joel/Documents/2009/tools'
/home/joel/Documents/2009/tools/bin2h
cp -f os/linux/Makefile.6 /home/joel/Documents/2009/os/linux/Makefile
make  -C  /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/joel/Documents/2009/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/joel/Documents/2009/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/joel/Documents/2009/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/joel/Documents/2009/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
cp -f /home/joel/Documents/2009/os/linux/rt2870sta.ko /tftpboot
cp: cannot remove `/tftpboot': Permission denied
make: *** [LINUX] Error 1


There is a error,
can someone tell me what's going on?

When I try the command sudo make install:

joel@compaq:~/Documents/2009$ sudo make install
[sudo] password for joel: 
make -C /home/joel/Documents/2009/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/joel/Documents/2009/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/joel/Documents/2009/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-11-generic
make[1]: Leaving directory `/home/joel/Documents/2009/os/linux'

When I try iwconfig:

joel@compaq:~/Documents/2009$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


When I try ifconfig:

joel@compaq:~/Documents/2009$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:94:34:a7  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe94:34a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51708757 (51.7 MB)  TX bytes:1595748 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

How do I configure my adpater?
I tried too ndiswrapper:

[IMG]file:///tmp/moz-screenshot.jpg[/IMG]
[IMG]http://ubuntuforums.org/home/joel/pic.png[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

System can see my adapter
but I could not install it

What kind of configuration tool may I use?

[IMG]http://ubuntuforums.org/home/joel/pic2.png[/IMG]




Please  I need help
I will appreciate it.

Thanks friends.

---

### Post by Reiger on 2009-09-23
It is what it says on the tin: "permission denied". You must run this particular make as root otherwise the process won't complete since it wants to do stuff which requires elevated permissions.

---

### Post by nickmcg on 2009-09-23
```
make
sudo make install
```

---

### Post by Reiger on 2009-09-23
For who is interested, a patch was submitted for the 28x0 driver that should bring parity with the Ralink 2.1.0 driver: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg08861.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg08861.html)

---

### Post by nickmcg on 2009-09-25
> **Reiger said:**
> For who is interested, a patch was submitted for the 28x0 driver that should bring parity with the Ralink 2.1.0 driver: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg08861.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg08861.html)

It looks to me that that patch applies to the rt2870sta module, not the rt2x00 modules.

Any idea how to get & apply the patch?

Nick

---

### Post by ctsdownloads on 2009-10-04
Tried everything here myself, blacklisting both and neither, each, etc - nadda. This is with the beta of 9.10 and all of the available updates installed.

THankfully Puppy Linux supports rt2800usb with full speeds out of the box. It's unfortunate, but at least that distro has usable wireless support for  rt2800usb...sigh. :(

---

