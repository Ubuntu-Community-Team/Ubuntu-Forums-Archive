---
title: "I have a dual boot question, please help"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by =FW= phoenix on 2007-07-19
I have installed both windows and ubuntu on a single HD. However when I boot into Ubuntu I have no internet. I use to only have ubuntu on this machine so I know they work well together. So is this just a matter of reloading ubuntu again? Any ideas or suggestions are appreciated and I thank you very much for your time.

---

### Post by az on 2007-07-19
> **=FW= phoenix said:**
> I have installed both windows and ubuntu on a single HD. However when I boot into Ubuntu I have no internet. I use to only have ubuntu on this machine so I know they work well together. So is this just a matter of reloading ubuntu again? Any ideas or suggestions are appreciated and I thank you very much for your time.

Whether you dual boot or single boot should not affect your network connection.  Can you provide more details please?  Are you saying it worked in Ubuntu before?  What kind of network connection do you have?

---

### Post by =FW= phoenix on 2007-07-19
Yes it worked just fine before. I'm on a 1.5MB dsl connection. Let me know if you need more info.

---

### Post by lord lewix on 2007-07-19
hi...
um did you install windows first or ubuntu..
if you installed ubuntu 2nd thats your problem wipe windows and ubuntu 
then install ubuntu and then windows..if that fails i have no idear...

---

### Post by =FW= phoenix on 2007-07-19
thank you for your response I'll will keep that in mind. I'm gonna wait for some more suggestions first though before I go wiping everything out LOL. Kinda pressed for time here lately so if there's a quicker fix it'd be a whole lot better.

---

### Post by bren on 2007-07-19
phoenix

I would ignore lord lewix if i was you - i don't think many people here would agree with what he says above...
The community will try and help you get it working....should be possible

Can you tell us

a) version of Ubuntu 
b) hardware you are using e.g. DSL cable modem, ADSL router, USB DSL modem
c) your PC name and model no.
d) go to applications -> accessories -.terminal and type ifconfig and post the results here...

bren

---

### Post by lord lewix on 2007-07-19
hello mister im so flash bren i had tthe same problem and what i said fixed it.. 
so i dont no what your talking about :mad:....

---

### Post by =FW= phoenix on 2007-07-19
O.K. I don't remember what version of ubuntu it is lol. If there's a way to find out let me know and I'll do it.
Next, I ran ifconfig so here it is.
eth0      Link encap:Ethernet  HWaddr 00:0C:41:28:DF:B5
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe28:dfb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1598 (1.5 KiB)  TX bytes:1152 (1.1 KiB)
          Interrupt:177 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5056 (4.9 KiB)  TX bytes:5056 (4.9 KiB)
I'm using a dsl modem running through a linksys 4 port router using standard cat 5e cable. Been using this setup for along time with no problems.
As for my computer...It's one I built myself-comprised of an asus A7S333 board with an AMD XP 2400+ chip and 512 ram with an 80GB HD.

---

### Post by confused57 on 2007-07-19
You can determine this in a terminal to determine which kernel you're using:
```
uname -r
```

I think you can click on System, then "About Ubuntu" &  it'll tell you which version you're using.

If you're using Feisty(or Gutsy), there is a Network Manager launcher in the upper panel...if this is the case, open the Network Manager manual configuration, remove the check next to Eth0, then click it again to re-enable...this will reconfigure your network connection.

You might also try:
```
sudo /etc/init.d/networking restart
```

---

### Post by =FW= phoenix on 2007-07-19
Ok thank you very very much for your help. I ran the sudo /etc/init.d/networking restart command and it worked like a charm. You are my new best friend. LOL 
Thanks to everyone who responded with their time and knowledge.

---

### Post by confused57 on 2007-07-19
> **=FW= phoenix said:**
> Ok thank you very very much for your help. I ran the sudo /etc/init.d/networking restart command and it worked like a charm. You are my new best friend. LOL 
Thanks to everyone who responded with their time and knowledge.
Glad to help...it's a little something I learned from testing Gutsy.

---

