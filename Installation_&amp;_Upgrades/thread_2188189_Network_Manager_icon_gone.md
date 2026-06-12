---
title: "Network Manager icon gone"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by Muketeer on 2013-11-15
I think i have a similar problem. After upgrade to salamader on my lubuntu system, I started off with network manager recognising my wireless network through my USB wireless stick, but not connecting to the internet.  I followed this thread [http://ubuntuforums.org/showthread.php?t=1810541](http://ubuntuforums.org/showthread.php?t=1810541) which eventually directed me to here [http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545) which seems to involve cutting out some of the drivers for the wireless stick.  It worked until i rebooted this morning, and now my network manager icon is gone.  Please can someone help me sort this out?  Thanks!

---

### Post by Muketeer on 2013-11-15
Incidentally, i had the driver rt2800usb which the former site recommended i disable in favour of another driver.  Now nothing works! Tried the advice in this page, too [http://askubuntu.com/questions/337775/is-there-a-fix-to-the-ubuntu-13-04-wi-fi-connection-woes](http://askubuntu.com/questions/337775/is-there-a-fix-to-the-ubuntu-13-04-wi-fi-connection-woes) but it seems to be talking about editing a file that doesn't exist on my system.  Thanks for any help anyone can offer!

---

### Post by syntaxerror74 on 2013-11-15
Hello, Lubuntu fellow. :) (There are not so many of us. :P)

> **Muketeer said:**
> It worked until i rebooted this morning, and now my network manager icon is gone.

I knew I wasn't dreaming away...(I did reboot the machine indeed after *apt-get upgrade* (way safer due to the wagonloads of libs updated))

---

### Post by oldos2er on 2013-11-15
Posts moved to their own thread. Rather than "hijacking" someone else's thread which is generally considered rude, please start a new one.

---

### Post by Muketeer on 2013-11-16
OK thank you, sorry for hijacking - not yet totally familiar with protocol.  Any suggestions, though?  My network manager icon has returned mysteriously, but now doesn't seem to detect or recognise the wireless network, and most of the usual options you get from clicking on the applet icon are also gone.  Very confused. Should i un-blacklist my original drivers?  How would i do that?

---

### Post by Muketeer on 2013-11-16
Just tried this too [http://linuxforums.org.uk/index.php?topic=852.0](http://linuxforums.org.uk/index.php?topic=852.0) installing new drivers for the ralink stick, but still no joy.  I don't seem to have the config.mk file it mentions, and i'm not sure where to make the changes it suggests.  There were a lot of error messages during installation, modprobe didn't work (Error: could not insert 'rt2870sta': Operation not permitted), and iwconfig reads lo       no wireless extensions.  Using the echo bit at the end didn't seem to help either, or rebooting.  Of course, i couldn't download and install build essentials or check install, because i can't get onto the internet!  I'd hoped that they were there from before the upgrade (how would i check this?).  Please help!

---

### Post by Muketeer on 2013-11-17
OK it now looks like the system isn't recognising the device at all (i've installed RutilT Wlan manager and additional drivers, and they say that there's no device and no drivers).  i've tried downloading and installing drivers from the mediatek website, but these don't seem to be compiling or installing properly using make and checkinstall.  I'm now camping out in the hallway, annoying my whole family, but at least i have a wired connection.  Please help me!  Thanks

---

### Post by Muketeer on 2013-11-17
have tried to install new drivers following [http://ubuntuforums.org/showthread.php?t=960642&highlight=rt28](http://ubuntuforums.org/showthread.php?t=960642&highlight=rt28) and [http://ubuntuforums.org/archive/index.php/t-1592731.html](http://ubuntuforums.org/archive/index.php/t-1592731.html) but run into problems with the make command:

cc1: some warnings being treated as errors
make[2]: *** [/usr/local/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/usr/local/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-13-generic'
make: *** [LINUX] Error 2

and then the make install command

install: cannot stat &#8216;rt2860sta.ko&#8217;: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/local/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
make: *** [install] Error 2

---

### Post by Muketeer on 2013-11-20
I don't seem to be getting any responses to this thread, perhaps because the title (which i didn't choose) isn't very specific.  i'll try again with a nice specific  title and watch the help roll in!  Wish me luck.

---

### Post by oldos2er on 2013-11-20
We prefer people not double post. If you wish to have staff re-title and/or move your thread, please use the 'Report Post' button and ask politely.  :)

---

### Post by syntaxerror74 on 2013-11-21
Ah! At least I can tell you where the problem source has to be located.

```

install: cannot stat &#8216;rt2860sta.ko&#8217;: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/local/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
make: *** [install] Error 2
```

A .ko is a pre-compiled **kernel module**.
So it says that you're missing this module.
And for that reason, this whole attempt may even become too specific for your case, since .ko files are normally created using *make modules* when compiling your kernel yourself. Let alone that you will have to exactly match your kernel version with the module version, otherwise there'll be lurking more unwanted surprises.

---

### Post by echotech2 on 2013-11-22
I have two Network Manager icons.  You can have one of mine, lol.

---

