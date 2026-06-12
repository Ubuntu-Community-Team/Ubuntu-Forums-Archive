---
title: "how to redirect inter netnetwork traffic through server"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by lobebufe on 2010-09-30
Greeting everyone,

I tried to setup a home server that will redirect the internet traffic through the server before it reach the client. Because i don't want to install anti virus on every machine, it will slow them down a lot. There are some anti virus for ubuntu. Most of my home machines are running windows, which is a pain with virus. Could some one give me head up of how should I do it. Many thanks in advance.

p/s: I'm running 1 ubuntu server 10.04 and the rest are windows 7 machines.

---

### Post by lobebufe on 2010-09-30
this software is similar to what I think is the best to describe what i would want

[http://www.kaspersky.co.uk/work_space_security](http://www.kaspersky.co.uk/work_space_security)

but is there any alternative products that is open source and free.?

---

### Post by sikander3786 on 2010-10-01
I run Squid to serve the purpose. See here.

[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

You can skip dansguardian and wpad setup if you don't want them.

The guide is intended for 9.04 but I'm pretty sure it will work with any other versions of Ubuntu as well.

---

### Post by lobebufe on 2010-10-01
wow.. many thanks, i will give it a shot and get back to you soon. again thank you so much...

---

### Post by lisati on 2010-10-01
When you are ready to add email capabilities, you might want to look [here]("https://help.ubuntu.com/community/PostfixAmavisNew") as well for dealing with spam and malware.

---

### Post by lobebufe on 2010-10-02
hi there,

thank you for a head up but this is somehow a bit hard for newbie like me:(

i got stuck at a few problem, i have done some research but without luck. Hope you can help.
I got stuck at this path, as it is somehow different. I think it is because of the new version of lighttpd

#mimetype.assign = ( ".dat" => "application/x-ns-proxy-autoconfig" 

When i do sudo /etc/init.d/lighttpd restart . It showed up with an error, point to the line i stated above.

Secondly, i tried to add this 

#custom-proxy-server "http://x.x.x.x/wpad.dat"

into "/etc/dhcp3/dhcpd.conf"

i got an error saying that i can't understand 

#option custom-proxy-server "http://x.x.x.x/wpad.dat";

And there are some people having the same problem with me, one of the guys said that he found a solution for this problem. But i don't really understand what he meant by it. he said:

"Hello People,

 I had problem setting the custom-proxy-server in dhcp3-server in a Lenny Debian distribution, I had a error.

But I solve the problem with dnsmasq:

 dhcp-option=252,[http://192.168.1.1/local/wpad.dat](http://192.168.1.1/local/wpad.dat)

 Thanks for the HOWTO...

Charlie "

Can someone please explain how he did it. Many thanks


Sorry for my poor explanation, it is hard for me to explain everything, i have tried and tried but without luck. Thank you for your understanding.

---

### Post by lobebufe on 2010-10-02
I think i found a solution here but I don't really understand :((

[http://users.telenet.be/mydotcom/library/network/pac.htm](http://users.telenet.be/mydotcom/library/network/pac.htm)

---

### Post by lobebufe on 2010-10-02
i have success setup everything, but I don't know if it is working or not. :( could someone please give me some advise on this.

---

### Post by sikander3786 on 2010-10-03
> i have success setup everything,

Success sounds good :-) But what have you installed? What is your current setup, and what do you want to test. I just couldn't understand that you installed Squid or not?

---

### Post by lobebufe on 2010-10-06
Hi sorry for the late reply,

I have installed Squid, Dansguardian, ClamAV and DHCP. I redirect the network traffic through server by squid, and then scan the content by Dansguardian and ClamAV. I can see that Dansguardian is working because when I tried to connect to a block content such as porn. I showed up in the client browser and said the page has been blocked. 

But I don't really know if ClamAV is working or not, because when i tried to test a virus from 

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

the eicar.com test virus was blocked out but the others are not (Lol). Maybe it is due to ClamAV is not quite a good anti virus after all, or maybe it is really good that it was being able to detect fake and real virus. But either way, it was quite a challenging experiences.

---

