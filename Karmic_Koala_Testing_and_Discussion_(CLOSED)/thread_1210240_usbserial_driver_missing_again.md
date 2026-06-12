---
title: "usbserial driver missing again?"
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-07-11
> Reference: **[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002)**

SRU justification:

Impact: The builtin machanism will not attach some 3g modems if usbserial is not a module.

Fix: Change back usbserial to be a module.

Trying to test some 3G modems with Karmic I realised that **usbserial** is not an external driver (as in above Jaunty 'bug'). I missed it doing any upgrade or there is not there at all?

Additionally in many cases **wvdial** is very helpful to be included into standard distro. There are many Ubuntu users that they do not have ADSL modems. Some using mobile broadband others special 'rural' phone/modems. Most problems are solved using **usbserial** in conjunction with **wvdial** (searching within ubuntuforums.org you can find a lot similar cases). Is **wvdial** still 'excluded' from the standard 9.10 pack?

Regards,
George

---

### Post by GeorgeVita on 2009-07-12
Just for reference/update, I just downloaded the current daily-live 9.10 (12-JUNE-09) from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) using my **ZTE MF636**, connected with **wvdial** on Karmic Alpha2+updates, my local provider had a trasfer rate of 20-80KBytes/s, total download time around 6 1/2 hours! Network Manager was removed. 

usbserial is not yet a driver

```
g@KK:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
[sudo] password for g: 
FATAL: Module usbserial not found.
g@KK:~$ uname -a
Linux KK 2.6.31-2-generic #17-Ubuntu SMP Fri Jul 10 21:48:31 UTC 2009 i686 GNU/Linux
```

Searching Launchpad I found a bug already reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189)

Note that ZTE MF636 causes a lot of 'stucks' (system totally frozen) with Network Manager installed (0.7.1 or PPA version).

G

---

### Post by ranch hand on 2009-07-12
All I can say is that there are an awful lot of folks that use dialup and they need support.

I have been on DSL for a few months now for the first time in my life (I am 57).  Dial up may be slow but it works.

I got a kick, by the way, from the statement about how long updates take at 20-80kb/s.  Our last dial up connection, on a good day, would burn up the line at a roaring 4.4kb/s.  Yes you can update at that rate, you break it up and do it in 6-8 hour chunks.  No I did not download .iso files but ordering them online was easy and the USPS delivers quicker than they could be downloaded (assuming that your connection held up for that long - figure about 10Mb per hour).

Slow it may be but we need the support.

---

### Post by GeorgeVita on 2009-07-14
> **ranch hand said:**
> **All I can say is that there are an awful lot of folks that use dialup and they need support...Slow it may be but we need the support.**
> **HarryBhat said:**
> Thanks a lot for the reply buddy :)
**But how do I download from repositories if my only means of connecting to internet is my 3G Wireless Card which fails to connect now?** :(
> **ronacc said:**
> I can tell you from long experience , **when nothing else works a pots line will . 56k may be dog slow but its infintely faster than "no connection**" .
> **plun said:**
> **This wiki explains howto probe unrecognised modems**
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
> **ramnarayan said:**
> ... and then the developers go and drop the usb thingummy as well as wvdial **effectively locking people like me (from the rural and not so DSL connected places) out of the net.**
Thanks all for expressing your thoughts!
If you have **[COLOR="Green"]other option to vote[/COLOR]**, post it to bold/color to be shown clearly.

Regards,
George

---

### Post by ronacc on 2009-07-14
@ Ranchhand I have d/l'd .iso's with dialup , I just let it hammer away all night every night for a week :lolflag: I use a cable modem now ,but I stll have my dialup modem for times when the cable is out like it was for weeks during the 2004 hurricanes here in Florida ,  I can tell you from long experience , when nothing else works a pots line will . 56k may be dog slow but its infintely faster than "no connection" .

---

### Post by plun on 2009-07-14
I didnt vote because of no alternative.;)

udev has been changed several times and my Option-modem now works again.

But... I must use the highly experimental trunk ppa for the Network-manager

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)


This wiki explains howto probe unrecognised modems

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)


dmesg for my modem:
```
[15419.704073] usb 5-1: new full speed USB device using uhci_hcd and address 2
[15419.927565] usb 5-1: configuration #1 chosen from 1 choice
[15421.304092] usb 5-1: USB disconnect, address 2
[15422.395079] hso: /build/buildd/linux-2.6.31/drivers/net/usb/hso.c: 1.2 Option Wireless
[15422.395159] usbcore: registered new interface driver hso
[15422.487324] Initializing USB Mass Storage driver...
[15422.487448] usbcore: registered new interface driver usb-storage
[15422.489613] USB Mass Storage support registered.
[15423.564054] usb 5-1: new full speed USB device using uhci_hcd and address 3
[15423.729527] usb 5-1: configuration #1 chosen from 1 choice
[15423.736284] hso0: Disabled Privacy Extensions

```


This change is important which was introduced for Jaunty:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=commit;h=7ba0bba12ddae10cc0056187752fd39b04f1b16b](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=commit;h=7ba0bba12ddae10cc0056187752fd39b04f1b16b)
Instead of using zerocd or a mode switcher, this is probably needed for
more modems.

;)

---

