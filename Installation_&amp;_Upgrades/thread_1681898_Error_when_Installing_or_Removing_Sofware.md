---
title: "Error when Installing or Removing Sofware"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by j_arshad on 2011-02-04
Hi,

Ive installed Ubuntu 10.10 on my netbook. My system has Broadcom PCI wireless card - BCM 4312 with PCI ID 14e4:04B5. When I installed the OS, I got a message that the system did not have the firmware for the wireless card and wanted me to download one from web. I first tried installing b43 kernel driver and it did not work. Then I tried the STA hybrid driver and got it working. Now, everytime I _install or remove_ any application, I get a message dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1¨ and though the application that I&#7743; trying to install or remove finally gets installed/removed, but still pops up the message.

 I need to know why this error pops and how to get rid of it.

Regards,
Arshad

---

### Post by sikander3786 on 2011-02-05
Welcome to the forums :-)

From Applications > Accessories > Terminal:

```
sudo apt-get remove --purge firmware-b43-installer
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

Please post the errors if any, straight in your post instead of attaching a .txt file.

---

### Post by j_arshad on 2011-02-05
Hi Sikander,

Thanks for your response.

I tried the codes given by you. When I try the code,

sudo apt-get upgrade

I get the following message:

Err [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main libebook1.2-9 i386 2.30.3-2ubuntu2.1
  The HTTP server sent an invalid Content-Range header
Err [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main nautilus-sendto-empathy i386 2.32.1-0ubuntu1.1
  Bad header line
Failed to fetch [http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.30.3-2ubuntu2.1_i386.deb](http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.30.3-2ubuntu2.1_i386.deb)  The HTTP server sent an invalid Content-Range header
Failed to fetch [http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_i386.deb](http://ubuntu.oss.eznetsols.org/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_i386.deb)  Bad header line
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any idea what should be done?

Thanks,
Arshad

---

### Post by sikander3786 on 2011-02-06
Change your server to Main from Software Center > Edit > Software Sources and try again.

---

### Post by j_arshad on 2011-02-06
It worked.Thanks.

---

