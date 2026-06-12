---
title: "Creating a DNS server for my website."
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by ajarduini on 2010-05-24
Greetings everyone,

I am trying to build a DNS server that can serve as a Name Server for my website.  I have a third level domain and currently have no control over the dns with it's current name servers.  I would like to build a dns name server using Ubuntu and the default installed dns server bind9.  I have tried following tutorials online and they all offer similar steps with slight differences.  

Most of what I am reading makes me believe that I am creating a local DNS server when in reality I want a dns server accessible from the outside.

I would appreciate any help you may be able to provide me with.

I thank you in advance for any help you can provide me with.

---

### Post by ajarduini on 2010-05-25
I just wanted to give everyone a status update.  I was able to ALMOST achieve what I wanted to by following a video tutorial on YouTube ([http://www.youtube.com/watch?v=GMWSH_iwhh4](http://www.youtube.com/watch?v=GMWSH_iwhh4))

I still have the following situation/issue:
*(Please note that I changed the domain url and ip addresses.)*

Web Server:  22.12.32.272
DNS Server:  22.12.32.282
Domain:  myurl.com
Nameserver: ns1.myurl.com pointing to 22.12.32.282 using GoDaddy

I can ping [www.myurl.com](www.myurl.com) and it replies 22.12.32.272 which to me is working correctly.

When I ping myurl.com it replies 22.12.32.282 which is the DNS server.  I would like it to resolve to 22.12.32.272.

I am hoping that this will be a small issue to someone that really knows what they are doing.

My files are as follows:



**named.conf.local**

zone "myurl.com" {
type master;
file "/etc/bind/myurl.zone";
};

zone "32.12.22.in-addr.arpa" {
type master;
file "/etc/bind/myurl.local";
};






**/etc/resolv.conf**

search myurl.com
nameserver 22.12.32.282





**myurl.zone**

$TTL 604800
@ IN A SOA myurl.com. admin.myurl.com. (
    2    ; Serial
    604800    ; Refresh
    86400    ; Retry
    2419200    ; Expire
    604800    )    ;Negative Cache TTL
;
@     IN    NS    myurl.com.
@    IN    A    22.12.32.272
myurl.com    IN    A    22.12.32.272
www    IN    A    22.12.32.272
sheets    IN    A    22.12.31.233




**myurl.local**

$TTL 604800
@ IN A SOA myurl.com. admin.myurl.com. (
    2    ; Serial
    604800    ; Refresh
    86400    ; Retry
    2419200    ; Expire
    604800    )    ;Negative Cache TTL
;
@     IN    NS    myurl.com.
@    IN    PTR    22.12.32.272
myurl.com    IN    A    22.12.32.272
;www    IN    A    22.12.32.272

---

### Post by darkod on 2010-05-25
If I understand correctly, you said you don't have control over the DNS records of the domain registrar.
But you must have this, because that is the point where DNS servers need to be changed. Even if you make your own setup with DNS server, the registrar is the one holding the domain (in your name), so it is their DNS that matters.

Also, if you manage to get control over the registrar settings, you can also try using a service like [http://www.dnsexit.com/](http://www.dnsexit.com/) or similar, and in that case you don't have to bother with creating a DNS server. Just point it to the web server.

I don't know the whole process 100% but it can't work like you are trying to do without changing and controlling at least some settings at the registrar. Otherwise anyone can just make their own DNS server and point microsoft.com to a wrong web server.

---

### Post by ajarduini on 2010-05-25
thank you for your reply.  I have the ability to change the name servers with the registrar.  For example, the nameservers are pointed to NS1.MYURL.COM and NS2.MYURL.COM which both point to the IP address of my DNS server.  I as able to achieve this using a Microsoft server; but I would rather use ubuntu.

Thank you for any help you may be able to provide me with.

---

### Post by darkod on 2010-05-25
OK. In that case, why don't you just use a service like dnsexit I mentioned? And there are probably others around.
If I remember correctly, when I spent some time playing with web servers and dns myself, creating an account at dnsexit is free and if you don't need them to register a domain for you, you can easily use them to point your domain to the web server IP.
In that case you put the dnsexit servers in the registrar, and that's it.

Or you want to create your own independent dns server?

---

### Post by darkod on 2010-05-25
A quick search returned these:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

They are rather old, from 2006 and 2007, but the basic is the same and maybe it will help you out. There might be even newer tutorials.

---

### Post by ajarduini on 2010-05-25
I will look into this; however, here is where my trouble comes in.   My actual website is a third level domain.  Meaning our actual webaddress would be something like:  myurl.theirurl.allurls.us.... sadly most websites like the one you mentioned do not support these types of domains.

---

### Post by ajarduini on 2010-05-25
Thank you, but I have been all over these links with no luck yet.  Following those links I couldn't even get the url to resolve.  I followed a youtube video and I can atleast get the main part to resolve.



> **darkod said:**
> A quick search returned these:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

They are rather old, from 2006 and 2007, but the basic is the same and maybe it will help you out. There might be even newer tutorials.

---