### Post by ranch hand on 2009-07-14
One thing that bugs me is the assumption that you have to use an external modem.  I have a USR5610c internal.  It is a great modem and takes up no space outside my box.

It was kind of a pain in Hardy, worse in Intrepid and I have not used it in Jaunty but assume it is worse.

Winmodems are too slow and kind of silly.  Hardware modems work fine and internal ones are a lot more convenient to use than externals.

---

### Post by ronacc on 2009-07-14
I like my USR external modem because I can eaisly move it from box to box, also it's hard to find an internal modem that isn't a winmodem and I wouldn't use a winmodem on a bet .

---

### Post by ranch hand on 2009-07-14
Internal or external USR hardware modems just get the best possible connection and hold it.

---

### Post by ronacc on 2009-07-14
I've been using USR since the stone age.:lolflag:

---

### Post by ramnarayan on 2009-07-14
Good Poll George,

Am totally frustrated with Ubuntu since 8.04 - one particular set of devices USB - Serial CDMA Fixed Wireless Phones have stopped working on Ubuntu since 8.04 and then the developers go and drop the usb thingummy as well as wvdial effectively locking people like me (from the rural and not so DSL connected places) out of the net. Frankly 9.04 sucks - I am still on 7.10 dual booted with 9.04 and am wondering, that, is there an alternative Linux that runs the latest kernal and apps and also runs wvdial and my problematic device, 

found that pclinuxos 2008 running kernal 2.28.xx seems to work well - and thats definitely a small step up from Ubuntu 7.10.

ram

---

### Post by GeorgeVita on 2009-07-14
> **ronacc said:**
> I've been using USR since the stone age.:lolflag:
Which age was the following? (I was using this set...)
TRS80 model I connected via acoustic coupled modem!
You could buy a small car (in Europe) instead of buying this pair!
[http://www.youtube.com/watch?v=5WCTn4FljUQ](http://www.youtube.com/watch?v=5WCTn4FljUQ)

The funny is that connections is/was done with the same ATDT command as today with our 3G HSDPA modems! Both modems can work with wvdial!

Regards,
George

---

### Post by ronacc on 2009-07-14
> **GeorgeVita said:**
> Which age was the following? (I was using this set...)
TRS80 model I connected via acoustic coupled modem!
You could buy a small car (in Europe) instead of buying this pair!
[http://www.youtube.com/watch?v=5WCTn4FljUQ](http://www.youtube.com/watch?v=5WCTn4FljUQ)

The funny is that connections is/was done with the same ATDT command as today with our 3G HSDPA modems! Both modems can work with wvdial!

Regards,
George

C64 and actualy at that time it was a 300 baud commodore modem , went with USR when I got my Amiga .

---

### Post by GeorgeVita on 2009-07-14
> **ronacc said:**
> **C64** and actualy at that time it was a **300 baud commodore modem** , went with USR when I got my Amiga .
This was ... before stone age! On these machines you could do some 'programming' using the installed BASIC interpreter. Later this 'active' function removed from win PCs but remains in our O.S. (python, etc).

My opinion about peripherals/drivers and especially modems is that we need ALL of them because they connect us. That's why I believe an old fashioned driver or program must exist till replaced clearly after complete debugging and documentation. Nobody wants to compete various solutions just one may 'fit' better than the other to some users.

Regards,
George

---

### Post by GeorgeVita on 2009-07-23
Update: I just downloaded the 9.10 Alpha3 using my **ZTE MF636**, connected with **wvdial** running on an installed Karmic Alpha2+updates. Network Manager was 'purged' (with N.M. I cannot use my PC and the MF636). With a trasfer rate of 20-40KBytes/s it took 11h12m to download (modem, provider and my enthusiasm tested=OK).

Hard Disk formatted, new installation done.

Although the situation is not changed:```
sg@KKa3:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
[sudo] password for g: 
**FATAL: Module usbserial not found.**
g@KKa3:~$ uname -a
Linux KKa3 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:04:41 UTC 2009 i686 GNU/Linux
g@KKa3:~$
```
From the typical 'bug' report it seems that **usbserial** will be a driver in a future update of the kernel.
Ref.: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189) 

Thanks,
George

---

### Post by wayne_cat on 2009-07-23
> **GeorgeVita said:**
> Update: I just downloaded the 9.10 Alpha3 using my **ZTE MF636**, connected with **wvdial** running on an installed Karmic Alpha2+updates. Network Manager was 'purged' (with N.M. I cannot use my PC and the MF636). With a trasfer rate of 20-40KBytes/s it took 11h12m to download (modem, provider and my enthusiasm tested=OK).

Hard Disk formatted, new installation done.

Although the situation is not changed:```
sg@KKa3:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
[sudo] password for g: 
**FATAL: Module usbserial not found.**
g@KKa3:~$ uname -a
Linux KKa3 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:04:41 UTC 2009 i686 GNU/Linux
g@KKa3:~$
```From the typical 'bug' report it seems that **usbserial** will be a driver in a future update of the kernel.
Ref.: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397189) 

Thanks,
George

I'm testing 2.6.31-4 at the moment ... it has the module
```
/lib/modules/2.6.31-020631rc4-generic/kernel/drivers/usb/serial/usbserial.ko
```

---

