---
title: "Internet Connection fails"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by squirebug on 2005-04-15
Dear All.

I recently changed my linux distribution from Fedora Core 1 to Ubuntu 4.10.

Everything seems to have gone well except that after switching to Ubuntu I cannot connect to the internet.  I connect through a Belkin router LAN as before.  There are two other computers on the LAN that have no problems seeing the internet.  

I can ping the router and  all other computers on the LAN and see the other computers in Nautilus, so it appears that the networking setup with DHCP went well.

However, I am unable to access any internet sites or ping any DNS sites outside the LAN with the Ubuntu computer.  

The network settings on the Ubuntu computer appear to be the same as on the Fedora Core 1 installation.

Any advice on how to get access to the internet will be greatly appreciated.

Thank you for your help.    ](*,)

---

### Post by ijsje on 2005-04-16
[QUOTE=squirebug]Dear All.
I recently changed my linux distribution from Fedora Core 1 to Ubuntu 4.10.

Everything seems to have gone well except that after switching to Ubuntu I cannot connect to the internet. I connect through a Belkin router LAN as before. 
[/QUOTE]
 Is it a wireless router?
 
> There are two other computers on the LAN that have no problems seeing the internet.I can ping the router and all other computers on the LAN and see the other computers in Nautilus, so it appears that the networking setup with DHCP went well.

That's a good start at least.

> 
However, I am unable to access any internet sites or ping any DNS sites outside the LAN with the Ubuntu computer.  

You say you don't get a ping response from a DNS server, so the problem shouldn't be with the dns servers, it seems nothing gets out of the lan.

> 
The network settings on the Ubuntu computer appear to be the same as on the Fedora Core 1 installation.

Any advice on how to get access to the internet will be greatly appreciated.

Thank you for your help.    ](*,)
You can access the network but can't ping anything outside of the network, perhaps you can find a clue at the web interface of the router. Also, you may want to double check the gateway ip.

---

### Post by usa on 2005-04-18
I have the same problem as you when i first installed ubuntu and tried to use the internet, and what i did is set DNS server.

1. Go to menu-> computer -> system configuration -> networking
2. Click Tab DNS and add DNS server click ok and try to use the internet again.

If you don't know what is the DNS ip of your network, you can go to your friend computer which has window os. 
Use the cmd prompt to run commmand line by going to 
the menu -> program -> run -> then type cmd.  
A window will appear, then type > ipconfig /all
it will show all network configuration, then copy DNS ip to set DNS in unbutu.

Hopefully, it will be useful for you.  :)

---

