---
title: "Ubuntu Server install does not detect onboard Ethernet"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by albertc on 2006-12-22
Hi

I'm trying to install Ubuntu Server on a new Dell PowerEdge SC440 server. Given that the enclosed Dell's Server Installation CD supports only Windows, RedHat and SUSE Linux, I went ahead with the Ubuntu standalone install. 

However, the Ubuntu install does not detect any Ethernet adapter, even though the server has one onboard. Is this a bug or am I missing something here?

Can anybody help? Please note that I've installed Ubuntu Desktop on a couple of Dells before, and the process ran well.

Thanks in advance for any assistance.
--
Albert

---

### Post by CIDM on 2007-03-11
Hi Albert, 

Here is the way to solve this issue (Broadcom Gigabit Ethernet on Dell PowerEdge SC440).
(there might be other ways, but this one worked for me)

Using Ubuntu 6.06.1 LTS CD...

1. Install as usual, at the network not found, just continue...
2. you will need another computer connected to the net, and some way to bring a file to the Ubuntu Server. Download the linux driver to you working computer at this address :
[http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php]("http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php")
3. From the zip, just get the tg3xxxxx.tar.gz, not the rpms or xxxxsup.tar.gz...
4. With an usb key, copy it to your ethernet-less Dell SC440 Ubuntu Server and do the following :
```
touch /etc/resolv.conf
vim /etc/network/interfaces
```
Add those lines :
```
auto eth0
iface eth0 inet dhcp
```
5. Be sure to unload current tg3, if enabled...
```
modprobe -r tg3 
```
6. Make sure you have everything needed for driver compilation (it's on the CD, you'll need it)
```
apt-get install build-essential linux-headers-$(uname -r)
```
7. Untar your driver and CD in it.
```
tar zxvf tg3-xxxxx.tar.gz
cd  tg3-xxxxx
```
8. Do this :
```
make
insmod tg3.ko
vim /etc/modprobe.d/aliases 
```
    Add a line : alias eth0 tg3 
9. Your first try :
```
/etc/init.d/networking restart
ifconfig
``` should show something good...

10. Driver installation 
```

modprobe -r tg3
make install
```
11. reboot ! Voilà !


Hope this will help you as well as others in this situation...

Francis

---

### Post by GoJimbo on 2007-03-21
Hi,

I just posted in Networking and Wireless about a problem I'm having
[http://ubuntuforums.org/showthread.php?t=390287]("http://ubuntuforums.org/showthread.php?t=390287")

I installed 6.06 and as you mention it does not detect the onboard Ethernet.  Post install I just manually added added loopback and eth1 (static ip) in /etc/network/interfaces and restarted networking.  Thought everything was ok because I could run apt-get update and browse to the machine from on campus and off-campus.

Shortly after I found I was unable to browse to the machine from off-campus and complained to the campus IT and got the response in my other post that there may be an internal server error because it responds to ping but not http or ftp.

Could this result from my not installing the driver per the instructions you provide above?

Don't mean to double post or hijack the thread but I'm getting pretty desperate.

Thanks in advance for any advice.

---

### Post by ddose on 2007-04-19
I followed the up to the tar command and then get an error on the make command in 6.06 LTS:


make
make -C SUBDIRS=/home/ddose/temp/tg3-3.71b modules
make: *** SUBDIRS=/home/ddose/temp//tg3.3.71b: No such file or directory. Stop.
make: *** [default] Error 2


Any ideas?

Thanks

---

### Post by ddose on 2007-04-19
Never mind previous, must have had a typo in step 6...

---

### Post by CIDM on 2007-04-19
You had missed this step :

apt-get install build-essential linux-headers-$(uname -r)

:) 

Best of luck !

---

### Post by 98xj on 2007-04-19
I had the same issue , but my broadcom used the bnx2 module
complete the install with out networking, 
after booting to the installed o/s modprobe bnx2 then dhclient eth0 , then add the lines to interfaces file that CDIM suggested, reboot and it should work (I though it was tg3 as well)

---

