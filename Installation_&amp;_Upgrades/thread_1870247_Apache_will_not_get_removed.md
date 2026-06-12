---
title: "Apache will not get removed"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by kensclark15 on 2011-10-26
I ran the command to purge it plus deleted all of the related packages in Synaptic and when I type in [http://localhost](http://localhost) it still has the default page for apache.
Here is the order I did it in:
Removed everything in Synaptic.
Ran apt-get remove apache2 apache2.2-bin apache2.2-common
Ran apt-get autoremove.

Do I have to restart the computer to complete the removal?

---

### Post by agillator on 2011-10-27
The short answer is probably. Your purge may have removed files but not stopped the running daemon. Assuming you are running apache2, see if /etc/init.d/apache2 exists. If so, run sudo /etc/init.d/apache2 stop. It should stop the daemon. Then remove that file and any reference to apache2 in the rcx.d directories (x = 1 through 6). Then a reboot, or if it isn't there a reboot, will not restart apache. You MAY still have files lying around (purges never get everything for me it seems) but that shouldn't matter although you could do a find and remove them carefully - you never know what requires what, you can screw things up very easily by just removing files willy nilly. But, apache will no longer be running.

---

### Post by MAFoElffen on 2011-10-27
> **kensclark15 said:**
> I ran the command to purge it plus deleted all of the related packages in Synaptic and when I type in [http://localhost](http://localhost) it still has the default page for apache.
Here is the order I did it in:
Removed everything in Synaptic.
Ran apt-get remove apache2 apache2.2-bin apache2.2-common
Ran apt-get autoremove.

Do I have to restart the computer to complete the removal?
Actually... You missed a step.  You didn't shutdown Apache2 before you did that so some of the files should have been locked (and where not removed.)

If previos to 11.04, try
```

sudo /etc/init.d/apache2 stop

```If 11.04 or newer, use
```

sudo service apache2 stop

```Then 
```

sudo apt-get remove --purge apache2-*

```Reboot and test.

---

### Post by reqqq on 2011-10-30
plz i need some help with apache2 
i tried to remove apache2 from my system 11.04 
i removed it usin[FONT=Verdana]g all the code i found 
[/FONT]sudo apt-get remove --purge apache2-*and reinstalled it with 

sudo aptitude purge apache2-common
sudo aptitude install apache2
also installed it again with only apt-get install apache2 and again the same
 the point is that i did something i found in a tutorial and changed in /etc/hosts
127.0.0.1 localhost 
i changed the localhost  with installapache2 [www.something.info]("http://www.something.info") installapache2
and in /etc/apache2/sites-available/default
i wrote a new line ServerName [www.something.info]("http://www.xxxxxxx.info")
the point is that i did it again and i wrote as the above [www.myserver.info]("http://www.myserver.info") and removed it again 
and now i removed it again and when i type server.info in browser(lan and pc i had the server) i see the empty index of server besides i removed it 
i think that this is by chance and server.info is the common link for server info for everyone am i right????
also i have a problem i cannot see my server on my lan computers ( i mean typing the ip in my lan pc and  say  It works ) what could be the problem ? i tried with another linux machine and typing my ip in lan computers seems to be ok (It works ) with firewalls everything -something might be with the configuration but what?
i have to mention that before all this my server was working with no problem without do anything after installin apache -i think afte some updates this problems happens 

sorry for questions but i am not so familiar with apache yet  :)

---

### Post by reqqq on 2011-10-31
> **reqqq said:**
> plz i need some help with apache2 
i tried to remove apache2 from my system 11.04 
i removed it usin[FONT=Verdana]g all the code i found 
[/FONT]sudo apt-get remove --purge apache2-*and reinstalled it with 

sudo aptitude purge apache2-common
sudo aptitude install apache2
also installed it again with only apt-get install apache2 and again the same
 the point is that i did something i found in a tutorial and changed in /etc/hosts
127.0.0.1 localhost 
i changed the localhost  with installapache2 [www.something.info]("http://www.something.info") installapache2
and in /etc/apache2/sites-available/default
i wrote a new line ServerName [www.something.info]("http://www.xxxxxxx.info")
the point is that i did it again and i wrote as the above [www.myserver.info]("http://www.myserver.info") and removed it again 
and now i removed it again and when i type server.info in browser(lan and pc i had the server) i see the empty index of server besides i removed it 
i think that this is by chance and server.info is the common link for server info for everyone am i right????
also i have a problem i cannot see my server on my lan computers ( i mean typing the ip in my lan pc and  say  It works ) what could be the problem ? i tried with another linux machine and typing my ip in lan computers seems to be ok (It works ) with firewalls everything -something might be with the configuration but what?
i have to mention that before all this my server was working with no problem without do anything after installin apache -i think afte some updates this problems happens 

sorry for questions but i am not so familiar with apache yet  :)


any help somebody?
thanks

---

