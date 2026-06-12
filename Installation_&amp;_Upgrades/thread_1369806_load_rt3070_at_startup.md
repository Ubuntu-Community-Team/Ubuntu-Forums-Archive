---
title: "load rt3070 at startup?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by gannggstaz on 2010-01-01
I have successfully installed the ralink rt3070 driver and it got my wireless usb drive to connect. The only problem is that I have to run the following commands to initiate it

```
cd /home/james/.2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux
sudo /sbin/insmod rt3070sta.ko
```

It may not seem like much, but it would be nice to get this to run on startup. I've made a command for it and click on a launcher for it, but when I put it into the startup applications list it doesn't work. 
There are instructions included in the rt3070 folder:
```
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'    
```

But I'm pretty sure 9.10 doesn't have/use these directories.

I am running ubuntu 9.10, and wireless usb is the EnGenius Wireless N USB Adapter EUB9706

---

### Post by khelben1979 on 2010-01-01
Have you tried to place the script in the /etc/init.d/ directory? 

(On Debian there's a lot of startup scripts which is executed from that path, not sure about Ubuntu.)

---

### Post by stefanmuc2k on 2010-06-27
> **gannggstaz said:**
> I have successfully installed the ralink rt3070 driver and it got my wireless usb drive to connect. The only problem is that I have to run the following commands to initiate it

```
cd /home/james/.2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux
sudo /sbin/insmod rt3070sta.ko
```


I think the problem is that the install script of the rt3070 driver doesn't work correctly. It doesn't seem to put rt3070sta.ko anywhere where the system can find it. I'm using lucid with kernel 2.6.32-21, so I created a directory here:

```
mkdir /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt3070

```

Then I copied the rt3070sta.ko into that directory and ran 
```
depmod
```

After that you should be able to use modprobe to insert the module into the kernel:
```
 modprobe -i rt3070sta
```

(If you've inserted the driver with insmod before, then you need to remove it with "modprobe -r" first.)

I also put rt3070sta into /etc/modules, but I'm not sure if it's really necessary. Doesn't do any harm, at least.


Probably far too late to help you, but I had the same problem and didn't see a solution anywhere. Maybe it helps the next guy.

---