### Post by ntnwwnet on 2007-06-24
I want to thank you VERY much for this help. Without it, I was about to call and complain to Dell.

Thank you for saving me a LOT of trouble!

---

### Post by bensode on 2007-07-23
When I skip and continue on with the install without the NIC, I get a blank blue screen when it should be starting the partitioning.  If I press ctrl-c, I get a blink, then starting up partitioner, then I get stuck in a loop no matter what option I pick on the partitioner it just blanks the screen and hangs.

---

### Post by thrcomputer on 2007-08-23
Kudos for posting this.  Installing Ubuntu for the first time and came across the network card issue on the poweredge sc440 server.  Your instructions worked for me!


> **CIDM said:**
> Hi Albert, 

Here is the way to solve this issue (Broadcom Gigabit Ethernet on Dell PowerEdge SC440).
(there might be other ways, but this one worked for me)

Using Ubuntu 6.06.1 LTS CD...

1. Install as usual, at the network not found, just continue...
2. you will need another computer connected to the net, and some way to bring a file to the Ubuntu Server. Download the linux driver to you working computer at this address :
[http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php]("http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php")
3. From the zip, just get the tg3xxxxx.tar.gz, not the rpms or xxxxsup.tar.gz...
4. With an usb key, copy it to your ethernet-less Dell SC440 Ubuntu Server and do the following :
```
touch /etc/resolv.conf
vim /etc/network/interfaces
```
Add those lines :
```
auto eth0
iface eth0 inet dhcp
```
5. Be sure to unload current tg3, if enabled...
```
modprobe -r tg3 
```
6. Make sure you have everything needed for driver compilation (it's on the CD, you'll need it)
```
apt-get install build-essential linux-headers-$(uname -r)
```
7. Untar your driver and CD in it.
```
tar zxvf tg3-xxxxx.tar.gz
cd  tg3-xxxxx
```
8. Do this :
```
make
insmod tg3.ko
vim /etc/modprobe.d/aliases 
```
    Add a line : alias eth0 tg3 
9. Your first try :
```
/etc/init.d/networking restart
ifconfig
``` should show something good...

10. Driver installation 
```

modprobe -r tg3
make install
```
11. reboot ! Voilà !


Hope this will help you as well as others in this situation...

Francis

---

### Post by peterLinux on 2007-11-13
This worked for me (less elaborated as suggested solution)

vim /etc/network/interfaces

You only see the loopback lines in there...
so add on the bottom

auto eth0
iface eth0 inet static
address 192.168.10.2
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
gateway 192.168.10.1

Save the file quit vim (:wq)

sudo /etc/init.d/networking restart

It will automagically 'detect' the bnx2 stuff ... (not sure for tg3)


Good luck

Peter

---

### Post by syahreza.octadian on 2007-12-14
dear all, 

please help 

when i upgrade dapper to edgy, i lost my netword card. when i compile i still get error like this:

make
make -C SUBDIRS=/apps/tg3-3.71b modules
make: *** SUBDIRS=/apps/tg3.3.71b: No such file or directory. Stop.
make: *** [default] Error 2



i have install build-esential and have install linux-header-2.6.17-12-386

what should i do now?????

---

### Post by clod81 on 2008-03-16
> **ddose said:**
> I followed the up to the tar command and then get an error on the make command in 6.06 LTS:


make
make -C SUBDIRS=/home/ddose/temp/tg3-3.71b modules
make: *** SUBDIRS=/home/ddose/temp//tg3.3.71b: No such file or directory. Stop.
make: *** [default] Error 2


Any ideas?

Thanks

I have the same problem
uname -r gives me: 2.6.15_51-386  but the package linux-headers-2.6.15_51-386 doesn't exist
I installed the package from installation CD called linux-headers-2.6.15_51 -> # apt-get install linux-headers-2.6.15_51
but I still have that problem during the tg3 module compilation: 
# make
make -C SUBDIRS=/path/tg3-3.71b modules
make: *** SUBDIRS=/path/tg3.3.71b: No such file or directory. Stop.
make: *** [default] Error 2


of course I also installed build-essential

what can I do?
thanks

---

