---
title: "newbie have a few probs inet"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by minimole on 2005-02-15
hy i am new to ubuntu  but i have used various distributions in the past mainly redhat 7.3 but i am by no means a linux expert. i have a few problems with a new install and i have never had it with linux before. 

when i check for my network settings it says DHCP is fine i have an ip and the correct subnet and these are the settings i have always used, but when i go to get to a web site it just never loads it just endlessly says resolving google.com or any other web page  I have access to all other network resources such as shares and everything the internet is the only thing that don't work and it is all on the same router using the same ip and subnet


any help would be greatly appreciated.

---

### Post by benjamin on 2005-02-15
Can you ping [www.google.com](www.google.com) ?

---

### Post by minimole on 2005-02-15
No it is crazy i can get on the net at all but my home network is fine. double checked the network settings they are correct gonna have another look later.

---

### Post by CyrilleMortreux on 2005-02-15
[QUOTE=minimole]No it is crazy i can get on the net at all but my home network is fine. double checked the network settings they are correct gonna have another look later.[/QUOTE]

Maybe your DCHP server does not give the right information about the DNS servers. 

So you have to edit by hand /etc/resolv.conf to write them there, that way

nameserver xxx.xxx.xxx.xx
nameserver yyy.yyy.yyy.yyy

And try again

---

### Post by minimole on 2005-02-15
yeah i am gonna give that a try but my DHCP server has never given the wrong infomation out before and i have about 6 machine running off of it and two of them are linux machine  :?  pain in the ass TBH other than this problem i kinda of like this distro looks clean runs smooth etc. i mean i am no newbie to networking just linux so i will have a look at the settings and get back to you

---

### Post by CyrilleMortreux on 2005-02-15
[QUOTE=minimole]yeah i am gonna give that a try but my DHCP server has never given the wrong infomation out before and i have about 6 machine running off of it and two of them are linux machine  :?  pain in the ass TBH other than this problem i kinda of like this distro looks clean runs smooth etc. i mean i am no newbie to networking just linux so i will have a look at the settings and get back to you[/QUOTE]

Sure I understand. 
I think that Ubuntu starts something to "rm" resolv.conf before starting networking at boot time to be sure that there is no fasle value in. 

Maybe that way to search.

---

### Post by minimole on 2005-02-17
ARGH. I got the inet working sort of changed the DNS settings went to google.com and it worked i thought woooo it is working then i tried other websites and it don't work but i can search anything in google but cant access anything after that. it is insane

---

### Post by CyrilleMortreux on 2005-02-17
[QUOTE=minimole]ARGH. I got the inet working sort of changed the DNS settings went to google.com and it worked i thought woooo it is working then i tried other websites and it don't work but i can search anything in google but cant access anything after that. it is insane[/QUOTE]

Well. 

Are you behong a gateway, proxy, squid ???

If the network works once, it should work everytime. But maybe you are using a proxy that doesn't gave you the right answer to your DNS requests. 
Or with a very strange caching trouble. 

Ubuntu starts 0dns-down to get sure /etc/resolv.conf is OK at boot time, are you sure to have this running ?

---

