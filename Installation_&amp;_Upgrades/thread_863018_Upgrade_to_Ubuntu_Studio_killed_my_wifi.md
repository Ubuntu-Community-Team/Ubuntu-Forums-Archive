---
title: "Upgrade to Ubuntu Studio killed my wifi"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Kenhillmusic on 2008-07-18
Hey everybody. Im very new to linux and I seem to have come to a problem. I had installed madwifi on Ubuntu HH and my wifi was working great, then i upgraded to the Ubuntu Studio kernel and audio apps/plugins and when i rebooted, I had no wifi.
PLEASE HELP!!!

---

### Post by coffeecat on 2008-07-18
I have no experience of madwifi but I believe you have to compile madwifi drivers against the kernel. Was that so?

If this is so, the drivers you compiled will not work against the new Studio kernel and you will have to reinstall them. However, you should still have the original Ubuntu kernel (and all modules) still on your system. Why not boot up with the Ubuntu kernel just to make sure nothing else has gone wrong? Then you could try reinstalling the madwifi drivers against the Studio kernel.

Sorry this is so vague. Perhaps you could post the link of the method you used to install madwifi.

---

### Post by schauerlich on 2008-07-18
If you still have the extracted folder with madwifi in it, then go into a terminal and try:

```

cd /path/to/madwifi/folder (Somewhere in your /home/USERNAME folder most likely)
make
sudo make install-modules

```

You will then need to reboot for the changes to take effect.

---

### Post by Kenhillmusic on 2008-07-18
> **EDavidBurg said:**
> If you still have the extracted folder with madwifi in it, then go into a terminal and try:

```

cd /path/to/madwifi/folder (Somewhere in your /home/USERNAME folder most likely)
make
sudo make install-modules

```

You will then need to reboot for the changes to take effect.

when i enter make i get

cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.



and how would i boot from the old kernel?
(sorry im such a n00b guys :P)

---

### Post by Kenhillmusic on 2008-07-18
ok i booted with the original kernel and wifi works fine, but i need to find out how to get it working in studio

---

### Post by schauerlich on 2008-07-18
> **Kenhillmusic said:**
> when i enter make i get

cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.



and how would i boot from the old kernel?
(sorry im such a n00b guys :P)

That's not the folder madwifi came in. Here's how to download madwifi and install it:

```

sudo apt-get install build-essential autoconf automake
wget http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz
tar -zxvf madwifi-trunk-current.tar.gz
cd madwifi-trunk-r*
make
sudo make install-modules

```

---

