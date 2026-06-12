---
title: "Ubuntu 12.04 does not start after instalation of dbus 1.8.6."
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by mariusz3 on 2014-08-11
Hello, I have Ubuntu 12.04 with kernel 3.2.0-29-generic-pae 

I followed the maunal build and instalation of BlueZ component from the: [http://www.linuxfromscratch.org/blfs/view/svn/general/bluez.html](http://www.linuxfromscratch.org/blfs/view/svn/general/bluez.html)

After instalation the bluetooh worked I even connected from my phone to Ubuntu. 
Unfortunatelly after reboot the xwindow system does not start. 

I enabled the full list of output messages and I can see the error:```

...
unable to connect to system bus: Failed to connect to socket **/var/run/dbus/system_bus_socket**: No such file or directory
* Starting AppArmor profiles
speech-dispatcher disabled; edit /etc/default/speech-dispatcher [OK]
saned disabled; edit /etc/default/saned

```
And nothing happenes after that.
I still can run other consoles and I checked the folder** /var/run/dbus** - it is empty. 

I tried to run **sudo apt-get upgrade** but network does not work - no configuration for eth0. 
I'm convinced that it is a fault of dbus service that I installed during installation of BlueZ. 
I even removed **dbus** script from **/etc/init.d/ **- it did not help.

I have no more ideas what to do.

---

### Post by mörgæs on 2014-08-12
Hi, welcome to the fora.

There's no need for building Bluez. It's available in the repositories.

---

### Post by mariusz3 on 2014-08-12
Ok I will try that but currently my system does not strat and I would like to fix this issue to learn something.

---

