---
title: "cannot ssh into my home computer"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by raac on 2010-09-11
Hi guys, I would like to get help. I'm able to do
ssh localhost 

and works

but if I try to access from somewhere else it does not work?

after the ssh command
it would say Connection time out, and it would not let me ssh

I'd appreciate suggestions and by the way I'm new with linux

Thanks

---

### Post by v1ad on 2010-09-11
it would be your router. 
ifconfig, and look at your ip. if it starts with 192.168.0.*

then your gateway will be: 192.168.0.1

if its 192.168.1.*

then your default gateway is 192.168.1.1

open a web browser and type in your default gateway.
log into your router, depends on router login varies,
and forward port 22 to your ip address.

---

### Post by raac on 2010-09-11
Ok my IP address is
if its 192.168.1.*
then I typed  192.168.1.* into the web browser

Firefox can't establish a connection to the server at 192.168.1.*

I'm not sure how to do the next thing you said

" depends on router login varies,
and forward port 22 to your ip address."

Thanks for helping, I would appreciate a little bit more details

---

### Post by v1ad on 2010-09-11
your default gateway would be 192.168.1.1 thats what you type into the web browser. once you log in you will have a control panel, it varies on the kind of router you have.

---

### Post by raac on 2010-09-11
I tried that

Unable to connect

      

      
    
          

Firefox can't establish a connection to the server at 192.168.1.1.

        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

You want me to do that in the server or client computer?? I did that on both and got the same message from firefox..The thing is that one computer (server) has the ethernet cable and the client (laptop) has wireless connection from the same router

---

### Post by v1ad on 2010-09-11
try 192.168.0.1

and if your ip starts with 192.168 you can go ahead and post it, its a local area network ip address, and we all have a similar one.

also go from the server,  sometimes routers won't allow a wireless connection to log in.

---

### Post by v1ad on 2010-09-11
ifconfig in the server. and use the servers ip when you are forwarding the port.

---

### Post by raac on 2010-09-11
What exactly do u mean by "forwading the port" sorry if it's a silly question. 

I did ifconfig in the server, and i'm using the displayed ip address as my host, E.G.

ifconfig
inet addr:ipAddress

so i'd say in my laptop(client)

ssh username@ipAddress

and that when it stands there doing nothing and then I get a connection timeout

---

### Post by v1ad on 2010-09-11
well if you have a router on the server, the router has a firewall. and it blocks all those ports. ssh uses port 22, on the local area network it will work, on the web it won't. firewall blocks incoming connections.

you can login to the router through a web browser by typing in your default gateway. (server side not client). and through that way you connect to the routers control panel. in there you open port 22 for the servers ip address. if the servers ip address does not start with 192. then there is another issue. you do not type in the servers ip address but the routers.

---

### Post by v1ad on 2010-09-11
the reason the router blocks ports is because it does not know to what computer to direct it to. also if from the web you would not type ssh username@192.168.*.* but go to ipchicken.com, get the ip address that is supplied to your router and use that.

---

### Post by v1ad on 2010-09-11
your internet service provider provider gives you 1 IP, your Router uses it, then gives your computers in the house their own local IP address.

in the router control panel you tell it to send any information on port 22 to the servers local ip address.

to access it you ssh to the router and it forwards the information on that port to the server. thats why its called port forwarding.

---

### Post by raac on 2010-09-11
ok, I got to the point where I have the router setting on the browser, but I don't know where to go to open the port, there are a lot of stuff that i don't know about this web page, but all I care about is opening port 22. I went to setting and firewall but is not there. Under settings, there is broadband, LAN firewall, logs. The thing is I don't want to change something that I'm not suppose to change and screw up the internet

Thanks

---

### Post by v1ad on 2010-09-11
just find administration and port forwarding or anything about ports.

also what kind of router do you have. maybe ill find a tutorial.

---

### Post by raac on 2010-09-11
it's a 2wire

---

