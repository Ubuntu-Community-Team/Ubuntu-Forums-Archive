---
title: "What type of server should I install?"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by boeing114 on 2011-01-29
I am going to be setting up my first ubuntu server this week, and I noticed in tutorials, that there are different options for what type of packages you want installed. I know a little bit, like what a DNS server is and such, but I am hoping somebody can shed some more light on the subject. These are the options:

DNS Server
LAMP Server
Mail Server
OpenSSH Server
PostgreSQL Server
Print Server
Samba File Server

I am pretty sure I won't need Postgresql or a print server, as the purpose of my server is to provide a low end platform that I can work on my php projects. I will be using PHP and mysql. I am also using Ubuntu 10.04 LTS, 32-bit edition.

---

### Post by boeing114 on 2011-01-29
Bump?

---

### Post by NightwishFan on 2011-01-29
I am assuming you are familiar with the GNU/Linux command line interface and Debian administration? Ubuntu server is a minimal platform with no graphical interface. It is only different from Ubuntu Desktop as it has different packages and a slightly different kernel installed. A GUI or any packages can easily be installed however you need to be familiar with Debian tools such as apt-get.

I would assume if you do not need any of the listed servers, you can simply install none of them, and just apt-get the required packages.

Hope that answers any questions, I was assuming you were not a beginner, but clarified just in case.

---

### Post by boeing114 on 2011-01-30
I know that it has no gui, and I have used aptget with ubuntu desktop. I realize each of the options just installs different apps, but I want to know more about the packets that get installed, and the pros and cons of the different server types

---

### Post by cj.surrusco on 2011-01-31
Well, it all depends on what you want to do with the server. If you want to share files, you might want to install an FTP server. An SSH server will allow you to remotely and securely control your server. An apache server will allow you to host websites. The list goes on.

---

