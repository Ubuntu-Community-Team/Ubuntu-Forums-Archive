---
title: "[newbie]  Ubuntu 8.10 Server Installation"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by jon80 on 2008-11-30
I have an Ubuntu 8.10 *Server* machine, and, I would like to do the following:

1. update the keyboard settings, preferably while still in command line
2. configure a network interface so that it interfaces with my existing router.  
3. install KDE / Gnome or some other desktop environment, for convenience.  
4. ubuntu is installed as a guest within VMWare Infrastructure, and, I pretty much can't scroll to view the whole screen.
5. ubuntu machine should be used to install Oracle Datawarehouse Builder 11g (if this fails I try 10g), has anyone carried out a similar installation before?

I've been skimming through the online documentation at [https://help.ubuntu.com/8.10/index.html](https://help.ubuntu.com/8.10/index.html), but found nothing specific so far.  

Information would be appreciated.

Failed resolutions
------------------
re: 2. So far only local host appears as a network interface; 
       starting up of eth0 using /etc/init.d/networking start fails
re: 3. I tried looking for /etc/inittab, but this does not seem to be available.

---

### Post by zvacet on 2008-11-30
To install GNOME 

```
sudo apt-get install ubuntu-desktop gdm
```

After that you will be able to configure your network with network applet.

Did you try to click on full screen button in Vmware?

Sorry,that is all I can suggest you.I´m sure that somebody else will be better help to you.

---

### Post by jon80 on 2008-12-01
> **zvacet said:**
> To install GNOME 

```
sudo apt-get install ubuntu-desktop gdm
```

After that you will be able to configure your network with network applet.

Did you try to click on full screen button in Vmware?

Sorry,that is all I can suggest you.I´m sure that somebody else will be better help to you.

Unfortunately I can't use apt-get because my network connection (no 2), is not available.

---

### Post by zvacet on 2008-12-01
Sorry for overlook.Try type in terminal

```
sudo pppoeconf
```


after that look in /etc/network/interfaces

and if you are connected with dhcp that file should look something like this

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

or if you use static adress 

> auto lo
iface lo inet loopback

auto et0

iface eth0 inet static
address 
netmask 
gateway 

you will put your address,netmask....

---

### Post by jon80 on 2008-12-02
Thanks,  I resolved the network problem by updating the /etc/network interfaces, since it was mapping to *eth0*, whilst this should have been *eth2 *.  

Attached details.

---

### Post by zvacet on 2008-12-02
Now you can install desktop of your choice. ;)

---

