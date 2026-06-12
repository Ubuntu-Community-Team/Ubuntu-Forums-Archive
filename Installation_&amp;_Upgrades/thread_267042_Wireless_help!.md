---
title: "Wireless help!"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by Transmit on 2006-09-28
Hi guys, I finnaly got to installing Ubuntu (latest version). Now I want to get my wireless working (secured with mac adress checking).

The only problem is that I do not have a clue how to do this.
So I'm pretty much asking for a quick guide on this.

Oh and I went to the add/remove programs thing but when I click a checkbox (I wanted to install the wireless manager or something) I get this error:
"package name is not available in any software channel
The application might not support your system architecture."

Thanks in advance!

---

### Post by happy-and-lost on 2006-09-28
```
sudo apt-get install wifi-radar
```

BTW, what's the iwconfig output?

---

### Post by Transmit on 2006-09-28
What's iwconfig and where do I put "sudo apt-get install wifi-radar" this?

Sorry I'm a big noob in ubuntu :(

---

### Post by happy-and-lost on 2006-09-28
Ah right, fire up the terminal (Applications-->Accessories) and type in iwconfig. Then copy and paste all the confusing looking text it gives you.

---

### Post by Transmit on 2006-09-28
K I'll need to reboot because I'm on windows and I do not have internet on ubuntu!

be right back!

---

### Post by happy-and-lost on 2006-09-28
If you have a wifi router, plug it into the ethernet and Ubuntu will pick that up, then you won't have to keep rebooting.

I have to go to my A level chemistry lesson now, I'll help you when I next have free time.

---

### Post by Transmit on 2006-09-28
k I get his for the swconfig:

jan@jan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Transmit on 2006-09-28
and another thing: can you tell me how I can run .dmg files?

oh yeah when I try to go on my hard drive sometimes it says: You do not have permission to write blalbal

---

### Post by happy-and-lost on 2006-09-28
1. I've never come accross .dmg files, I'm afraid.

2. What format is your hard drive in?

3. If you wire your computer up to ethernet (if possible, if not, download the .deb files [like .exe files, double click them, grant permission and press install] here [http://packages.ubuntu.com/dapper/net/wifi-radar](http://packages.ubuntu.com/dapper/net/wifi-radar)) and fire up the terminal and type "sudo apt-get install wifi-radar"

---

### Post by Transmit on 2006-09-28
K I got it installed, now what?

Is it possible that my wireless card isn't installed yet?

---

### Post by happy-and-lost on 2006-10-02
Sorry for the delay, was in France.

Have you used wifi-radar yet? If it can't see any networks, you've a problem with the card.

---

