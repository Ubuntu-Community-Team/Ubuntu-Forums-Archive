---
title: "how to install squid 3.0  on ubuntu 12.04 desktop"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by sdcisa on 2012-07-05
Hi ;
 
i have installed ubuntu 12.04 desktop and i am planning to install squid 3.0 on the same desktop os. 
Unfortunatly the sudo apt-get install squid is throughing out errors file fetching the repositories. 
 
PS: there is no issue with the internet.
 
Please can someone guide me in the right path to successfully install a squid proxy in transparent mode.

---

### Post by dino99 on 2012-07-05
it might be a good idea to post these errors ;)

[https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)

[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=de&tl=en&u=http://wiki.ubuntuusers.de/Squid](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=de&tl=en&u=http://wiki.ubuntuusers.de/Squid)

---

### Post by sdcisa on 2012-07-05
thanks i will provide u the output.

---

### Post by sdcisa on 2012-07-06
root@sam-desktop:~# service squid3 stop
stop: Unknown instance: 
 i have come across the problem of installing the squid3 proxy. but i am unable to stop the squid3 instance.

can  anyone help me out?

---

### Post by SeijiSensei on 2012-07-06
Try "sudo killall squid3".

---

### Post by sdcisa on 2012-07-06
> **SeijiSensei said:**
> Try "sudo killall squid3".
Hi;

i am able to start the squid service but i am not able to browse the websites as its saying 
The proxy server is refusing connections
      
      
      
      
      
        
        
          Firefox is configured to use a proxy server that is refusing connections.
        

        
        

  Check the proxy settings to make sure that they are correct.
  Contact your network administrator to make sure the proxy server is
    working.

---

### Post by sdcisa on 2012-07-06
if possible can you let me know the steps to diagnise... i am checking the net connection from my proxy server and i am not able to get the internet on the same machine.....

---

### Post by SeijiSensei on 2012-07-06
Are you installing squid to work as a proxy on your laptop, or to provide a proxy for others on a network?

If it's on your own machine, can you browse the Web with the proxy disabled in Firefox but not when it's enabled?  When you have it enabled, are you using 127.0.0.1 and 3128 as the proxy settings (or "localhost" instead of 127.0.0.1)?

If it's just for your own machine, I'm not sure I see the point.  Your browser already caches objects it downloads, so squid is rather redundant.  I run squid on gateway routers that connect whole offices to the Internet.  I don't use it on ordinary client machines.

---

### Post by sdcisa on 2012-07-06
> **SeijiSensei said:**
> Are you installing squid to work as a proxy on your laptop, or to provide a proxy for others on a network?

If it's on your own machine, can you browse the Web with the proxy disabled in Firefox but not when it's enabled?  When you have it enabled, are you using 127.0.0.1 and 3128 as the proxy settings (or "localhost" instead of 127.0.0.1)?

If it's just for your own machine, I'm not sure I see the point.  Your browser already caches objects it downloads, so squid is rather redundant.  I run squid on gateway routers that connect whole offices to the Internet.  I don't use it on ordinary client machines.

Hi;

My Proxy Server has two interfaces 1 is eth0 which is the interface for the internal network. and another interface is a ppp0 interface [usb dongle]. 

for testing purpose i have login into my proxy machine & set the browser proxy setting to point to my ip of the proxy server:3128. and my net is refused from the proxy machine itself.

---

### Post by SeijiSensei on 2012-07-06
Well either you should be using the eth0 interface.  In squid.conf, what do you have for http_port?  Just "http_port 3128" or did you bind it to a specific IP?  I'd suggest not doing that.

Did you create one or more entries with "acl localnet src" that include the subnets from which you are connecting?  E.g.,

```
acl localnet src 192.168.1.0/24
```

followed later by

```
http_access allow localnet
```

Did you read the documentation at [http://www.squid-cache.org/Doc/](http://www.squid-cache.org/Doc/)?

Squid isn't the hardest thing to configure, but you do have to make the appropriate changes to squid.conf to permit browsing through the proxy.

---

### Post by sdcisa on 2012-07-06
> **SeijiSensei said:**
> Well either you should be using the eth0 interface.  In squid.conf, what do you have for http_port?  Just "http_port 3128" or did you bind it to a specific IP?  I'd suggest not doing that.

Did you create one or more entries with "acl localnet src" that include the subnets from which you are connecting?  E.g.,

```
acl localnet src 192.168.1.0/24
```

followed later by

```
http_access allow localnet
```

Did you read the documentation at [http://www.squid-cache.org/Doc/](http://www.squid-cache.org/Doc/)?

Squid isn't the hardest thing to configure, but you do have to make the appropriate changes to squid.conf to permit browsing through the proxy.

please find my squid.conf file...

i have created two acls and two http_access rules

please let me know

---

### Post by SeijiSensei on 2012-07-06
I take it that RTF-formatted mess isn't the real squid.conf, right?  Can you post it again in plain-text, please?  And it would be nice if you ran:

```
grep -v ^\# squid.conf > clean-squid.conf
```

and post the latter to get rid of all the excess comments and just leave the actual directives.

If that really is your squid.conf file, well that's the problem right there.  It needs to be in plain text.

---

### Post by sdcisa on 2012-07-06
> **SeijiSensei said:**
> I take it that RTF-formatted mess isn't the real squid.conf, right?  Can you post it again in plain-text, please?  And it would be nice if you ran:

```
grep -v ^\# squid.conf > clean-squid.conf
```and post the latter to get rid of all the excess comments and just leave the actual directives.

If that really is your squid.conf file, well that's the problem right there.  It needs to be in plain text.

i had a copy of the original squid.conf, i have my changes and can you have a look
.

---

### Post by sdcisa on 2012-07-06
> **SeijiSensei said:**
> Well either you should be using the eth0 interface.  In squid.conf, what do you have for http_port?  Just "http_port 3128" or did you bind it to a specific IP?  I'd suggest not doing that.

Did you create one or more entries with "acl localnet src" that include the subnets from which you are connecting?  E.g.,

```
acl localnet src 192.168.1.0/24
```followed later by

```
http_access allow localnet
```Did you read the documentation at [http://www.squid-cache.org/Doc/](http://www.squid-cache.org/Doc/)?

Squid isn't the hardest thing to configure, but you do have to make the appropriate changes to squid.conf to permit browsing through the proxy.
well what i fel is that my process of squid3 is not getting registered.. i have typed the following commands and still its saying no process found.

root@sam-desktop:~# service squid3 start
squid3 start/running, process 2731
root@sam-desktop:~# sudo killall squid3
squid3: no process found
root@sam-desktop:~# service squid3 start
squid3 start/running, process 2802
root@sam-desktop:~# 

Why is the service not present?

---

### Post by SeijiSensei on 2012-07-07
I can't see anything glaringly wrong in the configuration.  I presume all the clients really are in 192.168.0.1-254, right?  Did you actually intend to use 192.168.0.0/16 instead?

The service is still running.  I forgot that though the package is called "squid3" the running daemon is called just "squid".  So the command "sudo killall -9 squid3" won't work, as you discovered, but "sudo killall -9 squid" should.  "-9" kills the process unconditionally. You might try using "-15" first which tells the process to shutdown "gracefully."  Only if that doesn't work should you resort to trying again with "-9".

You can see whether squid is running by simply running the command "ps ax | grep squid".  You don't need to be root to do this.

---

### Post by sdcisa on 2012-07-07
Hi SENSAI;

i am getting frustrated about the squid installation. i
i have noticed an incident is that there is no problem with the start command ie- service squid3 start, it shows the process id but  when i immediatly check the service squid3 status command ie- service squid3 status , it saying its stopped. Can you provide me a means to show the status as started and working.

and by the way i have run the ps grep command and the output is 

2620 pts/1    S+     0:00 grep --color=auto squid"

---

### Post by sdcisa on 2012-07-07
> **sdcisa said:**
> Hi SENSAI;

i am getting frustrated about the squid installation. i
i have noticed an incident is that there is no problem with the start command ie- service squid3 start, it shows the process id but  when i immediatly check the service squid3 status command ie- service squid3 status , it saying its stopped. Can you provide me a means to show the status as started and working.

and by the way i have run the ps grep command and the output is 

2620 pts/1    S+     0:00 grep --color=auto squid"

PLease note the following commands from my term:

root@sam-desktop:~# service squid status
squid: unrecognized service
root@sam-desktop:~# service squid3 status
squid3 stop/waiting
root@sam-desktop:~# sudo killall -12 squid
squid: no process found
root@sam-desktop:~# service squid3 status
squid3 stop/waiting
root@sam-desktop:~# service squid3 start
squid3 start/running, process 2515
root@sam-desktop:~# service squid3 status
squid3 stop/waiting
root@sam-desktop:~# ps ax | grep squid
 2620 pts/1    S+     0:00 grep --color=auto squid
root@sam-desktop:~# ps ax | grep squid3
 2631 pts/1    S+     0:00 grep --color=auto squid3
root@sam-desktop:~#

---

### Post by SeijiSensei on 2012-07-07
> root@sam-desktop:~# service squid3 status
squid3 stop/waiting
root@sam-desktop:~# ps ax | grep squid
2620 pts/1 S+ 0:00 grep --color=auto squid


No, it's not running.  As the status request says, it's stopped.  If it were running, you'd see lines like this:
```

21768 ?        Ss     0:00 squid -f /etc/squid/squid.conf
21771 ?        S    203:45 (squid) -f /etc/squid/squid.conf

```

This is from my CentOS server, so I don't know if the configuration file entry appears on the command line in Ubuntu.  The first entry is the "parent" process that runs with root privileges.  It spawns a child that runs as user "squid" and appears as "(squid)".  This is a security feature so that exploitation of the squid listener won't give the attacker root privileges.  Many server daemons work this way, the apache2 web server being a common one.

The line you report above in response to the "ps" command is the "grep" process in the second half of the command after the "pipe" symbol "|".  This syntax tells ps to pass its output to grep whereupon grep reports any lines containing "squid".  If you want to suppress the irrelevant "grep" entry, use:

```
ps ax | grep squid | grep -v grep
```

which will ignore any lines with "grep" in them.

---

### Post by sdcisa on 2012-07-08
the command above doesnt output any result....
Kindly let me know how to start the squid service.. and also let me know if there is any squid logs to help us troubleshoot the issue..

---

### Post by sdcisa on 2012-07-08
Thank you sensai,

i  couldnt wait any longer. i finally had to reinstall the entire squid.. i belive it was something to do with the squid.conf file.
i later took a backup after installation an then just added the following acl : my_lan 192.68.x.0 /16. & http_access rule for my_lan. before editing the squid.conf, i stopped the service. then started the same after editon.

Now i am able to see the service in ps aux and then able to get internet from the proxy machine and windows machine in the network.. thanks alot for your support.

---

