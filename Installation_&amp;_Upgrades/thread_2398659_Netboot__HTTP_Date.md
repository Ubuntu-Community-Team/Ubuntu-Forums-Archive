---
title: "Netboot / HTTP/ Date"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by brownjl on 2018-08-15
Hello,

I am trying to install ubuntu via PXE using a preseed and kickstart file pulling these files down via HTTPS from a remote server. 

I have this mostly working. However is there is a problem with the systems date/time, the installation process fails as it cannot verify the SSL connection. All my machines are headless or remote so changing the date time can be painful. 

Is it possible to configure the system to changed the date/time using an NTP source prior to downloading the Preseed/Kickstart file that are provided as kernel parameters? I see the installation process first configures its network interface prior to downloading the two files, this is where I would need to change the date/time. 

Thanks

James

---

