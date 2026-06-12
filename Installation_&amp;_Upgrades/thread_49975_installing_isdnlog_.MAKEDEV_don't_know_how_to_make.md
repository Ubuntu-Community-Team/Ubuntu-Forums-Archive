---
title: "installing isdnlog: ./MAKEDEV: don't know how to make device &quot;isdn&quot;"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by ivomans on 2005-07-18
Today I tried to install an ISDN card on my Ubuntu server installation.
Only purpose of this card will be to monitor incoming, outgoing and missed calls.
Therefore I gave command: sudo apt-get install isdnlog isdnlog-data

Unfortunately the installation ended up with following lines:

 ```
 * Starting ISDN services...
./MAKEDEV: don't know how to make device "isdn"

Setting up isdnlog-data (3.6.2005-01-03-4ubuntu1) ...
Setting up isdnlog (3.6.2005-01-03-4ubuntu1) ...
First time configuration, creating /etc/isdn/isdn.conf .
Creating /etc/isdn/rate.conf .
Creating default /etc/isdn/isdnlog.isdnctrl0 .
 * Starting isdnlog...
./MAKEDEV: don't know how to make device "isdn"
dpkg: error processing isdnlog (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 isdnlog
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

It's an internal Teles 16.3 ISDN card.
Anybody could advise me in which direction I should try to find the solution?

---

### Post by nibbio on 2005-07-18
I think i have the same problem but with another isdn card.
I have a "W6692 based PCI card" and my problem is:
[list]
[*] I can load the kernel module and it seams to work. For now i only added a line "modprobe hisax type=36 protocol=2" in the "/etc/init.d/modules-init-tools" script. When I find the right way to load the module, i do this thing better.
[*] I installed the isdn-utils from synaptic, configured the isp number, user, pass etc but an error stopped the installation. I tryed to connect to internet with "isdnctrl dial ippp0" and it worked.
[*] But at next reboot i had this error:
```
 * Starting ISDN services...
./MAKEDEV: don't know how to make device "isdn"
``` 
But the strange thing it that if i run
```
dpkg-reconfigure ipppd
``` 
it tells me that i must delete config files before reconfiguring ipppd, i quit and at the console appears
```
Note: running MAKEDEV to create ISDN devices in /dev...
 * Restarting ipppd...                                                   [ ok ]
``` 
If now i try to restart isdnutils with
```
/etc/init.d/isdnutils restart
``` 
it works and i can connect to internet, but the next time i reboot the problem is the same
[/list] 
I tried to reinstall isdn-utils, reconfigure ipppd, reinstall ubuntu...
Any ideas?
PS:
Sorry for may english :)

---

### Post by ivomans on 2005-07-18
After lots of Google-ing and reading doc-files I came to understand:

Load the required modules first: (values can be different for every system)
 ```
modprobe  isdn
  modprobe hisax type=3 protocol=2 irq=9 io=0x180
``` 

Then I found (from [http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009876.html]("http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009876.html") ) that you need to give these commands
 ```
$ sudo sh -c 'for i in isdnctrl0 ippp0 isdninfo;do ln -s /.dev/$i /dev/$i;done'
$ sudo ln -s /dev/isdnctrl0 /dev/isdnctrl
``` 
 Then reinstall the isdnlog packages:
 ```
 $ sudo apt-get install isdnlog --reinstall
``` 

At least I don't get any errors anymore. Tomorrow I'll try if things are also actually doing something usefull.

This might help for Nibbio as well?

---

### Post by nibbio on 2005-07-20
[QUOTE=ivomans]After lots of Google-ing and reading doc-files I came to understand:

Load the required modules first: (values can be different for every system)
 ```
modprobe  isdn
  modprobe hisax type=3 protocol=2 irq=9 io=0x180
``` 

Then I found (from [http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009876.html]("http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009876.html") ) that you need to give these commands
 ```
