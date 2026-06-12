---
title: "Need help compiling or finding a compiled driver for an Asus PCE N15 NIC"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by Xelxa on 2012-12-07
Title pretty much says it all. I am running Ubuntu 12.10 and I have been unable to find a compiled version of the drivers and have been attempting to work with the one I got off the asus website. Their readme is fairly confusing (as it has almost no detail or direction) basically all it says is
'You can enter top-level directory of dirver and execute following command to compile, installation, or uninstall the driver:
1. Change to super user: sudo su
2. Compile driver from source code: make
3. Install the driver to the kernal: make install. reboot
4. uninstall driver: make uninstall reboot
or rmmod r8192ce_pci.ko
That's all it has in the readme. I'm brand new to Linux so it was hard to understand at first. But I tried entering the commands and have gotten plenty or error messages. When i try using make it starts running only to get a fatal error: openssl/ssl.h no such file or directory. I try apt-get install openssl/ssl.h and it returns 'E: release 'ssl.h' for 'openssl' was not found Although when I type in apt-get install openssl I get a message saying the 'openssl' is already up to date and then lists packages that were automatically installed and are no longer needed. Any help at all would be greatly appreciated.

---

### Post by steeldriver on 2012-12-07
Hello and welcome

To get the openssl/ssl.h header file I think you will need the  libssl-dev package (the openssl package itself just contains the bits needed for running ssl - not for compiling)

```
sudo apt-get install libssl-dev
```

There may well be other 'prerequisites' though - have a look in the downloaded driver directory and see if there is a README or INSTALL file that gives more detailed instructions than those on the website. 

If you want to take a step back and get help with your NIC driver in general, then I suggest posting a thread in the Networking and Wireless section where one of the networking gurus may be able to help you

---

