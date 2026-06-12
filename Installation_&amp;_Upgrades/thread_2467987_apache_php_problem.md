---
title: "apache php problem"
date: 2021-10-14
forum: Installation &amp; Upgrades
---

### Post by joe672 on 2021-10-14
ive installed ubuntu 20.04. apache is installed, it displays the test html page once setup on the virtual host and also the test php pagr but it wont load any of my sites in var/www/html. some are php and some html. any helps appreciated

---

### Post by joe672 on 2021-10-15
the test html page loaded when i added the ip to server name in the virtual host. but when i try that with any of my sites, nothing works , same with the domain names

---

### Post by yancek on 2021-10-15
You should have an index.html page in /var/www/html.  Your statement that nothing works isn't very helpful.  What exactly does happen when you open your browser and in the address bar you type:

> [http://loclahost/index.html](http://loclahost/index.html)

---

### Post by joe672 on 2021-10-15
at the moment when i use the ip i get same as when i use the domain

> **This site can&#8217;t be reached**

[COLOR=#5F6368][FONT=&amp]Check if there is a typo in [www..]("http://www..")[/FONT][/COLOR]
[COLOR=#5F6368][FONT=&amp]
[LIST]
[*]If spelling is correct, try running windows network Diagnostics.
[/LIST]




[/FONT][/COLOR]
[COLOR=var(--error-code-color)][FONT=&amp]DNS_PROBE_FINISHED_NXDOMAIN[/FONT][/COLOR]

when i setup a test config in sites available/enabled and var/www/html/testsite.html and using the server name as the ip, the test page loads. when i use it for any of my other sites in var/www/html/sitename/ nothing loads . my sites used to be in home/site/public_html before but i read 20.04 must use var/www/html/site/public_html

---

### Post by joe672 on 2021-10-15
a wild guess: if ive setup custom name servers for my domain with my old host to point to new, do i need to edit  resolv.conf  ?

---

### Post by joe672 on 2021-10-15
[COLOR=#404040][FONT=AntennaCond-Light]root@localhost:~# host mysite.com[/FONT][/COLOR]
[COLOR=#404040][FONT=AntennaCond-Light]Host mysite.com not found: 2(SERVFAIL)[/FONT][/COLOR]
[COLOR=#404040][FONT=AntennaCond-Light]root@localhost:~# host myothersite.co.uk[/FONT][/COLOR]
[COLOR=#404040][FONT=AntennaCond-Light]myothersite[/FONT][/COLOR][COLOR=#404040][FONT=AntennaCond-Light].co.uk has address 77............

the difference between the two is how the name servers are setup, one has custom name servers setup on old host still pointing to ip,  the .co.uk domain was moved to a new host and uses A record with domain and the hosts name servers. It still doesnt display when url is used[/FONT][/COLOR]

---

### Post by SeijiSensei on 2021-10-15
Apache determines which virtual host to use by matching the requested name to the value of the ServerName field in every <VirtualHost></VirtualHost> stanza.  If it finds no matches, it uses the default page.

You can use a ServerAlias declaration in the VirtualHost definition specifying other names to which that definition applies.
```
<VirtualHost>
ServerName     [www.example.com](www.example.com)
ServerAlias    example.com
[stuff]
</VirtualHost>
```

---

### Post by joe672 on 2021-10-15
here is one of my sites-enabled conf  


```
<VirtualHost 77...:80>    
    ServerAdmin joe@.com
    ServerName www..com
    ServerAlias www..com
    DocumentRoot /var/www/html/.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


thanks


```

---

### Post by joe672 on 2021-10-15
Time for a virtual fire for this setup lol

cant get a connection between the domains and the server no matter what

---

### Post by CharlesA on 2021-10-15
Have you got DNS updated with the correct IP for the domain name you are trying to hit?

If you are trying to connect to [www.example.com](www.example.com) and there is no DNS entry for it, the traffic will go nowhere - so it won't hit Apache at all.

You can verify this by either ping or using dig.

```
ping www.example.com
```

```
dig www.example.com
```

---

### Post by joe672 on 2021-10-15
ive not long tried changing the domains name servers a A record. do i need to update dns on the vps side to? didnt need to on 12.04

> 

--- [www.c.com](www.c.com) ping statistics ---
98 packets transmitted, 98 received, 0% packet loss, time 99314ms
rtt min/avg/max/mdev = 0.036/0.045/0.055/0.003 ms
root@localhost:~# dig [www.c.com](www.c.com)




> ; <<>> DiG 9.16.1-Ubuntu <<>> [www.c.com;;](www.c.com;;) global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54542
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;[www.c.com](www.c.com).                IN      A


;; ANSWER SECTION:
[www.celticalliance.com](www.celticalliance.com). 0       IN      A       77...........(ip removed)


;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Fri Oct 15 23:09:01 UTC 2021
;; MSG SIZE  rcvd: 67




---

### Post by CharlesA on 2021-10-15
As long as the IP matches, you should be fine.

You can try troubleshooting it with curl:

```
 curl http://example.com
```

---

### Post by joe672 on 2021-10-15
i didnt know about curl, every days a school day

> curl: (6) Could not resolve host: c.com



---

### Post by CharlesA on 2021-10-15
Try it with the www and see if it gets a response.

---

### Post by joe672 on 2021-10-15
it doesnt return anything, another one does



301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.e.co.uk//

i had to remove some of the code as the forum wouldnt let me post

---

### Post by CharlesA on 2021-10-15
That looks norm if you are doing a redirect.. are you doing a redirect from one site to another?

---

### Post by joe672 on 2021-10-15
there is a rewrite in that config

>  

   RewriteEngine on 
   RewriteCond %{HTTP_HOST} !^www\.e\.co.uk$ [NC]
    RewriteRule ^(.*)$ http://www.e.co.uk/$1 [R=301,L

thats the only site out 4 thats returning anything at the moment, no pages are loading. thanks for the help

---

### Post by CharlesA on 2021-10-15
At least one is the sites is working. If the other sites are the same except the document root and server name are different, they should be working too.

You could check your apache logs. They should be in /var/log/apache2/

---

### Post by joe672 on 2021-10-15
none of the sites load, ill have to give the dns more time and hope its that. i have some php errors on the log, thats it. the forum needs to be updated after the php upgrade to 7 but am not going to touch it untill i start to see something loading. its a strange one.

---

### Post by CharlesA on 2021-10-15
If you want to bypass DNS for the time being, you can add an entry to your /etc/hosts file and see if the site loads or not.

---

### Post by joe672 on 2021-10-16
[COLOR=#141414][FONT=&quot]etc/hosts[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]127.0.0.1       localhost.localdomain localhost[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]127.0.1.1       localhost[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]77.........(removed)  [www.site1.com]("http://www.site1.com/") [www.site2.com]("http://www.site2.com/") [www.site3.co.uk]("http://www.site3.co.uk/") [www.site4.co.uk]("http://www.site3.co.uk/") [www.site5.co.uk]("http://www.site4.co.uk/")[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# The following lines are desirable for IPv6 capable hosts[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]::1     localhost ip6-localhost ip6-loopback[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]ff02::1 ip6-allnodes[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]ff02::2 ip6-allrouters[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]etc/resolv.conf[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# 127.0.0.53 is the systemd-resolved stub resolver.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# run "systemd-resolve --status" to see details about the actual nameservers.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]nameserver 127.0.0.53[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]options edns0 trust-ad


root@localhost:~# systemd-resolve --status
Global
LLMNR setting: no
MulticastDNS setting: no
DNSOverTLS setting: no
DNSSEC setting: no
DNSSEC supported: no
Current DNS Server: 212.227.123.16
DNS Servers: 212.227.123.16
212.227.123.17
DNSSEC NTA: 10.in-addr.arpa
16.172.in-addr.arpa
168.192.in-addr.arpa
17.172.in-addr.arpa
18.172.in-addr.arpa
19.172.in-addr.arpa
20.172.in-addr.arpa
21.172.in-addr.arpa
22.172.in-addr.arpa
23.172.in-addr.arpa
24.172.in-addr.arpa
25.172.in-addr.arpa
26.172.in-addr.arpa
27.172.in-addr.arpa
lines 1-23[/FONT][/COLOR]

---

### Post by CharlesA on 2021-10-16
That should work - you can try running ping or curl and see if you get a response or not.

You didn't mention which forum software you are running, so that might be helpful.

---

### Post by joe672 on 2021-10-17
looks to be a problem with name servers, A record edit on one got it working, ill give the others more time and hopefully they work. should do , setup same as the one working. thanks for your help mate, appreciated

---

