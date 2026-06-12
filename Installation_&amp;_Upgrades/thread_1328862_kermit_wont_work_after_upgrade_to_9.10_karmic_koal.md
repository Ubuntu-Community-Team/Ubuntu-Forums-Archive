---
title: "kermit wont work after upgrade to 9.10 karmic koala"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by cheshirekow on 2009-11-16
**---edit---** 
I managed to get ckermit working by downloading the source from [ftp://kermit.columbia.edu/kermit/archives/cku211.tar.gz]("ftp://kermit.columbia.edu/kermit/archives/cku211.tar.gz"). It was a nice, easy install: 

1. make linux 
2. make install 
3. sigh of relief

**---end edit---**

I had ckermit installed and had used it before in 9.04 without a problem. After upgrading to 9.10 I cannot run kermit. I can't even get any information out of it. I run the command "kermit" and all I get is "Segmentation fault". I tried to uninstall it with "apt-get remove ckermit" and then reinstall it with "apt-get install ckermit" but still have the same problem. 

I'm trying to connect to a device on the serial port (/dev/ttyS0) so I also tried "kermit -l /dev/ttyS0" but the same result: "Segmentation fault". 

Any suggestions? Any information?

Thanks

---

