---
title: "Nagio's installation."
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by sbhayyal on 2012-06-08
**[SIZE=2]Hi,   I want to install Nagio's,in Ubuntu 12.04 LTS,please could you help me  in this regard with step by step procedure!    Thanks, [/SIZE]**

---

### Post by N0oki3 on 2012-06-08
Hello there. I have installed my nagios on CentOS server. So there are quite (well quite small diffrences in commands) I recommend you to read and follow this guide [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

The installation is not hard, but you will have to underastand how and why at creating parameters aka services for your monitoring. Also if you want to monitor other server you will have to install and confgiure nrpe on the server. 

If you are going to be stuck on any step, feel free to ask in this topic.

I also recommend you **not to use sudo apt-get install nagios** in my case. Nagios didn't worked as it should and i had to reinstall it via source

---

### Post by psyllex on 2013-01-01
> **N0oki3 said:**
> Hello there. I have installed my nagios on CentOS server. So there are quite (well quite small diffrences in commands) I recommend you to read and follow this guide [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

The installation is not hard, but you will have to underastand how and why at creating parameters aka services for your monitoring. Also if you want to monitor other server you will have to install and confgiure nrpe on the server. 

If you are going to be stuck on any step, feel free to ask in this topic.

I also recommend you **not to use sudo apt-get install nagios** in my case. Nagios didn't worked as it should and i had to reinstall it via source

I'm having trouble getting Nagios up and running.  So do I install the main Nagios installation on the server I wish to monitor?  Or the desktop that I will be monitoring from. Again do I install NRPE on the monitored server or the desktop?  I've installed it about 4 times now and I'm just about as confused as I was when I started.  So I would really appreciate any assistance.  Thanks.

---

