---
title: "Can u help me to convert kernel 2.4 driver to kernel 2.6 ?"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by ajinkyakulkarni87 on 2007-11-23
I have UT-300R2U ADSL Modem. I am connecting it via USB port. The driver came with cd requires linux kernel 2.4 for working. Can you help me to analyze  this driver and help to convert it for kernel 2.6. Can you just look at it at least once?

[B]
I have attached it into zip file.[/B]

Thank you:KS

---

### Post by Whiffle on 2007-11-23
It should work without doing any work...

[http://ubuntuforums.org/archive/index.php/t-159039.html](http://ubuntuforums.org/archive/index.php/t-159039.html)

---

### Post by ajinkyakulkarni87 on 2007-11-24
Thanks for reply.

I have seen that post before. But infact USB port  doesnt work in linux as mentioned in that post. I dont know why!! :confused:

This router has 1 ethernet port + 1 usb port.  The ethernet port just works fine with Ubuntu  on my Laptop. But on my desktop I have to connect using usb only.

It would be great if I can compile that driver for new kernel!

**The readme file came with driver is as follow**
[INDENT][INDENT][I][COLOR="Sienna"]USB  Driver  for  Linux  Install
Date: 2006/6/8

[COLOR="Blue"]1. Install RedHat 9.0 (RedHat 8.0)[/COLOR]

[COLOR="Blue"]2. Login as root[/COLOR]

[COLOR="Blue"]3. Check out Linux version (RedHat 8.0 -> linux-2.4.18-14, RedHat 9.0 -> linux-2.4.20-8)[/COLOR]
[root@CNXT root]**# cd /usr/src**
[root@CNXT src]**# pwd**
/usr/src
[root@CNXT src]**# ls -l**
total 12
drwxr-xr-x    2 root     root         4096 Jan 25  2003 debug
lrwxrwxrwx    1 root     root           14 Jun 17  2005 linux-2.4 -> linux-2.4.2
0-8
drwxr-xr-x   16 root     root         4096 Jun 17  2005 linux-2.4.20-8
drwxr-xr-x    7 root     root         4096 Jun 17  2005 redhat

[COLOR="Blue"]4. RedHat 9.0 for example[/COLOR]
   **#ln -s linux-2.4.20-8 linux**
[root@CNXT src]**# ln -s linux-2.4.20-8 linux**
[root@CNXT src]**# ls -l**
total 12
drwxr-xr-x    2 root     root         4096 Jan 25  2003 debug
lrwxrwxrwx    1 root     root           14 Jun  8 12:19 linux -> linux-2.4.20-8
lrwxrwxrwx    1 root     root           14 Jun 17  2005 linux-2.4 -> linux-2.4.2
0-8
drwxr-xr-x   16 root     root         4096 Jun 17  2005 linux-2.4.20-8
drwxr-xr-x    7 root     root         4096 Jun 17  2005 redhat

[COLOR="Blue"]5. Copy folder ASL-25020 to /root [/COLOR]

[COLOR="Blue"]6.[B] #cd /root/ASL-25020[/COLOR]
   #make clean
   #make all[/B]
[root@CNXT ASL-25020]**# pwd**
/root/ASL-25020
[root@CNXT ASL-25020]**# make clean**
rm -f ./src/CDCEther.o  ./src/CDCEther.o *.o .depend ./VKGEther
[root@CNXT ASL-25020]**# make all**
gcc -c -O2  -Wall -Wno-missing-braces -Wstrict-prototypes -fomit-frame-pointer -
fno-strict-aliasing -pipe -fno-strength-reduce -mcpu=i486 -falign-loops=2 -falig
n-jumps=2 -falign-functions=2 -I/usr/src/linux/include -I./inc  -D__KERNEL__ -DM
ODULE  -Dlinux -DDBG=0 -o src/CDCEther.o src/CDCEther.c
ld -r -o ./VKGEther ./src/CDCEther.o
[COLOR="Blue"]
7. Add "alias eth1 VKGEther" in file /etc/modules.conf[/COLOR]
   #**vi  /etc/modules.conf**
alias eth0 pcnet32
alias scsi_hostadapter BusLogic
alias sound es1371
post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1
|| :
pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 |
| :
alias usb-controller usb-uhci
alias eth1 VKGEther  
[COLOR="Blue"]
8. Edit file "ifcfg-eth1"[/COLOR]
   #**vi /etc/sysconfig/network-scripts/ifcfg-eth1**
DEVICE=eth1
BOOTPROTO=static
BROADCAST=192.168.1.255
IPADDR=192.168.1.3
NETMASK=255.255.255.0
NETWORK=192.168.1.0
ONBOOT=yes
[COLOR="Blue"]
9. Add "insmod /root/ASL-25020/VKGEther" to file rc.local[/COLOR]
   #vi /etc/rc.d/rc.local
   insmod /root/ASL-25020/VKGEther

[COLOR="Blue"]10. Connect USB to device and reboot[/COLOR]
 
[COLOR="Blue"]11. Test[/COLOR]
    #ifconfig eth0 down
    #ping 192.168.1.2
[root@CNXT ASL-25020]# ifconfig eth0 down
[root@CNXT ASL-25020]# ping 192.168.1.2 -c 3
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=2.03 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=3.06 ms

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2021ms
rrt min/avg/max/mdev = 2.038/2.549/3.061/0.513 ms

[root@CNXT ASL-25020]# **ifconfig eth1**
eth1	Link encap:Ethernet HWaddr 00:05:5D:00:00:04
	inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:34 errors:0 dropped:0 overruns:0 frame:0
	TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:100
	RX bytes:3200 (3.1 Kb) TX bytes:3396 (3.3 Kb)

[/COLOR][/I][/INDENT][/INDENT]

---

### Post by ajinkyakulkarni87 on 2007-11-24
When Driver is compiled using above steps, it gives lot of errors during compilation itself

---

