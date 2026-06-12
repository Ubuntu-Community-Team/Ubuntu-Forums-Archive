---
title: "Connecting to SMTP remote host under AWS EC2"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by frankielee56 on 2012-08-22
Hey kids,

I'm running **Ubuntu Server 12.04 LTS **on several servers on the Amazon Cloud EC2 service. I have successfully installed and configured postfix/dovecot as a secure SMTP server on one of the servers. I can send emails from this server. Eventually I will be relaying to a bulk email service.

My problem is that I want to communicate with this server from one of the other servers in the same security group. I have searched for a solution and found a lot of advice, but nothing complete and comprehensive.

Things I've tried:
telnet ip 25 from remote host - it hangs and never responds
I've added the following 
mynetworks = 0.0.0.0/0 [::/0]
 to /etc/postfix/main.cf, and restarted postfix with no change

I've used netstat to verifiy postfix is listening on port 25
sudo netstat -plntu; sudo ls -l /proc/11830 | grep exe

tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      11830/master

lrwxrwxrwx 1 root root 0 Aug 21 23:00 exe -> /usr/lib/postfix/master

I can telnet in from the local host.

Can someone help me out here. Is this a conflict under EC2, SSH, postifix, or UBUNTU?

Thanks for your help.

---

### Post by dragonfly41 on 2012-08-23
I'm not at all sure if this is relevant to your problem since I'm fairly new to using AWS EC2 and S3 .. but yesterday I bookmarked this reference to "Elastic IP's" which apparently allow inter-instance communications.   I've yet to try it out.

[http://alestic.com/2009/06/ec2-elastic-ip-internal](http://alestic.com/2009/06/ec2-elastic-ip-internal)

---

### Post by frankielee56 on 2012-08-23
Thanks dragonfly41. I'm new to AWS EC2 as well, which is part of my frustration.

Elastic IP is good for setting servers under one ip externally, but I'm having trouble connnecting multiple servers internally.

---

### Post by dragonfly41 on 2012-08-23
As I read the article I found above (it needs some digesting) it suggests that Elastic IP can be used for inter server communications, as well as having a static IP address in your CNAME.

See this reference ...

> How do you solve the problem of connecting internal EC2 servers to each other?I've got as far as allocating an Elastic IP address to one of my EC2 instances but some more experimenting will be needed for testing inter-EC2-instance communications.

[COLOR=DarkRed][p.s.]

I found a further article here which gives more insights.

[http://about.silkapp.com/page/Multiple%20IP%20addresses%20on%20Amazon%20EC2]("http://about.silkapp.com/page/Multiple%20IP%20addresses%20on%20Amazon%20EC2")

and another here ...

[http://serverfault.com/questions/227682/whats-best-practice-for-communication-between-amazon-ec2-instances](http://serverfault.com/questions/227682/whats-best-practice-for-communication-between-amazon-ec2-instances)

[p.p.s]

Caveat.  Apparently only applies within a region and not between regions.




[/COLOR]

---

### Post by frankielee56 on 2012-08-23
Thanks again dragonfly41. As this was not the direct answer to my issue, it helped me dig deeper. When I started looking at the inbound ports on my security group I reallized SMTP port 25 was not open. I can at least telnet into the SMTP server from another instance.

---

