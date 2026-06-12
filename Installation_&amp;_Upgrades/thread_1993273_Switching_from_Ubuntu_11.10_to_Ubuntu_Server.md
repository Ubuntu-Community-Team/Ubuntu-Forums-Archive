---
title: "Switching from Ubuntu 11.10 to Ubuntu Server"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by julesmazur on 2012-06-01
I've never done this kind of switch before. My machine is natively Windows, and has a BIOS. How do I go about doing this?

---

### Post by jadtech on 2012-06-01
> **julesmazur said:**
> I've never done this kind of switch before. My machine is natively Windows, and has a BIOS. How do I go about doing this?

if you have ubuntu 11.10 already installed why not just go to the software center and down load the server application if its a webserver search and down load Apache once that is done you can figure out if you need  MYSQL and other parts just get what you need ... 

all computers have bios  not really sure what  you are look for in the way of advice there ..

just understand that if you install  a server  all well and good but work on the server has to be done remotely from another computer for the most part other then installing and updateing  the server aplications them selves and reboot and even these things can be done remotly, think of it as your personal cloud service :)

get the server installed and running you can even  romove the keyboard monitor and mouse no need for them on a server at all  really ..

---

### Post by julesmazur on 2012-06-02
Will the server application install the exclusively command-line server? The computer I'm going to use is an old machine, and the GPU can't handle Ubuntu's interface.

---

### Post by voyy on 2012-06-02
> **julesmazur said:**
> Will the server application install the exclusively command-line server? The computer I'm going to use is an old machine, and the GPU can't handle Ubuntu's interface.

If you ask about apache/mysql/php/firewall then of course, they it will install just by command line. Did that many times. Not much experience with other server orientated soft but I can't imagine that it would be impossible to install without X loaded.

---

### Post by julesmazur on 2012-06-02
Alright, in that case, which server app from the software centre is the one in question? There seem to be dozens of them, most of them manuals and scripts. I can't actually find a concrete Apache server app.

---

### Post by darkod on 2012-06-02
I think the title of your thread is confusing. You say switching from ubuntu 11.10 which sounds like it's already running on the machine, but then you say it's an older machine and can't take the GUI of 11.10.

If you are after the server version, download the ISO, burn a cd from that image, and install the server version. Also, it's much better to install 12.04 LTS right now instead of 11.10. That will be a command line only since the server version is CLI.

Otherwise, you can install Apache webserver on ubuntu desktop 11.10 for example, but it will not make it a command line only system. It will still be ubuntu desktop 11.10 with its GUI, only running apache server on it.

---

