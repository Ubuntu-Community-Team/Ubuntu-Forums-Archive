---
title: "apt-get upgrade starts Tomcat if booting, but not after boot"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by walsh159 on 2011-04-01
Greetings,

I'm running 10.04 on ec2 at Amazon using an AMI (Amazon machine image) based on Canonical's 32 bit 10.04 AMI. I used apt-get to install Tomcat6 when I built the AMI. Before building the AMI, I removed the /etc/rc2.d script link that started Tomcat at boot time, as I need to do some other work before starting Tomcat.

If I call "apt-get upgrade -y" in /etc/rc.local, apt attempts to stop Tomcat and then starts Tomcat, even though I didn't have it running before the call. If I remove the apt-get upgrade call from rc.local and run it manually in a bash shell after boot, apt does not start Tomcat. 

I'd like Tomcat to not be running after the apt-get upgrade call returns. I could stop Tomcat in my script after the upgrade call, but I'd like to understand why Tomcat is started in the first place. I'm concerned that if I solve this by stopping Tomcat, at some point in the future something else in the system will change and some other service will be started up by the apt-get call. Instead of just coding a workaround for this problem, I'd much prefer to understand why apt-get starts Tomcat only when apt-get is invoked from rc.local.

Thanks,
John Walsh

---

