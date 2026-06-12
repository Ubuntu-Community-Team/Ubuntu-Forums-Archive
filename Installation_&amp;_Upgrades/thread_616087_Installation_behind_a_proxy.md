---
title: "Installation behind a proxy"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by mmasroorali on 2007-11-17
Dear All,

I have searched over the Internet and can  not find anything appropriate. I found some discussions but not anything definite.

At my office we are all behind a proxy, which unfortunately does not act as a gateway. It acts as a simple http proxy. 

After installation, I can set environment variables like http_proxy but during installation, connectivity to the outside world does not work. 

Can you please point out how can I set proxy before installation? 

I am using Gutsy by the way.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-18
There's 2 ways (that I know) for setting proxy in Ubuntu (Feisty & Gutsy):
[LIST=1]
[*]**System -> Preference -> Network Proxy**
This one will set proxy for your daily internet usage.
[*]**System -> Administration -> Synaptic Package Manager**
Then go to menu: Settings -> Preferences -> Network
This one will set proxy for getting packages from apt-sources.
[/LIST]

So I think for installation, you should try no. 2

---

### Post by bapoumba on 2007-11-18
Or set up the proxy in **/etc/apt/apt.conf**, but that's after the install:
[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

I have already installed Ubuntu behind my corporate proxy, and filling out the infos during the install process worked OK. Is it different with a simple http proxy? What is is BTW?
My univ offers wireless with such a simple http proxy (I think, sorry for being not so precise) and do not allow anything but web access. So I cannot run updates/upgrades using wireless (works fine with wired net access behind a squid proxy).

---

### Post by ryukocn on 2007-11-19
I have the same situation in Ubuntu 7.10 Installation.
It is a Sony notebook using VMWare Workstation 6.0.2.
Ubuntu 7.10 is supposed to work as Client VM in VMWare using bridge network connection to outside
DHCP networking environment. The LAN is connected using a simple http proxy proxy by providing a server name and a port number.  
The Desktop CD bootup is ok , and most of the installation processes are finished. 
At the last process , I think apt is trying to get security update, it stunked. 
I have been experiencing that apt will try to download security update before installaton is finished. 
I am wondering why not give me a choice to select if I want to update at that time or at the first time boot up?
Even Windows gives me such a choice.

---

### Post by bapoumba on 2007-11-19
As I said, I have already installed behind a proxy (squid, I have an http url and a port), but I always use alternate install CDs, and I get prompted for network specifications. Is not there such a setup with the LiveCD?

---

### Post by pete.dawgg on 2007-11-19
it all depends on the protocols/ports used for installation (download) and if the proxy allows those. most download-clients/web-browsers and most installers support proxies this way (among others) ```
http_proxy="http://user:pass@proxy:port"  program/ installscript
``` or you might try to export the http_proxy env-variable (same for ftp). 
but if the proxy blocks protocols or certain filetypes it may not work (check the response, if pkg.deb is a plaintext-file with a http-404 or 403 that's likely the case;)  )
there's other ways to get "thru" proxies (remember that what's technically possible is not necessarily allowed @work; and the proxy usualy "sees" and logs all transfers.)

if that doesn't work with the installer-gui you can use the alternative install cd, i'm pretty sure it works with that.
good luck!

---