$ sudo sh -c 'for i in isdnctrl0 ippp0 isdninfo;do ln -s /.dev/$i /dev/$i;done'
$ sudo ln -s /dev/isdnctrl0 /dev/isdnctrl
``` 
 Then reinstall the isdnlog packages:
 ```
 $ sudo apt-get install isdnlog --reinstall
``` 

At least I don't get any errors anymore. Tomorrow I'll try if things are also actually doing something usefull.

This might help for Nibbio as well?[/QUOTE]
 Tnx ivomans, following the link you posted i found the pach file that fix this bug. I don't now how  to apply a patch, but i modified the "/etc/isdn/init.d.functions" by hand following the diff file and now all works perfectly.
You have also solved my other problem, now i found how to load hisax modules in the right way, tnx another time! :)

---

### Post by gatiba on 2006-01-10
Nibbio my girlfriend have the same card, winbond 6692, but i can't figure out how to make it works on Breezy. Could you help me or simply give me an howto? (Sorry for my english) :(

---

### Post by nibbio on 2006-01-12
After upgrading my Hoary into the new Breezy Ubuntu my isdn card stopped working. Installing the new isdn-utils i selected the option to install the new configuration files hoping the bug had been solved. Unfortunately at next boot the isdn cart wasn't configured properly and it doesn't work. Then i tried to reconfigure all as before the upgrade but this doesn't solved the problem.
After same attempt i concluded the problem is that the devices needed in "/dev" wasn't created at bootup. Adding the following lines:
```

cd /dev
MAKEDEV isdnmodem isdnbri dcbri isdn-io isdn-tty isdn-ippp
ln -s /dev/isdnctrl0 /dev/isdnctrl
```
in the "/etc/init.d/isdnutils" script the card start woking. I think the best place to insert the three line of code is near the top of the script in the case section where the isdnutils are started. Here a peace of code that explain where i put the new three lines:
```

[...]
# source the function definitions for stopping / starting the various parts

. /etc/isdn/init.d.functions



#isdn_verbose=true     # default is set by VERBOSE in /etc/default/rcS

case "$1" in
    start)
#START of section where to insert the extra code <==========================
	cd /dev
	MAKEDEV isdnmodem isdnbri dcbri isdn-io isdn-tty isdn-ippp
	ln -s /dev/isdnctrl0 /dev/isdnctrl
#END of modified section <==================================================
    if [ ! -z "$2" ]; then
        service="$2"
	case "$service" in
	    ipppd|isdnlog) ;;
	    *) log_failure_msg "Unknown ISDN service to stop: $2"; exit 1
	esac
[...]

```
With the new distro is solved also the problem that when the sistem was under heavy load the connection stop working until the sistem load come back to normal usage.
I Hope you can solve the problem, i'm not an expert but if you need further info i'm here :)

---

### Post by yshsu168 on 2006-01-16
[QUOTE=gatiba]Nibbio my girlfriend have the same card, winbond 6692, but i can't figure out how to make it works on Breezy. Could you help me or simply give me an howto? (Sorry for my english) :([/QUOTE]

I have a winbond 6692 based ISDN pci card too.
When I try "sudo modprobe hisax type=3 protocol=2 irq=9 io=0x180", it shows that
"FATAL: Error inserting hisax (/lib/modules/2.6.12-10-386/kernel/drivers/isdn/hisax/hisax.ko): No such device
"
Did I forget to install some thing?? My OS is Ubuntu Breezy 2.6.12-10-386;
Any suggest on driving this card is welcomed. Thank you in advance.

---

### Post by gatiba on 2006-01-16
[QUOTE=yshsu168]I have a winbond 6692 based ISDN pci card too.
When I try "sudo modprobe hisax type=3 protocol=2 irq=9 io=0x180", it shows that
"FATAL: Error inserting hisax (/lib/modules/2.6.12-10-386/kernel/drivers/isdn/hisax/hisax.ko): No such device
"
Did I forget to install some thing?? My OS is Ubuntu Breezy 2.6.12-10-386;
Any suggest on driving this card is welcomed. Thank you in advance.[/QUOTE]

Try this: **sudo modprobe hisax type=36 protocol=2**

---

