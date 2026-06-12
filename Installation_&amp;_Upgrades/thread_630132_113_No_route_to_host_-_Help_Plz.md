---
title: "113 No route to host - Help Plz"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Jhantu on 2007-12-03
Hello All,

I am new to Ubuntu and I am using Ubuntu 7.04 using VMware. I am running it on WindowsXP.

Well I was able to run ubuntu successfully from my home PC where I had a direct internet connection, however when I have come to college and I need to connect to internet through a proxy I am getting "**113 No route to host" error**.

However my Mozilla is working perfectly. I have already put the proxy string in the browser preferences. I am using Bridged Ethernet.

However when i issued the command, sudo apt-get update, I got the "**113 No route to host**" error.

Can some one tell me how to resolve this. Where do I need to setup the things to get my installations working.

Help me please.

Thanx in advance.
Jhantu

---

### Post by Jhantu on 2007-12-03
I tried doing the following things but with no success:

1. System --> Preferences --> Network Proxy, and enetered the proxy string but still getting the **113 No route to host** error.
2. Went to Network Setting, and in Wired Connections --> Properties, I changed it to **Automatic Configuration DHCP** from **Enable Roaming Mode**. HOwever I am still getting the same **113 No route to host** error.

However I am able to open all websites through my browser, but when i type "**sudo apt-get update**" in terminal prompt it gives me :

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg    
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (113 No route to host) [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (113 No route to host) [IP: 91.189.88.45 80]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
ubuntu@ubuntu:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg    
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (113 No route to host) [IP: 91.189.88.31 80]

Kindly lemme know what can i do to resolve this problem.

---

### Post by Jhantu on 2007-12-03
I tried further with :

1. Changing Ethernet from **Bridged** to **NAT**. And with this I tried both Enable Roaming Mode and Automatic Configuration DHCP. But I am unable to get my sudo apt-get update command working.

---

### Post by Jhantu on 2007-12-03
Finally it did worked, actually I had to configure apt to use the proxy settings which can be done by giving appropriate proxy settings in apt.conf.

---

