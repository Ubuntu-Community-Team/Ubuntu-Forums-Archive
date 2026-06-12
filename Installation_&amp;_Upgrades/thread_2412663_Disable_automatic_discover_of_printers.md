---
title: "Disable automatic discover of printers"
date: 2019-02-15
forum: Installation &amp; Upgrades
---

### Post by fmurillo on 2019-02-15
Hello,
I have a problem. I need to disable the automatic discover function of network printers.
I have a network with PCs (Ubuntu 18 and Ubuntu 16) and Printers (different brands). All of them are connected to the network.
Some PCs need only one printer. But, some of the printers are added automatically (according to some forums, CUPS service has this function)
 So I tried to  remove the printers, but after a  few seconds, printers are added again.
I revised some forums related, but solutions proposed do not work for me. (I tried to change cups-browse.conf file,  BrowseRemoteProtocols parameter and restart the service. It did not work)
Please help me.

---

### Post by ubfan1 on 2019-02-15
Did some of the solutions suggest removing the libnss-mdns package?  That should remove the  mdsn part of the hosts line in the ./etc/nsswitch.conf file.  Don't know if getting rid of multi-cast dns would help, but it might.

---

### Post by kurt18947 on 2019-02-15
Here's what I saved so I guess it worked:tongue:.

Edit /etc/cups/cups-browsed-conf so it shows 

```
BrowseRemoteProtocols none
```

and save. Restart CUPS with the following command:

```
service cups restart
```

---

### Post by fmurillo on 2019-02-18
Thanks for help. 
I tried to apply kurt18947's solution, but it did not work. 
I solved the problem with another way. I entered into the printer's configuration (ubfan1's answer gave me a clue). I disabled MDNS or Multicast and DDNS option. After that Ubuntu did not add the printer again.:D

---

