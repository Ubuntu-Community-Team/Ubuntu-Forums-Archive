---
title: "Need Help Installing GUFW"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by xMoDx on 2008-07-17
> sudo wget [http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb](http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb)

sudo dpkg -i gufw-0.0.3.deb

from: [http://ubuntuforums.org/showthread.php?t=800950](http://ubuntuforums.org/showthread.php?t=800950)


> mod@mod-laptop:~$ sudo wget [http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb](http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb)
[sudo] password for mod: 
--10:22:49--  [http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb](http://gui-ufw.googlecode.com/files/gufw-0.0.3.deb)
           => `gufw-0.0.3.deb'
Resolving gui-ufw.googlecode.com... 64.233.187.82
Connecting to gui-ufw.googlecode.com|64.233.187.82|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
10:22:50 ERROR 403: Forbidden.

mod@mod-laptop:~$ 




    Forbidden
    Your client does not have permission to get URL /files/gufw-0.0.3.deb from this server. (Client IP address: 121.97.226.112)

    You are attempting to perform an activity that you have insufficient permissions for. If you feel this is in error, please contact the project administrator.

is their another way to install GUFW?

---

### Post by tommcd on 2008-07-17
I am not familiar with GUFW, but I got the 403 forbidden too when I tried to download it.
Have you tried Firestarter? It is a nice and simple firewall with a GUI. It is available in the Ubuntu repos. I have used Firestarter before and it works about as well as any other software firewall.

---

### Post by gaiterin on 2008-07-19
Hi!
The web changed to [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/) and Launchpad ;)
You can download 0.0.6 version, but the 25 July 2008, will release the 0.0.7!
Best regards.

---

### Post by tommcd on 2008-07-20
> **gaiterin said:**
> Hi!
The web changed to [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/) and Launchpad ;)
You can download 0.0.6 version, but the 25 July 2008, will release the 0.0.7!
Best regards.

Have you used GUFW? If so, does it offer any significant advantages over Firestarter? I'm just curious about it.
Searching around the ubuntu forums there does not seem to be much info on it. Here is a thread discussing UFW, the command line version:
[http://ubuntuforums.org/showthread.php?t=823741&highlight=gufw](http://ubuntuforums.org/showthread.php?t=823741&highlight=gufw)

---

### Post by gaiterin on 2008-07-20
Hi, yes I used Gufw, I development it.
Gufw or ufw is for allow/deny ports/ips, hide IP (Ipv6 included).
It isn't good for me to compare it with Firestarter.
Best regards.
Marcos.

---

### Post by xMoDx on 2008-07-26
sometimes firestarter daemon wont start when using my laptop

---

