---
title: "dummynet+ipfw"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by ramu492 on 2011-05-02
hi,

 i have a problem with dummynet. I have  installed dummynet on ubuntu 10.10.

my laptop is connected to another laptop via cross cable.
my ip being XXX.XXX.0.1  and anohter one being xxx.xxx.0.2

I am generating UDP traffic with Iperf

when i use the command,

**ipfw add pipe 03 ip from any to any**

there is no traffic flowing from my laptop to other laptop. I observed this with wireshark.

when i flush the rules, traffic flows normally!! 

waiting for ur replies,

Thanking you before !!

---

### Post by Monu_93 on 2011-07-13
Hi ramu,

According to dummynet website and documentation, you have to create a pipe and configure it like :

ipfw add pipe 3 ip from any to any
ipfw pipe 3 config xx xx xxx

Do you configure your pipe ?? 
Do you know if dummynet module works on Ubuntu 11.04 ?? 

Thank you.

---

