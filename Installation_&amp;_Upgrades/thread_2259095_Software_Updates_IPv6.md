---
title: "Software Updates IPv6"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by Beernut on 2015-01-01
Since installing 14.04 software updates fail unless I disable IPv6.  Is there a problem with the Ubuntu servers?

---

### Post by MAFoElffen on 2015-01-01
IPv4 and IPv6 are in layer 3 of the 7 layer OSI model. The SIP (Source IP) only matters inside the local network and at your gateway. Ubuntu's Servers (the repo's) do not care about that layer.

I am not having any problem using IPv6... I know that IPv6 has to be recognized by your network equipment to be able to use it. Are you using IPv6 local? Are you using DHCP for your IPv6 or Static or static? Is there any way you are having a local conflict of addressing? Is your local subneted? I also know from my CISCO classes that routers don't have IPv6 services turned on by default. Have you turned those services on? (config)

You say you have no problem if you use IPv4. Could you describe your topology?

Please post your /etc/network/interfaces and the result of 
```

ifconfig -a

```

---

### Post by Beernut on 2015-01-02
It's not my network IPv6 worked perfectly until I ran the upgrade to 14.04.  Unity didn't load after the upgrade and was trying to fix things with apt at the command line and couldn't do an update.  Ended up wiping everything out and just installed 14.04 fresh.  The only way updates run is if I disable IPv6 on my interface.  Here is what happens when running apt it gets stuck at us.archive.ubuntu.com

```
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
57% [Connecting to us.archive.ubuntu.com (2001:67c:1562::17)] [Connecting to se
```

---

### Post by MAFoElffen on 2015-01-02
My best guess suggestion of that then would be to report it as a bug to launchpad. Seems to be a deeper problem. They will tell what they need to sort it out.

---