### Post by v1ad on 2010-09-11
[http://www.cctvcamerapros.com/2-Wire-Port-Forwarding-Setup-s/221.htm](http://www.cctvcamerapros.com/2-Wire-Port-Forwarding-Setup-s/221.htm)
[http://www.youtube.com/watch?v=KV0SBuc2sYw](http://www.youtube.com/watch?v=KV0SBuc2sYw)
[http://www.dslreports.com/faq/14305](http://www.dslreports.com/faq/14305)

pick any1 .

---

### Post by CharlesA on 2010-09-11
portforward.com

---

### Post by raac on 2010-09-11
should i select tcp or udp if i plan to ssh ?

and for the port range, would it be from 22 to 22??

---

### Post by v1ad on 2010-09-12
use both. and yes port range 22-22

---

### Post by raac on 2010-09-12
Well they are radio buttons (either or), i can only select one

---

### Post by v1ad on 2010-09-12
set up two. 1 udp, 1 tcp.

---

### Post by raac on 2010-09-12
Oh man, it still would not let me ssh, it came out the same thing

ssh username@ipadress
ssh: connect to host ipaddress port22: connection time out

All this work for nothing, lol

---

### Post by v1ad on 2010-09-12
ssh username@externalipaddress

specifying port not needed.  the ipaddress is the 1 u get from ipchicken.

the local ip will never work.

[http://www.ipchicken.com/](http://www.ipchicken.com/)

[email]username@thatipaddress[/email]

also in the router i hope u specified the servers ip address not your own.

---

### Post by raac on 2010-09-12
> **v1ad said:**
> ssh username@externalipaddress

specifying port not needed.  the ipaddress is the 1 u get from ipchicken.

the local ip will never work.

[http://www.ipchicken.com/](http://www.ipchicken.com/)

username@thatipaddress

also in the router i hope u specified the servers ip address not your own.

I tried that (ip chicken), same problem, and yes i did specified the servers ip address when i open the ports. (which is also a computer)

Could there be other problem?

---

### Post by v1ad on 2010-09-12
90% of the problems resolve in the router. question is, is from where are sshing from 2 your server. and the ipchicken is accessed from the servers local area network hopefully. what i do to test is ssh outside the network and then ssh back to the server from there. if you got noway to do that i can setup a temp username and password for you to do that off my server.

also another way is putting your server on DMZ what that does is bypasses all router firewalls. but its not recommended because it opens up your server to possible external attacks.

---

### Post by raac on 2010-09-12
ok. i'll try that...thanks for your help though i learned a great deal of networking


thanks a lot

---

### Post by v1ad on 2010-09-12
giving my best to help, Good luck.

---

### Post by Lateralis on 2010-09-12
You may need to install an ssh server on your home computer in order to connect to it, if you do not have it installed already. Certainly, that's what I've had to do in every distribution of Ubuntu before I could ssh in.  

```

sudo aptitude install openssh-server

```

There are then some optional configuration setps that you might (should) want to go through.  The configuration file is /etc/ssh/sshd_config.  First, make a copy of the file in case it all goes wrong:

```

sudo cp /etc/ssh/sshd_config ~/sshd_config.bak

```

Then you need to edit the file:

```

sudo gedit /etc/ssh/sshd_config

```

You will want to change the yes next to *PermitRootLogin* to a **no**.  And then at the bottom of the file add "*AllowUsers <your login name>*".  Save the file then restart the ssh server:

```

sudo /etc/init.d/ssh restart

```

You should now be able to ssh into your home computer, so long as your router now forwards connection requests sent over port 22 to your home computer.

---

### Post by v1ad on 2010-09-12
technically you can get away by just doing:
```

sudo apt-get install ssh

```
but i'm pretty sure you already did that. since you can connect locally.

---

### Post by Lateralis on 2010-09-12
A good point, I managed to conveniently miss. :P  

Never mind then!  *runs away*

---

### Post by rodgull on 2010-09-14
Lateralis,

Part of your suggestion fixed my issue.  Everything was going ok, then i installed some php extensions and ssh was broken.  I set PermitRootLogin to no and added an AllowUsers directive and bingo it works!

Thanks heaps.

Rod

---

### Post by rodgull on 2010-09-14
Actually wish I could vote for a post, as yours is really clear and helpful.

Rod

---

### Post by Lateralis on 2010-09-14
Ah, excellent!  Glad I was of some use (in a round about way!).

---

