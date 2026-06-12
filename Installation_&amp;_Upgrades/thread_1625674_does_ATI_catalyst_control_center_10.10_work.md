---
title: "does ATI catalyst control center 10.10 work?"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2010-11-19
Looking at the AMD/ATI download pages, I can't tell if catalyst control center (which installs the drivers) is fully functional for Ubuntu 10.10.

Has anyone had success with this software?

I have integrated ATI Radeon 3200 HD graphics on my motherboard and can't get things working.

---

### Post by Zookalicious on 2010-11-19
Hi raymondvillian! If you have not already tried this, see if Ubuntu has automatically detected your video drivers by going to System > Administration > Additional Drivers. 

Hopefully it will tell you that you have an AMD driver available and that you need to enable it. If so, click enable, and then restart your computer if prompted. This will install the Catalyst control Centre under System > Administration > Catalyst Control Centre. 

Let me know if this is of any help or if you have any questions. Good luck!

---

### Post by raymondvillain on 2010-11-19
Thanks, Zookalicious, but it didn't work.  This message appeared:

> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

/var/log/jockey.log is a big file and it has lots of lines I don't understand, but towards the end of the file appears

> WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

Does this tell you anything?

---

### Post by Zookalicious on 2010-11-19
That's interesting. Let's try this:

It looks like your system does not have fglrx installed, so open a terminal (Applications > Accessories > Terminal) and type in 
```

sudo apt-get update
sudo apt-get install fglrx
sudo apt-get upgrade

```
enter your password when prompted and answer Y whenever it asks if you want to continue. These commands will update your system as well as install the amd fglrx packages. Once this is done (it might take a while if you have not done an update before) you'll probably need to restart your computer. 

Once you have logged back in, try enabling that Driver again (it did show up as unactivated in "Additional Drivers" though correct?).

---

### Post by raymondvillain on 2010-11-19
Hi again, Zookalicious, tried your instructions but still not working.

Yes, the additional drivers window shows that fglrx is not activated, and after trying your suggestion I get the same error message.

This time the file /var/log/jockey.log has the lines

> 2010-11-19 15:51:18,587 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-11-19 15:51:18,589 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver

and there is no folder /sys/module/fglrx/drivers on my file system.

What to try next?

---

### Post by Zookalicious on 2010-11-19
Hmm. Well I guess we go back to the original way. 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English")

Assuming you are running a 64bit OS this should be the driver you're looking for. I'm not exactly sure how AMD does it's installations though, I've only ever used Nvidia graphics. It looks like it will make it from source for you, so just download the package on that page, right click, check "allow executing file as program" and then run it.

EDIT: I looked up the problems your having with jockey. It's a known bug unfortunately, I couldn't find a workaround but [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/496225](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/496225) might give you some more information.

---

