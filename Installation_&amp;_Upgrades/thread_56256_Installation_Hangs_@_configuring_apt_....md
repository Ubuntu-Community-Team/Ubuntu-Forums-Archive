---
title: "Installation Hangs @ configuring apt ..."
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by t2kburl on 2005-08-11
Installing hoary_amd64 on a new AMD64 3000+ system. It flies through everything including configuring the net with DHCP (as it should) and even found the SATA HD with no problems (as opposed to the misery it was to install XP on it) ...   but it gets up to configuring apt ... just a bit after setting the root password ... and it hangs at 25% - Setting up primary installation repository.

HELP !!   please  :)

I built this machine for a friend and I really want her to see what Ubuntu can do.

---

### Post by blind0wl on 2005-08-11
Will be an issue getting onto the net....reinstall using the command ```
expert
``` at the boot cd prompt...this will give you a couple more options...step through each one until you get to the apt configuration...make sure you dont select a mirror and just use cd.  Once youve completed the install, copy the repositories list located at [Ubuntuguide](http://www.ubuntuguide.org#extrarepositories) into your sources.list and run a ```
sudo apt-get update
sudo apt-get upgrade
```

This will work as long as you are connected to the net....

---

### Post by t2kburl on 2005-08-11
are the repos the same for amd64 arch?

edit > nm I see they are

still haven't got it yet

---

### Post by t2kburl on 2005-08-12
after several tries, I finally had to just stop the process of network configuration by pulling the ethernet cable  ...
then I got everything installed from the CD (base only, server install) ...  tried to sudo apt-get install ubuntu-desktop off the CD and it couldn't find it   ](*,) 

I'm not a nOOb when it comes to installs ...  I just got Gentoo up & running in Vmware ... have installed Ubuntu on several machines ...   but this one is kicking me

maybe I'll try installing a 32-bit Ubuntu and see what happens

---

### Post by blind0wl on 2005-08-12
Why are you trying to install ubuntu-desktop?  It should all ready have installed it via CD....thats how I set mine up at work as its a pain in the arse to get out of our proxy...Did you try doing as I suggested?  And in your sources.list, does it have a reference to the cdrom?

---

### Post by t2kburl on 2005-08-12
yes  ... everything was commented but the Cd in sources.list

I did a server install on that particular try ...

trying again now ...  it is now in the final stages of installation (normal install, this time, just no network)
planning on trying to config the net once I'm in gnome

---

### Post by blind0wl on 2005-08-12
Okay well if all else fails try the expert mode of install

---

### Post by t2kburl on 2005-08-12
ok ... now the only net device is lo   :(

in the device manager it shows the Yukon gigabit ethernet card ...  no idea what module I need to activate it

did lspci ...
shows Marvell Technology...Yukon Gigabit Ethernet  blah blah  ....   still no clue as th what to modprobe for

---

### Post by blind0wl on 2005-08-12
Try:

```
modprobe sk98lin
```

---

### Post by t2kburl on 2005-08-12
got it      :) 


tyvm

---

### Post by devkelso on 2005-09-21
> HELP !! please

A very poorly documented feature of debian-installer is setting the proxy environment variable.  To do this try the following:

* boot from cdrom (or any other install type but thats a different topic)
* at the "Boot: " prompt type "linux http_proxy='<my proxy server ip or dns><proxy port>'"
* install as normal

---

