---
title: "Upgrade to 6.06 Server"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Bob_Mendon on 2006-06-10
I would really like to use 6.06 server with LAMPS (?) support but have not been able to do so. I can upgrade from 5.10 to 6.06 Desktop with little problem but can't figure out how to do the same to upgrade to 6.06 Server.

Am I missing something or is it impossible to upgrade from 5.10 to the 6.06 Server product?

Thanks

---

### Post by Seaman on 2006-06-10
Ubuntu 6.06 Desktop has almost all the things that Ubuntu 6.06 server has but some services (I think) like ssh/ftp-server (which easily can be installed with apt-get).

A simplified description of Ubuntu 6.06 Server would be "Ubuntu 6.06 Desktop without GUI". It is just less bloated.  So if you for example want to run a web server. Just make an update to 6.06 Desktop, install apache or what ever you prefer and do not start the gui when you start your computer (this may require som tweaking though).

I hope this description and instructions are correct ;) I have never installled Ubuntu with the Ubuntu Desktop cd, only with the server cd.

---

### Post by Bob_Mendon on 2006-06-10
It's beyond me why the two were split. I thought 6.06 server was supposed to have a GUI as well or am I mistaken. I am fully aware that I can install Apache etc on the desktop but I have used LAMP before and it is so much easier to manage.

---

### Post by Seaman on 2006-06-10
[QUOTE=Bob_Mendon]It's beyond me why the two were split. I thought 6.06 server was supposed to have a GUI as well or am I mistaken. I am fully aware that I can install Apache etc on the desktop but I have used LAMP before and it is so much easier to manage.[/QUOTE]
Well, a basic server install of Ubuntu does not come with any gui, but there is nothing that prevents you from installing X and a window manager or similar if you want.

---

