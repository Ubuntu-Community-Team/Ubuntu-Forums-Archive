---
title: "Trying to SSH from PC to laptop"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-11-01
Hello Experts !!

I am trying to do an ssh from one machine to another.

So I have checked that port 22 is not closed on my lap top,  I have tried to ping the ip of my laptop and get something like this

64 bytes from 192.168.1.2: icmp_req=1 ttl=64 time=0.244 ms

which repeats with changes to "ms" at the end.

I then try 

ssh  root@192.168.1.2

and get cannot connect to host 192.168.1.2 port 22: Connection refused

So what am i doing wrong here ???

---

### Post by Lars Noodén on 2012-11-01
That you can ping the machine is a good sign.  Let's check the obvious first.

Do you have the package openssh-server installed on the machine you are trying to connect to?  If the machine you are trying to connect to has a firewall active (e.g. UFW), have you opened port 22?  Also, on that machine, what is the status of sshd?  

```

service ssh status

```

Also, it's not a good idea to allow remote log in as root.  That can be disabled by editing the target machine's /etc/ssh/sshd_config file to have the line "PermitRootLogin no"

---

### Post by bencouve on 2012-11-01
[FONT=Times New Roman, serif]Hello Lars Noodén (what a great name), I will check that and get back. Thanks for the response.[/FONT]

---

### Post by bencouve on 2012-11-01
Hi Lars, you were right, it was the firewall. Worked once switched off.

Am aware that ssh as root is not advised, just wanted to see it work..

Thanks for you help, much appreciate

---

