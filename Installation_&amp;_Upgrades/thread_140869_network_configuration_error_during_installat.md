---
title: "network configuration error during installat"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by jeisma on 2006-03-07
hello!

im trying (for the first time) to install 5.10 on my pc.

however, during install i get this message:

the network autoconfiguration was successful. however, no default route was set: the system does not know how to communicate with hosts on the internet. this will make it impossible to continue with the installation unless you have the first official Ubuntu CD-ROM, a 'netinst' CD-ROM, or packages available on the local network.

im stumped. what am i suppose to do on this message? why is it saying "impossible to continue.."? what kind of network information does it need? 

the install does allow me to continue with the installation, but this message hunts me.

tips anyone?

id like to know linux through ubuntu..


thank you!

---

### Post by jamesr on 2006-03-07
> the network autoconfiguration was successful. however, no default route was set: the system does not know how to communicate with hosts on the internet. this will make it impossible to continue with the installation unless you have the first official Ubuntu CD-ROM, a 'netinst' CD-ROM, or packages available on the local network.

It will continue with installation because you have the 1st Ubuntu CD-Rom. The error states "or" in the latter part if the sentence.. But to access the internet and add software you will need that setting up.

Post the outputs of 
```
sudo ifconfig -
cat /etc/resolv.conf
```

---

### Post by jeisma on 2006-03-07
hi!

thanks for the assurance.

will proceed with the installation then. 


thanks!

---

