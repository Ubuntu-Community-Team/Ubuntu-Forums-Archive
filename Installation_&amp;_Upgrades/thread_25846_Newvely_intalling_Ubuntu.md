---
title: "Newvely intalling Ubuntu"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by LusiphurScyla on 2005-04-11
Hello there people!

Im from Buenos Aires Argentina, an this is the second time i tried to install ubuntu.

Actully, the last time i tried i have the same issues than this time...but lets talk about my problems...
The big one? well...im almost a newvie in this linux world...but still i have a lot of skills to under stand anything you purpose.

Well, lets talk about the issues...
1) I dont know why , this time, the resolution is 640x480....last time it was installed perfectly!...i tried to change it, but the preferences resolutions leave me only the 640x480 option. How can i inrease my screen resolution?

2)I have a PCMCIA ethernet card, i tried to install it, but the network configuration tool says that i havent a DHCP server installed...what can i do? i want my machine in a network with another single node, a windows machine, with simple protocols like tcp or ipx.

I accept any hand you can bring me, even if a have to edit some text files by hand....thanks.

---

### Post by heimo on 2005-04-11
Maybe you can get ideas from these threads? Sorry for very quick answer - I get back to this after 8-12 hours, if you haven't solved it already.

[http://www.ubuntuforums.org/showthread.php?t=25414](http://www.ubuntuforums.org/showthread.php?t=25414)
[http://www.ubuntuforums.org/showthread.php?t=25416](http://www.ubuntuforums.org/showthread.php?t=25416)
[http://www.ubuntuforums.org/showthread.php?t=25481](http://www.ubuntuforums.org/showthread.php?t=25481)
[http://www.ubuntuforums.org/showthread.php?t=25402](http://www.ubuntuforums.org/showthread.php?t=25402)

---

### Post by LusiphurScyla on 2005-04-11
I managed to fix the screen resolution problem...
But still i havent network...
If anyone can help me...

Thanks.

---

### Post by heimo on 2005-04-11
EDIT: Check this
[http://www.ubuntuforums.org/showthread.php?t=25557](http://www.ubuntuforums.org/showthread.php?t=25557)

How do you connect these computers to each other? Using crossover ethernet cable, or somekind of hub / switch to connect both computers to? Are these computers also connected to internet? Does the internet service provider have DHCP-server? (that would mean that you don't have to set static ip addresses to connect to internet)

DHCP (Dynamic Host Configuration Protocol) server can assign hosts their ip-addresses, dns-addresses, default gateway ip and stuff like that. If you don't have DHCP or your ISP doesn't use one to configure clients, you need to set networking configuration manually. What does this mean?

If those computers are connected directly to internet, you probably get IP addresses from your service provider. If those computers are not directly connected to internet, you probably should pick ip addresses like 192.168.1.1 and 192.168.1.2 to your both machines, set the subnet mask to 255.255.255.0 and use your gateway (ADSL-modem/switch/router) ip address as a default gateway and put your ISP's DNS server addresses to /etc/resolv.conf

You can check your Windows machines networking config by going to command prompt (Start->Run->cmd [enter]) and typing 'ipconfig /all'.´If that computer has working internet connection, write down dns-server addresses, and default gateway address. Those should be same on both computers. What needs to be different on these computers is IP address. It should however be from same subnet. (basicly, first octets of ip address should be same, for ecample 192.168.1 and then the host part is different for your two different computers 1 and 2. These ip addresses can be used in private networks, but are not routed through internet, so in this case you would need NAT (network address translation) service on your ADSL / Cable modem / router box (the device that is between your computers and Internet).

I'm not on Linux box at the moment, so these instructions may be off. But you can go to terminal window and run /sbin/ifconfig to check your network settings, you need to do that as a root or with sudo. (sudo /sbin/ifconfig) When those settings are correct, you should be able to ping the other host (and vice versa), using ping 192.168.1.2 or what ever the ip address is. Check that the lights in your network adapters and switch is lit - and it should blink when sendind/receiving data.

Then you need to check that DNS (domain name system) is working correctly. That translates host names (like [www.ubuntuforums.org](www.ubuntuforums.org)) to ip addresses. On linux you do 'dig www.ubuntuforums.org' and you should get ip address for that name. Check the same on your Windows machine using 'nslookup www.ubuntuforums.org'. If that's not working, you need to check /etc/resolv.conf there should be lines with 'nameserver' and the ip address of that server. Something like:
```

nameserver  10.0.0.1
nameserver  10.0.0.2

```
but of course with the correct ip addresses. There can also be line with 'domain' or 'search' but that shouldn't matter at this point. 

Oh, your dns can't work if the default gateway is not set. You can probably see that by typing '/sbin/route -n', but you could as well use the networking settings under System menu. When those settings are ok, you should be ready... to start configuring the network shares or whatever that is you want to do.

Tell me about your progress and setup, so I can give more spesific help. Thanks for listening! :)

---

### Post by LusiphurScyla on 2005-04-11
Well this is what i tried...i was like about two hours with this and doesnt seems to work.
Following the steps of the link you posted...this is the information i have recover : 

"Is the interface configured correctly ? (lspci, lsmod, dmesg, ifconfig /etc/network/interfaces)"

I runned ifconfig /etc/network/interfaces and this is the output :
error fetching interface information : Device Not found

The PCMCIA card ligths are on....but it never get flashy, or anything. Even so, the others things are never conecting or anything....it cloud be a interface configuration plroblem? my card its a CNF 401 cnet 100/10 fast ehernet cardbus adapter.

Thank you anyway for your help.

---

### Post by heimo on 2005-04-11
I don't know if this is the problem, but you should probably make sure that you have pcmcia-cs package installed. You can try something like:
```

sudo apt-get install pcmcia-cs
sudo modprobe pcmcia
sudo /etc/init.d/pcmcia start

```

Then you can
```
sudo tail -f /var/log/messages
``` 
while inserting the card to see if there's a message about the card.

---

### Post by LusiphurScyla on 2005-04-11
Does not work...
The card is still unrecognized...
I used the comandas you asked...but nothing happends....the is still the same error. Saying i dont habe the interface...any other ideas?

---

### Post by LusiphurScyla on 2005-04-12
After this :
sudo apt-get install pcmcia-cs
sudo modprobe pcmcia
sudo /etc/init.d/pcmcia start

And everything it shows looks fine.

I run the ifup -a command, and it shots : 
ifup:interface Io already configured
SIOCADDRT: File exists
Failed to bring up eth0

The Ip's i use are this :
Windows XP machine : 192.168.1.1
Linux Ubuntu : 192.168.1.2
The Windows, is conceter to a ADSL router , without a physical IP. I mean, the internet ip is auto managed.
The subnet mask for each system is 255.255.255.0
The ubuntu linux machine is conected to the windows machine by a UTP-5 cord. This cord worked before, and the conection is clearly reached, beacuse the ligths of the pcmcia card goes off when i unplug the cord.
Any suggestions?

---

