---
title: "I have created Pxe but iso on apache missing"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2009-11-20
I have created TFTP ,DHCP for my network to install Ubuntu via NETBOOT but the image that I have hosted on Apache my Ubuntu installer is not able to find the correct path to it when it asks me to give the location of a mirror on internet after booting from LAN I give it 
```

[http://IP](http://IP) Of Apache server

```and in the next step 
```

/directory where image was copied/

```but here the error is coming since the installer is not able to find the correct server my apacher server ,DHCP and TFTP are all same the service /etc/inint.d/apache2 is running 
so any guesses or links to tutorials etc ,
I read some where we need to host the alternate CD ISOs only since vmlinuz and initrd were available in casper folder in CD and there was no netboot folder in the CD

---

### Post by tapas_mishra on 2009-11-22
Finally solved  [http://ubuntuforums.org/showthread.php?t=1331410](http://ubuntuforums.org/showthread.php?t=1331410)

---

