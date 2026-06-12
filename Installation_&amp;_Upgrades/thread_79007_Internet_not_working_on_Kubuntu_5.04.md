---
title: "Internet not working on Kubuntu 5.04"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by duffmckagan on 2005-10-19
I cannot get the internet working on Kubuntu.
I even can't see GUI for configuring that.

I don't really understand why is that!  ..The following commands worked fine on Debian Sarge.

```

ifconfig eth0 up   ... works

ifconfig eth0 inet netmask 255.255.255.0

ifconfig eth0 inet broadcast xx.xx.xxx.255

ifconfig eth0 inet address xx.xx.xxx.xxx

route add default gw xx.xx.xxx.1


```

I need to set the above things to get my Internet Connection working.

Static IP address.  --LAN Connection.




I know that this is the old version ...I should download the new Breezy Badger, but I was just givin' Kubuntu a try, and had this only version Handy.

Moreover, during the install process I selected the option of "Configuring Internet" later, as I had experienced problems with the installer.

Problem while installing Ubuntu, apt-get started looking for an Internet connection to get the updates or stuff like that, and the install process hung there. NO progress after that. 
So, not to repent later, I did this, but now I can't configure the Internet to work on Kubuntu.


Thank you.

---

### Post by rmjokers on 2005-10-19
I am slightly confused by your post.  Are you saying that the commands you attached dont work if you execute them on your system?  If they fail, what type of message do you get?  What does the output from:

sudo ifconfig -a

look like?  There should be a network configuration application available in the KDE Control Center under Internet & Network -> Network Settings.

---

### Post by duffmckagan on 2005-10-19
>  Are you saying that the commands you attached dont work if you execute them on your system?

Yeah. They don't excecute. They give me an error message. (same for all ...umm sorry about that! but I forgot to not it down. I will post that tomorrow. (Late night here.)



> >look like? There should be a network configuration application available in the KDE Control Center under Internet & Network -> Network Settings.

I did not find any!
I will take a closer look at the KDE Control center again tomorrow.

---

### Post by rmjokers on 2005-10-19
Dont forget that you have to use 'sudo' to run those ifconfig commands as they require root privilege.

---

### Post by duffmckagan on 2005-10-19
Yes man! 

Without sudo, Kubuntu won't even tell me that there is a command like that!

All the commands were executed after sudoing.
I thought the Root environment variable and crap like that would be causing problems, so I used the passwd to throw up a password for the root, but still no luck.


I should have noted the Error message and posted it here, but sorry for that.

I will post it soon!
Hold on.

---

### Post by duffmckagan on 2005-10-20
I get the following error while I try the aforementioned commands.

```

Error: SIOCSIFBRDADDR: Cannot assign requested address

```


Moreover, the ifconfig -a command gives the following output.


```

root@copperskull:/home/amit # ifconfig -a
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet6 addr: fe80::4e00:10ff:fe00:c0cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:449 errors:186 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47506 (46.3 KiB)  TX bytes:378 (378.0 b)
          Interrupt:11 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1800 (1.7 KiB)  TX bytes:1800 (1.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

### Post by duffmckagan on 2005-10-20
Please also suggest a method to setup the network, permanently. I now realize my mistake of not configuring the Network during installation, but I still know there is some workaround. 

But what is that??????????

Thank you.

---

### Post by rmjokers on 2005-10-20
My only other idea would be that perhaps the order of the ifconfig commands matters (maybe the interface needs an address before it allows the mask and broadcast to be set).  Try this:

sudo ifconfig eth0 *.*.*.* netmask 255.255.255.0 up

where *.*.*.* is the address you want.  If it still complains, then you may have some sort of ethernet driver problem (look at output from dmesg).

To add this configuration stuff permanently, you can put in in /etc/network/interfaces.  There is a manual page that describes what to do at:

man interfaces

---

### Post by duffmckagan on 2005-10-20
[FONT=verdana, arial, helvetica][SIZE=2]Yes. Now I know. 

But the last time I edited the /etc/network/interfaces file, I was surprised to see that nothing happened.

Haha! I forgot to restart the network.
```

/etc/init.d/network restart

```

This should solve the problem, but lets see.

I will surely post back the results.   :)
[/SIZE][/FONT]

---

### Post by duffmckagan on 2005-10-21
I edited the /etc/network/interfaces file, but no good yet. 

Internet still not working. 

I also did a 

```

/etc/init.d/networking start

```

It gave me a message saying OK, But then when I tried to ping my Gateway, it said 
>Network Unreachable.  :(





Now I am seriously thinking of adding the Debian Sarge CD 1 to the /etc/apt/sources.list and then installing Etherconf to solve my problem. 
I think it is gonna be a sureshot win, but not worth the hassles. 


Any other idea where I went wrong?

---

### Post by duffmckagan on 2005-10-21
Internet working fine after a good nice restart.   :)


Editing the /etc/network/interfaces file did the job.   :)

---

### Post by rmjokers on 2005-10-21
So, manually configuring the interface with ifconfig like this:

sudo ifconfig eth0 *.*.*.* netmask 255.255.255.0 up
 
does not work (where *.*.*.* is the address you want)?

---

### Post by duffmckagan on 2005-10-21
It should have worked, but it did not when I tried it in the beginning. 

But everything went smooth after editing the /etc/network/interfaces file, and then restarting the computer.

Initially, when I tried to use the ifconfig commands, I got the error mentioned in my Post #6.

Thank you.  :)

---

### Post by duffmckagan on 2005-10-21
Searching for   >
Error: SIOCSIFBRDADDR: Cannot assign requested address 
I found that it is related to 

> 
>> it is result of IP-PNP being enabled.


---

