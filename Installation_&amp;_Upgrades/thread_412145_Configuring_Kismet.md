---
title: "Configuring Kismet"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by colinireland on 2007-04-17
Could anybody tell me how I can get kismet to run.
Im using Dapper and installed the *.deb package of kismet. heres the output i recieved when i ran it.

root@Niloc:/etc/kismet# kismet
Server options: none
Client options: none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled. This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,INTEL'
root@Niloc:/etc/kismet#

I edited the config file with my suid, source, interface etc.
Ive tried inserting ipw2200 and atheros instead on intel but nothing seems to work.
Ive also tried installing kismet with the .tar file i downloaded with the same results.

Does anybody have any other ideas that could help me rectify this?

Any help would be much appricated

Colin

Any help would be greatly appricated

---

### Post by athleticbum32 on 2007-04-17
Many people have had problems with the deb. installation. One reason it may not be working for you is the librarys it needs are missing. I compliled it from the kismet wep site and had in working in no time. You can do this in the terminal:

#sudo su
#sudo aptitude install build-essential
#wget [http://www.kismetwireless.net/code/kismet-2007-01-R1b.tar.gz](http://www.kismetwireless.net/code/kismet-2007-01-R1b.tar.gz)
#tar zxvf kismet-2007-01-R1b.tar.gz
#cd kismet-2007-01-R1b
#sudo apt-get install libncurses5-dev
#./configure
#make dep
#make
#make install

Hopefully this help you out. It takes a little screwing around with but there is no reason it shouldn't work.

---

### Post by colinireland on 2007-04-17
> **athleticbum32 said:**
> Many people have had problems with the deb. installation. One reason it may not be working for you is the librarys it needs are missing. I compliled it from the kismet wep site and had in working in no time. You can do this in the terminal:

#sudo su
#sudo aptitude install build-essential
#wget [http://www.kismetwireless.net/code/kismet-2007-01-R1b.tar.gz](http://www.kismetwireless.net/code/kismet-2007-01-R1b.tar.gz)
#tar zxvf kismet-2007-01-R1b.tar.gz
#cd kismet-2007-01-R1b
#sudo apt-get install libncurses5-dev
#./configure
#make dep
#make
#make install

Hopefully this help you out. It takes a little screwing around with but there is no reason it shouldn't work.

I just tried that but now im getting:

colin@Niloc:~$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
colin@Niloc:~$

I opend the config file in /etc/kismet and my suid was set to colin, not "your_user_here". 
Is this version i installed opening up a different conf file from a different location? I searched my harddrive for another one but couldnt find any!

---

### Post by athleticbum32 on 2007-04-18
Did you unistall the old one first? My config file is in usr/local/etc.

---

### Post by colinireland on 2007-04-18
well i finally got it working. cheers for the help lads!

One final question. I am unable to connect to the internet after quiting kismet. I have a similar problem after using airodump. The only difference is after using airodump the green icon with the four green rectangles that indicates the wireless connection turns to just one yellow rectangle. After terminating kismet the four green rectangles remain but I still have no connection to the net.

Any ideas on how I can sort this out? I always have to reboot which is a pain.

---

### Post by athleticbum32 on 2007-04-18
When starting kismet it throws your wireless card into monitor mode. You can check this in iwconfig. When you exit kismet correctly it should go back into managed mode. Make sure that you quit kismet with the "Q" command. That will put everything back to normal. I havent got to aircrack yet but im sure there is something similar. Im having a few problems getting my new atheros card working with kismet. hope to fix that soon. Hope ive been a little help to you.

---

### Post by weblordpepe on 2007-12-01
I just did the instructions in the thread
and changed your_user_here to my username, however it wont start.
I know that I have a Broadcom wireless chip on eth1, however I can't seem to get kismet to start. 

Can anyone give me a quick pointer on how to get kismet running? On the Backtrack distro(liveCD) it starts up flawlessly.

---

### Post by Keen101 on 2008-01-01
It seemed to take me forever to figure out how to get kismet to work on my Ubuntu 7.10 system.

these links might be useful:


[http://kerneltrap.org/node/5414](http://kerneltrap.org/node/5414)
[http://www.wi-fiplanet.com/tutorials/article.php/3595531](http://www.wi-fiplanet.com/tutorials/article.php/3595531)
[http://ubuntuforums.org/showthread.php?t=504698&page=2](http://ubuntuforums.org/showthread.php?t=504698&page=2)

.............................


For me I installed kismet via synaptic, and then had to edit my configure file in

sudo gedit /etc/kismet/kismet.conf

and edit the line "source=sourcetype,interface,name"

to say "source=zd1211,eth0,ZyDAS USB" since i use a cheap Zydas USB dongle that I bought off ebay.

I also made a copy of the configuration file to /usr/local/etc/kismet.conf (just in case)

from what i hear Broadcom are tricky to get working.

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

12. Capture Sources
    
    A capture source in Kismet is anything which provides packets to the Kismet
    engine.  Capture sources define the underlying engine needed to capture
    data from the interface, how to change channel, and how to enter rfmon
    mode.  It is necessary to tell Kismet what specific type of card you use
    because different drivers often use different methods to report information
    and enter monitor mode.

    Source type     Cards               OS          Driver
    --------------- ------------------- ----------- -------------------------
    

    bcm43xx         Broadcom            Linux       BCM43XX
                    [http://bcm43xx.berlios.de](http://bcm43xx.berlios.de), kernel
                    Linux native broadcom drivers incorporated into modern
                     kernels. 

    b43             Broadcom            Linux
                    B43 broadcom drivers for current Broadcom devices in
                     Linux kernels

    b43legacy       Broadcom            Linux
                    B43 broadcom drivers for legacy Broadcom devices in
                     Linux kernels

    
    zd1211          ZyDAS USB           Linux       zd1211
                    [http://zd1211.ath.cx](http://zd1211.ath.cx)
                    The ZD1211 drivers have had some regressions which lead to 
                     data corruption while changing channel.  Some versions 
                     work, and typically the aircrack patches resolve the
                     corruption issues if your version doesn't properly handle
                     rfmon.

    Chipsets known to NOT WORK:
     Broadcom           - No linux drivers, only useable with ndiswrapper or
                          linuxant wrappers around windows drivers.
                          *** UPDATE ***
                          See the bcm43xx source type entry.  There are
                          experimental reverse-engineered drivers which have
                          monitor mode support now under Linux!  If they don't
                          work, however, then too bad.
     Airport Extreme    - Really a Broadcom, with no rfmon in the OSX drivers.
                          *** UPDATE ***
                          See the bcm source for linux on ppc, it MAY work, it
                          may not.  Currently theres no solution for OSX but
                          I'm looking for OSX hackers interested in redoing the
                          Kismet port and looking into adding more support.
     Atmel              - There is a hack for pseudo-monitor in USB.  There is
                          currently no equivalent hack for PCMCIA.
     HermesII           - Proxim successor to the Orinoco/HermesI.  No support
                          yet in the drivers, may be available in the future.
     ndiswrapper        - Anything using ndiswrapper is using WINDOWS drivers
                          AND CAN NOT BE USED WITH KISMET.

for you it might be

source=BCM43XX,eth1,bcm43xx

or something similar.

once you get that right, it should work by issuring "sudo kismet" in the terminal.

---

### Post by weblordpepe on 2008-01-04
Yeah I got it working fine in Ubuntu too. Although I can't remember what I did :)
I'm not using ndiswrapper.

---

