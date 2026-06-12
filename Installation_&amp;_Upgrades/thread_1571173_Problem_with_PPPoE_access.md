---
title: "Problem with PPPoE access"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by i-idea on 2010-09-09
Hi
 
This is my first post so hello to everyone. I am a web designer and don't know anything about servers. My server service provider use Linux environment and sometime it would be much easier for me to have a local server to test my websites. 
 
So I have install a fresh copy of Ubuntu 10.04 to one of my computer. Half way installation, the system tell me something like couldn't configure the DHCP, I have checked that my router has enabled DHCP servers (D-Link 615).
 
After installation and logon, I use **sudo pppoeconf** command and try to set the network. But it said something like no PPPoE access.
 
I know I am very dull, and maybe get ban from this forum because I have not read the instruction, it will be great if you can point me to the right page. All I want to do is have something like a web space + MySQL and support PHP to work with. Want to know how to set it all up. please help.
 
 
:KS
Many thanks
 
Genesis

---

### Post by tyblogger5 on 2010-09-09
Try to refresh the IP with:

```
sudo dhclient
```

To install Apache Server, PHP, MySql (LAMP Server), use the following command:

```
sudo tasksel install lamp-server
```

I'm learning web development as well and it takes a little bit to figure out how to install LAMP for a new-comer.

Does this help?
Tariq

---

### Post by i-idea on 2010-09-09
Thank you Tariq for your rapid response
 
I will try that now and let you know right away.

---

### Post by i-idea on 2010-09-09
Done that, is said no DHCP lease received. Any idea?

---

### Post by tyblogger5 on 2010-09-09
Hmmm...could you type in:

```
ifconfig
```

and copy the output (by the way, this command is the same as ipconfig in windows).  This might be able to give me a little more info.

---

### Post by i-idea on 2010-09-09
Comes up loads of stuff, which part is significant?
 
Thanks

---

### Post by tyblogger5 on 2010-09-09
If you are trying to connect with ethernet, there should be some things with ethX (X is a number usually 0).  Just to be safe copy everything onto the forum.

-Tariq

---

### Post by i-idea on 2010-09-09
[IMG]http://www.i-idea.co.uk/photo13.jpg[/IMG]

---

### Post by i-idea on 2010-09-09
I am so sorry. As Linux in my other PC are the only operating system. I couldn't think of a better way than take a photo. Hope you can read that ok. Many thanks

---

### Post by tyblogger5 on 2010-09-09
I'm clueless now, I'll try to research it a little bit if I have time.  By the way, check that the cable is plugged in on both sides (it doesn't hurt to check :)).

-Tariq

---

### Post by i-idea on 2010-09-09
thanks for your help. I have checked the cable. Cable is good.

---

### Post by tyblogger5 on 2010-09-09
Check out this site, it might help you:

[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

---

