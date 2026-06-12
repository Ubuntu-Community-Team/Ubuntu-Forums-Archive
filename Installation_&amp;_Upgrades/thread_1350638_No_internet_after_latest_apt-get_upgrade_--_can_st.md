---
title: "No internet after latest apt-get upgrade -- can still ping router.."
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by jeepzj on 2009-12-09
Hi folks,

I am running Ubuntu 9.04 on an AMD system.  Have had no problems running it for a couple of months now until 2 days ago.  Since I have an ATI x800 vid card there are some issues where I had to downgrade my X and as such, some of the libraries are locked.  The only way I can upgrade my system is to do the "apt-get upgrade" which up to this point has worked like a charm.  About 2 days ago I did my last upgrade and finally re-booted the pc last night, but when it came back up.. guess what.. no internet.. :( ..

I checked my connections, all is good, the internet works great from my other PC, router is good.  I can ping the router (and can load up the router GUI in firefox) and other PC on the net, but can't get out to surf or get e-mail.  So this leads me to think that something with the DNS must be borked. I checked the network status icon on top of the status bar, and it says connected, but I can't get out..

Any ideas?  It's very boring when you have no internet connection.. ;(

Thanks everyone
- Hubert

---

### Post by darkod on 2009-12-09
If you right click the network status icon and select Connection Information, does it show ip, network mask, dns as expected?

---

### Post by jeepzj on 2009-12-09
Yes it does.. all of the details are as expected.. this is from memory, but I think it listed the following :

ip is 192.168.1.11, outbound 192.168.1.255, gateway 255.255.255.0, router 192.168.1.1

- Hubert

---

### Post by darkod on 2009-12-09
You can also try disabling and then enabling the connection. Sometimes it helps to "wake up". And check the connection information, it should also list dns, and you're suspecting dns problem.

---

### Post by jeepzj on 2009-12-09
Tried that yesterday as well.. many times.. I have 2 ports on my MB, eth0 and eth1 and I tried both of them with no luck.  They both get recognized, and it says connected.. but it won't let me go anywhere.. so basically , same result on both network jacks.

- Hubert

---

### Post by jeepzj on 2009-12-09
Any ideas?? still have this issue when I got home...

Thanks

---

### Post by jeepzj on 2009-12-09
So no ideas of what I can try??  this no internet is not that much fun.. ;)
 
Anyways, I've tried pinging ftp.dell.com with no luck, but if I try to ping 143.166.170.10 it pings it with no problem.. this leads me to think that I have something that deals with the DNS system broken..  Any ideas here folks?? How can I check if ubuntu is handling the DNS correctly?

PLEASE !!!

---

### Post by phillw on 2009-12-10
Hi, not seen this one, but having a trawl around .. a couple of suggestions...

>                                   **Re: Network connection but no Internet with 9.04**             
                                                                It finally started working, but mostly by accident. I accidentally created a second instance of my home network. When I saw there were two I deleted one -- it happened to be the one that was connected to my home network. When I deleted it, it disconnected from the network. Then a window popped up asking me if I wanted to "allow the keyring to access the password..." or something like that, for the other instance of my network. I said yes and everything started working. Apparently everything was configured correctly in the first place using DHCP, but Ubuntu needed a kick-start to initialize it.
                                                                                               Also, this thread may help you  [http://ubuntuforums.org/showthread.php?p=7234361#post7234361](http://ubuntuforums.org/showthread.php?p=7234361#post7234361)

It's most odd to loose a hard wired connection, the 1st thread was pointing to the mask address wanted by the the router/modem NOT being the usual 255.255.255.0 but 255.255.252.0 -- Which is certainly non-standard !!

Hope the above helps,

regards,

Phill.

---

### Post by jeepzj on 2009-12-10
well.. I spent a few hours last nigh looking for similar situations, not much I could find.  But what kept me confused is that I can ping all of the numerical values and not the alpha addresses.. as such I started investigating the DNS system, which led me to investigating the bind9 libraries to see if there was something there broken.. this led me to a file called /etc/resolv.conf and this is where I think my problem is..

My current file has the following :

nameserver 127.0.0.1

when I changed that to :
nameserver 192.168.1.1

everything came back to life.. untill I rebooted or reset my connection in which case the 127.0.0.1 comes back.  I have to investigate this more to determine how to make this a permenant change.. so if anyone has any ideas how to make this happpen.. I'm all ears !!

Thanks for taking the time reading this..

- Hubert

---

### Post by phillw on 2009-12-10
Hi,

Well, setting the dns is covered here --> [http://www.cyberciti.biz/faq/ubuntu-linux-configure-dns-nameserver-ip-address/](http://www.cyberciti.biz/faq/ubuntu-linux-configure-dns-nameserver-ip-address/)

A more in depth look is over this way -->  [http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

Regards,

Phill.

---

