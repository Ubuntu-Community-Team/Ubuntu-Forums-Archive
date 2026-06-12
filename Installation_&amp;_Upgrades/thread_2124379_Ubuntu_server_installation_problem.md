---
title: "Ubuntu server installation problem??"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by FOCIRL on 2013-03-10
I recently installed the ubuntu 12.10 server and client. I've also installed LAMP server but when I go to view my localhost/phpmyadmin page it does not load correctly. Just seems to be forever trying to load. I then installed squirrelmail and when I went to view localhost/squirrelmail, the same thing happened. I thought my problem was initially with the incorrect installation of LAMP server but I dont think this is the case now since I installed squirrelmail and I seem to have the same problem. I'm thinking the problem is from when I initially installed the ubuntu 12.10 server. Anybody think they may be able to shed some light on my problem. Kinda stuck and frustrated with it!!!

---

### Post by RoosterHam on 2013-03-10
What is your network config? are you using the hostname localhost to connect? can you ping localhost? have your tried [https://NETWORK_IP_ADDRESS/phpmyadmin?](https://NETWORK_IP_ADDRESS/phpmyadmin?) are you trying http: or https:?

---

### Post by FOCIRL on 2013-03-11
My network is a small vmware vApp with one client and one server machine. It has no connection to the outside world therefore http:// or https:// isnt working. When I put in IP address which is 192.168.2.101/phpmyadmin the page just keeps trying and trying to connect to the page, it does the same for squirrelmail.

---

### Post by darkod on 2013-03-11
The server OS by default has no web browser. How are you trying [http://locahost/phpmyadmin?](http://locahost/phpmyadmin?)

If you are trying from the desktop VM, have you confirmed they are in the same network? Can you ping the private IP of the server from the desktop? And did you set static IP on the server or left it dynamic (dhcp)?

Also, with VMs you have to be careful since many times they are configured with the network adapter in NAT mode by default. Trying to open web pages through NAT might not work as you expect it. Set the settings of the VMs to have the network adapters in Bridged mode, that way they should be inside your host network instead of receiving a NAT-ed IPs.

---

### Post by FOCIRL on 2013-03-11
Yes I am trying from the desktop VM, I am able to ping between the two so no issues there. They are static IPs also. However it is configured with the network adapter in NAT mode. I'm unsure if I can change the settings of the VMs as I am not using VM workstation, it is a university vcloud so would prob need administrator to change this???

---

### Post by darkod on 2013-03-11
You can't use localhost from the desktop. As the name says, that means the local machine (and the applications are on the server). As mentioned earlier, have you tried something like:
http://<server IP>/phpmyadmin

---

### Post by FOCIRL on 2013-03-11
Yes have tried the following 192.168.2.101/phpmyadmin and this does not load the page correctly, just keeps loading, like its forever searching, when I try loading the following 192.168.2.101/info.php this shows up the PHP info page no problem (have installed LAMP server) ??

---

### Post by darkod on 2013-03-11
I might be wrong but I'm not sure phpmyadmin is part of LAMP. Have you double checked that? Or maybe you need some changes in the config so that it shows up for you?

---

### Post by FOCIRL on 2013-03-11
Yes it is part of LAMP but I'm pretty sure I've configured this correctly but I've since configured SquirrelMail on my server and this too will not load the webpage 192.168.2.101/squirrelmail, it does the exact same thing as with phpmyadmin so therefore it must be something wrong with the server installation?? Pulling my hair out with this one!

---

### Post by darkod on 2013-03-11
Hmm, this says it's not part of LAMP and you need to install it separately:
[http://tuxtweaks.com/2011/10/install-lamp-and-phpmyadmin-on-ubuntu-11-10/](http://tuxtweaks.com/2011/10/install-lamp-and-phpmyadmin-on-ubuntu-11-10/)

Unless something has changed since then.

I don't think there is anything wrong with the server installation. Maybe if you need to do some additional configuration after, but not with the installation itself.

Also, some programs might give you issues over NAT, that's why I wouldn't use a NAT-ed server VM. But you already mentioned you don't have direct control of that.

Since you have LAMP, test apache too by opening the IP address in web browser:
[http://192.168.2.101](http://192.168.2.101)

As for Squirrelmail, do you have a mail server installed? Like an IMAP server at least? So far you only mentioned installing LAMP but you need mail server before using squirrelmail.

EDIT PS. This also says you need further configuration of apache before squirrelmail can work. Did you do something like that?
[http://www.techrepublic.com/blog/doityourself-it-guy/diy-install-squirrelmail-to-allow-web-access-to-your-postfix-server/841](http://www.techrepublic.com/blog/doityourself-it-guy/diy-install-squirrelmail-to-allow-web-access-to-your-postfix-server/841)

---

### Post by FOCIRL on 2013-03-11
I have successfully installed the following on the server, using this tutorial, [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3). I've tested apache and it works in the browser using 192.168.2.101.....

---

### Post by steeldriver on 2013-03-11
Why not just check that for sure phpmyadmin is installed? e.g.

```
dpkg -l | grep php
```

As others have pointed out, it does not appear to be part of the standard LAMP stack - at least it isn't installed as part of 'lamp-server^'

---

### Post by darkod on 2013-03-11
I remember another thread yesterday which had DNS problems and it followed the same tutorial to install the server. Only it turns out ISPConfig doesn't create the A records for the nameservers and bind wasn't working properly.

There are many tutorials and I have nothing against it, but sometimes they can lead the unintented results. I would recommend you do things manually, like we saw in that other thread. Using ISPConfig didn't do its job and the person spent hours troubleshooting, when the job would have been done in 5mins if he configured bind manually at the command line.

I didn't write that tutorial and I can't sey what it does or does not do, but your system is not working as expected and the server installation is not to blame. The configuration after the installation is the problem as it seems.

---

### Post by darkod on 2013-03-11
I forgot to mention, did you double check my post #10 because I edited it and added a link explaining the procedure for squirrelmail and apache. It seems after installing squirrelmail you do need to make changes to the apache configuration too. Not sure if you did this. It doesn't work by default.

---

### Post by FOCIRL on 2013-03-11
...

---

### Post by RoosterHam on 2013-03-11
The tutorial you provided a link to is for 12.04. You are installing 12.10? while I don't think using a 12.04 guide on 12.10 will break anything or cause massive rifts in the space-time continuum, using a guide for the edition you have chosen to install is usually the best idea. Newer releases have quicker ways of doing things and guides for the right release will point out anything peculiar to that release.

You say you can ping the IP address? if the virt-host is using a NATed interface, then you're probably getting replies from the physical host system and not your virtual server. Take the advice of others who've already posted; contact the admin responsible for the VM host and have it set to bridged mode with a network visible static IP.

You mentioned there's no connection to the outside world and so http:// and https:// won't work. http and https don't mean the world wide web. they simply are how your browser is connecting, not to where. I was administering a nagios and a graylog2 system, if I just entered the IP of the nagios system it would changet to https://<nagios-ip>. but when I entered the graylog2 systems IP, it looked up http://<graylog2-ip> and just sat there till it timed out. The server was running, everything was configured. When I entered https://<graylog2-ip> it connected fine. I haven't gotten a chance to find out why, in my network, it didn't matter to nagios but was important to graylog2.

Check what the tutorial guided you through with these howtos from ubuntu:
[https://help.ubuntu.com/12.10/serverguide/lamp-applications.html](https://help.ubuntu.com/12.10/serverguide/lamp-applications.html)
[https://help.ubuntu.com/12.10/serverguide/web-servers.html](https://help.ubuntu.com/12.10/serverguide/web-servers.html)
[https://help.ubuntu.com/12.10/serverguide/email-services.html](https://help.ubuntu.com/12.10/serverguide/email-services.html)

squirrelmail guide from unixmen
[http://www.unixmen.com/install-squirrel-mail-on-ubuntu-server/](http://www.unixmen.com/install-squirrel-mail-on-ubuntu-server/)

---

