---
title: "Internet problems"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Taurus548 on 2007-11-13
I have just installed Feisty Fawn and everything seems to go well except no connection to the internet.

I have used a fixed IP addres to fit in with my network 192.168.0.6.

The box can see the network and can browse all the other PC's on the network and I can use the browser  to manage the administartion of the Router, so I do have network connectivity. but the browser cannot resolve the websites IP addressess. I am using exactkly the same DNS servers as all the other PC's on my network.

Any help appreciated.

---

### Post by ddrichardson on 2007-11-13
Is the correct nameserver specified in /etc/network/interfaces?

---

### Post by Threbus5 on 2007-11-26
I had the same problem:

After I added the DNS nameserver to the resolv.conf file and changed the Firefox IPV6 statement in my Feisty installation, the Internet worked.

If you have access to another Internet connection, find the IP address of an Internet site.
Open Firefox and use that IP  address. For example, if you found that site ABC had the IP address of 271.xxx.yyy.zzz then you would enter [http://271.xxx.yyy.zzz](http://271.xxx.yyy.zzz) as the firefox address.

If Firefox then displays that site you have a DNS problem.
If you are unable to obtain a numeric IP address for an Internet site then assume that you have a DNS problem and proceed to correct it.

In order to correct the DNS problem it is necessary to have a line in the resolv.conf file that lists your DNS address.
As listed in the previous post the resolv.conf file is reachable via using a terminal window and the following path: /etc/network/interfaces then look for the resolv.conf file and perform a gedit on it. Engage Gedit by going to the /etc/network/interfaces directory and entering in the terminal window, gedit resolv.conf   . 

Do not worry if visually examining the interfaces directory fails to locate a resolv.conf file, the gedit will either open the one that is there or make a file that you can save as resolv.conf.

In the open gedit file make sure that you have a line that says
nameserver xxx.yyy.zzz.nnn 
where the x's y's z's and n's are replaced with the DNS for your network. Sometimes the DNS for a network is the .1 address associated with the subnet. In this case the line could read:
nameserver  192.168.0.1  
(note that if you are making a brand new resolv.conf file the only text in the file might be the: 
nameserver 192.168.0.1 
that you just typed in.)

After gediting the file save it as resolv.conf
quit gedit and try the Internet again. You may find it necessary to restart the Ubuntu machine.

If the Internet still does not work, open Firefox and type    about:config     in the address box. Scroll down and find the network statement that says something such as IPV6 enabled  true. Double click on that 
line so that it changes to false. Then restart Firefox.


Good Luck

---

