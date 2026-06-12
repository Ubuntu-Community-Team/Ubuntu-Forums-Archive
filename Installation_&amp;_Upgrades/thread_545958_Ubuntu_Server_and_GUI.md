---
title: "Ubuntu Server and GUI"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by dc.manage.service on 2007-09-08
Hi there

I'm installing Ubuntu Server but I'm stuck with the command line. Is there documentation showing the step by step to configure the GUI and accounts?

Thanks

---

### Post by Steveway on 2007-09-08
The server-edition doesn't come with a GUI, it isn't needed on a server.
You can install one with:
sudo apt-get install ubuntu-desktop

---

### Post by peachy on 2007-09-08
If you want a GUI install Xbuntu, not Ubuntu server.

You might find Ubuntu server + Webmin to be a good alternative. I don't think it's in the repos but you can get it from [www.webmin.com](www.webmin.com)

Install Ubuntu server. SSH to the machine

```
cd /tmp
wget http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.360_all.deb
sudo dpkg -i webmin_1.360_all.deb
```

At this point it will fail to install due to missing dependencies. You can install them using aptitude
```
sudo aptitude update
sudo aptitude install <list of files that dpkg was missing seperated by spaces>
```

The should install webmin too, if it doesn't just install via dpkg as listed above.

You should be able to login to webmin via [https://hotsname:10000](https://hotsname:10000)

There's probably a HOWTO on here somewhere if you search.

---

### Post by dc.manage.service on 2007-09-08
1) What I want is actually if I can manage the FILE SERVER, DNS SERVER ETC (SERVER APPS) through GUI. So if I install ubuntu-desktop as per advised. Do I get the that GUI?

2) I looked at Xubuntu.org. Do I get the GUI for FILE SERVER, DNS SERVER ETC (SERVER APPS)?

Thank you

---

### Post by merlinus on 2007-09-08
As peachy said, webmin is a gui for adminstrating all aspects of a server.

You can go to the website, download and install it.

The interface runs in your browser.

-merlin

---

### Post by kerry_s on 2007-09-08
[B]sudo apt-get install xorg fluxbox
startx[/B]

---

### Post by dc.manage.service on 2007-09-08
So I need to install webmin and stick with Ubuntu Server version.

but when I try do the SSH, it said that it can't connect. But I can ping address though.

Do I miss anything? BTW ... once do the installation Ubuntu Server, do I need to configure anything after that? Like DNS, SSH server, File Server?

Is there any documentation on how to do this?

Thanks

---

### Post by merlinus on 2007-09-08
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

-merlin

---

### Post by maybeway36 on 2007-09-08
```
sudo apt-get install openssh-server
```
After that, you can take several different approaches.

---

### Post by jwarra on 2007-09-08
I have just 'inherited' a linux server at my new job. There was no documentation so trying to get my head around how the server works. At present just turn it on and it works but would love to know how I can back up the server in case of problems, especially if I start playing around with it.
The lack of a gui has me stumped. 
Is it possible to install the ubuntu desktop from a magazine disk and not affect the server?
Have got webmin working from a browser and have no idea about samba.
Any help would be much appreciated

Jim

---

### Post by merlinus on 2007-09-08
You can install a gui, but where would you install it to?

For example:

```

sudo aptitude update && sudo aptitude install gnome-desktop

```

-merlin

---

### Post by AnRa on 2007-09-08
Gutsy will come with [eBox](http://www.ebox-platform.com/). ;)

---

