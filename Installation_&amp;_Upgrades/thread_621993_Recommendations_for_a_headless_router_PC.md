---
title: "Recommendations for a headless router PC"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by datablitz7 on 2007-11-24
Hi everyone, this is my first post. First things first: I'm a complete noob when it comes to linux. I understand the underlying principles of PCs and am a quick learner....

Now, to the point, I have an old PC lying around. It's a Slot 1 PIII 450MHz, 512MB SD-RAM. I want to make it into a headless DSL router that is going to be tucked in my closet, will be online 24/7 and will server through an 8-port switch at least 2 other PCs with internet. I want to run on it a DHCP server, a DNS server (I think i need to anyways), a Samba and an FTP server. The idea is to manage this PC with webmin from my regular desktop.

Question 1: Obviously i don't need any gui, since the PC won't have a monitor. Should I use ubuntu alternate CD or xubuntu alternate CD? I understand these are text only?

Question 2: Do I need to run DHCP and DNS server on it?

Thanks in advance!

---

### Post by Pumalite on 2007-11-24
You can load a Server in your hardware. Do you have a Home LAN? If not, get one. Get a router set to give DHCP to dynamic IP's
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I recommend 6.06 Server Edition

---

### Post by Phurious on 2007-11-24
I run Smoothwall instead of Ubuntu; geared more for what you are trying to do.

[http://www.smoothwall.org/]("http://www.smoothwall.org/")

---

### Post by arsenic23 on 2007-11-24
> ubuntu alternate CD or xubuntu alternate CD

The Ubuntu Alternate cds do install a GUI, they just don't have a GUI installer.  Like Pumalite said, you want Ubuntu Server if you don't need a GUI installed on your machine.

---

### Post by datablitz7 on 2007-11-24
Thanx for your replies. Isn't 7.10 supposed to be any better?? Why recommend the 6.06 version? (older kernel).
Smoothwall looks the part, but can I ran an ftp server off of it?

---

### Post by Pumalite on 2007-11-24
More reliable. Proven. And longer support. Besides, you can do anything you want with it.

---

### Post by datablitz7 on 2007-11-24
Damn you're fast! And to the point! Downloading now 6.06 LTS server... Will keep you informed

Thanks everybody for your prompt and accurate answers

---

### Post by Pumalite on 2007-11-24
Good luck.

---

### Post by datablitz7 on 2007-11-25
Ubuntu Server 6.06 is up and running! I'm running dhcp3, ssh, samba and dns servers. I wanna do an ftp too later. And guess what, I have a few more questions....

1. All I need is to setup this headless PC as a router...Do I need DNS server on it?

2. I have set up NAT but I can't get it to work. I can connect to the net on the ubuntu box and dhcp seems to give out ips fine but no other computer on the network has internet...

3. Off topic... Since I'm running headless and I have no sound card on, is it safe to remove alsa?

Thanks again for your time

---

### Post by Pumalite on 2007-11-25
Check each connection individually. If you set your router to give each of your computers an IP via DHCP there should be no problems. You don't need sound in a server.

---

### Post by datablitz7 on 2007-11-25
Individually everything works fine...

i can ssh into the server or run webmin. I can connect to the internet on the server (i think). It seems to connect fine but i don't know how to test my internet connection without a browser. would ping work?

Btw do i need to run a dns server??

I want to use no-ip.com for dynamic dns in order to ftp and ssh to my box from anywhere

---

### Post by Pumalite on 2007-11-25
To tell you the truth, I'm not the best guy to answer all your questions regarding a server. Now that you have it installed, start a new thread with an appropriate name.

---

### Post by datablitz7 on 2007-11-25
No problem. Thanks for all your help so far! See you in another thread

---

### Post by Pumalite on 2007-11-25
OK. Good luck.

---

