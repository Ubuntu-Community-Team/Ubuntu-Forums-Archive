---
title: "Upgraded to 11.10 but halts during boot sequence."
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by andrew287 on 2011-10-15
15 October 2011

Upgraded from 11.04 64 bit to 11.10 64 bit Intel® Core™ i3-2100 CPU @ 3.10GHz × 4 
Halts during boot sequence.
Now waiting patiently for 11.11 but in the meantime it can be made to work, here are some initial steps that I found to be necessary ...

1. When booting halts ... Ctrl + Alt + F1
2. Login
3. Sudo su   (login again as root user)
4. pico /etc/network/interfaces and verify that eth0 is present, here is a basic configuration that will get you connected to the Internet from your 11.10 desktop. Where 123.456.71.83 is the static IP assigned to you by your ISP.

auto lo eth0
iface lo inet loopback

iface eth0 inet static
    network 123.456.71.80
    gateway 123.456.71.81
    address 123.456.71.83
    broadcast 123.456.71.87
    netmask 255.255.255.248
    
    pre-up /sbin/ifconfig $IFACE mtu 1492

5. Navigate to /var/run/dbus
6. rm pid  (delete PID file)
8. pico /etc/init/failsafe.conf (edit this file to reduce timeout delays)
9. reboot

Here are the steps I use on a daily basis to get to the 11.10 Desktop

1. When booting halts ... Ctrl + Alt + F1
2. Login
3. Sudo su   (login again as root user)
4. Navigate to /var/run/dbus
5. rm pid  (delete PID file)
6. reboot
7. 11.10 desktop appears but cannot connect to internet.
8. open terminal
9. sudo su  (login as root user)
10. /etc/init.d/networking restart (Internet should work now)

Andrew

---

### Post by afajknaz on 2011-10-15
Thanks, I too have the problem with my Nokia Booklet 3G and lubuntu.
I followed the guide to point 4. Then, when configuring network, I skipped 'network' and 'broadcast' because I don't understand them and didn't know what to put in there to make it work on my machine. Also, I put 'pre-up /sbin/ifconfig $IFACE mtu 1492' as written, w/out any mods because I don't understand it either.
Anyway, after this I continued with the guide, but I'm stuck at 
'7. 11.10 desktop appears but cannot connect to internet.'
The desktop doesn't appear, the OS halts again.

---

### Post by andrew287 on 2011-10-15
The key point seems to be to delete the pid file as this always works for me.

Try this again...

1. When booting halts ... Ctrl + Alt + F1
2. Login
3. Sudo su   (login again as root user)
4. Navigate to /var/run/dbus
5. rm pid  (delete PID file)
6. reboot

The network interface configuration is something that can be sorted out after you have successfully reached the 11.10 desktop.

However it may be a different situation with a Nokia tablet, my setup is a standard PC Desktop.

Cheers and good luck !

Andrew

---

### Post by afajknaz on 2011-10-15
> **andrew287 said:**
> The key point seems to be to delete the pid file as this always works for me.

Try this again...

1. When booting halts ... Ctrl + Alt + F1
2. Login
3. Sudo su   (login again as root user)
4. Navigate to /var/run/dbus
5. rm pid  (delete PID file)
6. reboot

The network interface configuration is something that can be sorted out after you have successfully reached the 11.10 desktop.

However it may be a different situation with a Nokia tablet, my setup is a standard PC Desktop.

Cheers and good luck !

Andrew
Sadly, it doesn't work. 
I looked into some logs:
boot is empty
kern.log contained some errors and warnings:
```

[Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
...
ERST: Table is not found
...
EISA: Cannot allocate resource for motherboard
 Cannot allocate resource for EISA slot 1
... (2,3,4,5,6,7)
 Cannot allocate resource for EISA slot 8
...
init: plymouth-stop pre-start process terminated with status 1
init: lxdm main process terminated with status 1
(end of file
```boot.log was much like kern.log, the same errors except for the last 2.
dmesg didn't show anything suspicious.
syslog looked very much like kernel.log too, I didn't verify they are identical, but they look so.
lxdm.log:
```
error: unexpectedly disconnected from boot status deamon
...
FATAL: Module emgd not found
(EE) Screens(s) found, but none have a usable configuration.

Fatal server error:
no screens found
...
```Xorg.0.log:
```
...
[drm] failed to load kernel module "emgd"
(II) EMGD(0): Graphics hardware initialization failed
(II) EMGD(0):   The cause was a failure to connect with the DRM during PreInit().
(II) EMGD(0): Cannot open connection with the DRM
...
```So it seems something's wrong with my EMGD driver...what can I do about it?



BTW, it's a netbook, not tablet.

---

### Post by andrew287 on 2011-10-15
Sorry but I am not much help to you as it would seem it is something specific to your Nokia hardware configuration and outside my knowledge scope.

I attempted an upgrade from a highly configured and optimized 11.04 installation. Perhaps if I had have done a fresh install from a live CD it would have booted without any issues.

If you are in the same situation we my have to keep reading the posts for a better solution or wait for 11.11 . I note that there are many bug reports about this issue in the pipeline. I prepared my original post from these bug reports, at least I can use 11.10 and move on with it, but it is quite an ordeal to startup after a reboot.

If you can start from scratch again, then a live CD or USB install would be the best solution.

Cheers

Andrew

---

### Post by afajknaz on 2011-10-15
> **andrew287 said:**
> Sorry but I am not much help to you as it would seem it is something specific to your Nokia hardware configuration and outside my knowledge scope.

I attempted an upgrade from a highly configured and optimized 11.04 installation. Perhaps if I had have done a fresh install from a live CD it would have booted without any issues.

If you are in the same situation we my have to keep reading the posts for a better solution or wait for 11.11 . I note that there are many bug reports about this issue in the pipeline. I prepared my original post from these bug reports, at least I can use 11.10 and move on with it, but it is quite an ordeal to startup after a reboot.

If you can start from scratch again, then a live CD or USB install would be the best solution.

Cheers

Andrew
I'm not happy with it, but I can do it. Thanks.

---

### Post by andrew287 on 2011-10-15
Hi,

This morning (Sydney time) I tried the suggestions from Wergorz and Codac ....

sudo mv /var/run/* /run/
sudo mv /var/lock/* /run/lock/
sudo rm -r /var/run
sudo rm -r /var/lock
sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock
sudo rm /run/dbus/*


This works perfectly for me and fixes all the startup and internet connection issues. Now I can use 11.10 without any workarounds. Hope it works for you.

Cheers

Andrew

---

