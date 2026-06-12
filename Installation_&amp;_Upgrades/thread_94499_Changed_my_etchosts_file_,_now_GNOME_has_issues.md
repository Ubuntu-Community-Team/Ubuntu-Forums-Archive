---
title: "Changed my etc/hosts file , now GNOME has issues"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by Antal on 2005-11-24
Hi Guys,

I'm a Linux noob and tried installing ISPConfig which went wrong. Reinstalled Ubuntu and tried again. 

ISPConfig requires you to change the hosts file.

this is what they want to change;

```
127.0.0.1       localhost.localdomain   localhost       server1
192.168.0.100   server1.example.com     server1

```

Instead of 192.168.0.100 I used my IP adres of the box, being 10.0.0.8 and I added " lunix.linuxhost"  where it says server1.example.com above.

I am trying to change the host file back to the original way but I get an error saying that it cannot connect to localhost.localdomain. After a reboot and initial log in screen a pop up from GNOME appears that it cannnot connect and asks my to cancel or re-try.

When i use sudo gedit etc/hosts it give me an error that it cannot connect either.

Any ideas? or the usual example why a noob like me should not use Sudo??? 

Love to hear some ideas.

Antal

Ps. Machine is at home and I am at work...

---

### Post by ranf on 2005-11-24
[QUOTE=Antal]
When i use sudo gedit etc/hosts it give me an error that it cannot connect either.
[/QUOTE]
Instead of `gedit' you could try `nano' in that line (I prefer `vi' but it really isn't "noobish").

You could also post the output of `ifconfig'.

---

### Post by Antal on 2005-11-25
thanks for the input, will do that later todat and keep you posted!

---

### Post by Antal on 2005-11-29
this is one of the "issues"
```
antal@linux:~$ sudo -s -H
sudo: unable to lookup linux.localhost via gethostbyname()
antal@linux:~$

```

plus the ifconfig output
```
antal@linux:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:55138 (53.8 KiB)  TX bytes:55138 (53.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:8B:8A:09
          inet addr:10.0.0.8  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:88ff:fe8b:8a09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20929 (20.4 KiB)  TX bytes:6841 (6.6 KiB)
          Interrupt:22 Base address:0xbc00

```

Any ideas how i can get the hosts file amended?

---

### Post by lcg on 2005-11-29
[QUOTE=Antal]this is one of the "issues"
```
antal@linux:~$ sudo -s -H
sudo: unable to lookup linux.localhost via gethostbyname()
antal@linux:~$

```
Any ideas how i can get the hosts file amended?[/QUOTE]
Boot any live CD you can find (Ubuntu's or Knoppix are fine), mount your / partition, fix your /etc/hosts file and you're good again.

HTH,
Lars

---

### Post by Topsiho on 2005-11-29
You can change the files that only root can change by booting into the rescue mode.

You are then root as indicated by the # prompt and can change the /etc/hosts file.

After that you just reboot the normal way and I hope your problem is solved :)

It's exactly how I solved the same problem that I had.

Topsiho

---

### Post by Antal on 2005-11-30
Thanks for all your help guys!

Got sorted!

---

