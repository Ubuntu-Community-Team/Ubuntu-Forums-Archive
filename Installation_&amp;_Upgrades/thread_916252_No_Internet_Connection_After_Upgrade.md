---
title: "No Internet Connection After Upgrade"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by pavicnat on 2008-09-10
I upgraded my distro to Ubuntu 8.04 with an internet connection, but as soon as it was done I couldn't reconnect to the internet. I rebooted my computer a couple of times, and noticed that I was getting an error about not being able to start HAL. 

Other than "being unplugged from the wall", is there anything else which should hinder my internet connection?

---

### Post by cariboo on 2008-09-10
Your a little short on information. What kind of network connection is it?
Have you checked to see if the proper module for your network card is loaded.
What is th output of ifconfig?
Have you tried:

```
sudo dhclient eth0
```

Replace eth0 with whatever your network interface is.

Jim

---

### Post by pavicnat on 2008-09-10
Hi, thanks very much for your reply and ideas. 

The only one of your questions I can answer is that it is a regular ethernet connection.

I am not at home to check this right now, so I shall have to answer your other three questions later. I will return tomorrow with an answer to what is returned by running 'ifconfig' and 'sudo dhclient eth0'.

Please stay posted for those answers. 

How do I check if the proper module for the network card has been loaded?

---

### Post by pavicnat on 2008-09-11
Running 'ifconfig' in the terminal returned no result. 

Running 'sudo dhclient eth0' connected me to the internet for a very brief time. Once I ran this command I opened firefox and my computer actually froze. I have never seen a Linux OS freeze. I couldn't even open another terminal. I have not idea why this is the case. 

Anyone have ideas?

---

### Post by jal301 on 2009-11-02
> **pavicnat said:**
> Running 'ifconfig' in the terminal returned no result. 

Running 'sudo dhclient eth0' connected me to the internet for a very brief time. Once I ran this command I opened firefox and my computer actually froze. I have never seen a Linux OS freeze. I couldn't even open another terminal. I have not idea why this is the case. 

Anyone have ideas?

I ran 'sudo dhclient eth0' and that got my internet connection going in both Firefox and Newsreader.  Any idea why this worked?

---

