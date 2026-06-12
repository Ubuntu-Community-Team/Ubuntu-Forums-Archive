---
title: "Getting &quot;No rule to make target 'install'. Stop.&quot; while installing vpnclient"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by boombastic2 on 2016-08-07
So I'm trying to install softether vpn client. I got the tar.gz archive and extracted it, noticed there's no .deb file so I remembered I need to do ```
sudo make
```. It created additional two files: vpnclient and vpncmd. Trying to do ```
sudo make install
``` ends up with ```
make: *** No rule to make target 'install'.  Stop.
``` I realized that I may have to download dependencies, something like ./configure? But I have no idea where I could possibly find them. I found nothing in readme file about them.

Place I downloaded it from [http://www.softether-download.com/en.aspx?product=softether](http://www.softether-download.com/en.aspx?product=softether)

Screenshot
[IMG]http://i.imgur.com/pF7sfg1.png[/IMG]

---

### Post by steeldriver on 2016-08-07
The software does not appear to "install" in the traditional sense

If you look at what the Makefile does by default, e.g.
```

$ make -n
./.install.sh

```

you can see it just runs the (hidden) ./.install script, which should have led you through a licence agreement paperchase, culminating by building the client and then offering the following instructions:

```

*** How to start the SoftEther VPN Client Service ***

Please execute './vpnclient start' to run the SoftEther VPN Client Background Service.
And please execute './vpncmd' to run the SoftEther VPN Command-Line Utility to configure SoftEther VPN Client.

Of course, you can use the VPN Server Manager GUI Application for Windows / Mac OS X on the other Windows / Mac OS X computers in order to configure the SoftEther VPN Client remotely.


*** For Windows users ***
You can download the SoftEther VPN Server Manager for Windows
from the http://www.softether-download.com/ web site.
This manager application helps you to completely and easily manage the VPN server services running in remote hosts.


*** For Mac OS X users ***
In April 2016 we released the SoftEther VPN Server Manager for Mac OS X.
You can download it from the http://www.softether-download.com/ web site.
VPN Server Manager for Mac OS X works perfectly as same as the traditional Windows versions. It helps you to completely and easily manage the VPN server services running in remote hosts.

--------------------------------------------------------------------

```

---

### Post by boombastic2 on 2016-08-07
But wait how do I exactly run the program with the GUI (if there is any). I only found so far to configure it by running ./vpncmd. I'm guessing I need to run the client to get the GUI.

This question sounds dumb to You but I'm just learning (x)ubuntu, that's why I have dual boot of it with Win8. :)

---

