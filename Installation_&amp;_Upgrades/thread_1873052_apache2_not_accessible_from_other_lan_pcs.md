---
title: "apache2 not accessible from other lan pcs"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by reqqq on 2011-10-31
if it is possible a moderator delete the same  post i did again here 
[http://ubuntuforums.org/showthread.php?t=1870247](http://ubuntuforums.org/showthread.php?t=1870247)


plz i need some help with apache2 
i tried to remove apache2 from my system 11.04 
i removed it usin[FONT=Verdana]g all the code i found 
[/FONT]sudo apt-get remove --purge apache2-*and reinstalled it with 

sudo aptitude purge apache2-common
sudo aptitude install apache2
also installed it again with only apt-get install apache2 and again the same
 the point is that i did something i found in a tutorial and changed in /etc/hosts
127.0.0.1 localhost 
i changed the localhost  with installapache2 [www.something.info]("http://www.something.info/") installapache2
and in /etc/apache2/sites-available/default
i wrote a new line ServerName [www.something.info]("http://www.xxxxxxx.info/")
the point is that i did it again and i wrote as the above [www.myserver.info]("http://www.myserver.info/") and removed it again 
and now i removed it again and when i type server.info in browser(lan  and pc i had the server) i see the empty index of server besides i  removed it 
i think that this is by chance and server.info is the common link for server info for everyone am i right????
also i have a problem i cannot see my server on my lan computers ( i  mean typing the ip in my lan pc and  say  It works ) what could be the  problem ? i tried with another linux machine and typing my ip in lan  computers seems to be ok (It works ) with firewalls everything  -something might be with the configuration but what?
i have to mention that before all this my server was working with no  problem without do anything after installin apache -i think afte some  updates this problems happens 

sorry for questions but i am not so familiar with apache yet  :smile:

---

### Post by reqqq on 2011-11-01
> **reqqq said:**
> if it is possible a moderator delete the same  post i did again here 
[http://ubuntuforums.org/showthread.php?t=1870247](http://ubuntuforums.org/showthread.php?t=1870247)


plz i need some help with apache2 
i tried to remove apache2 from my system 11.04 
i removed it usin[FONT=Verdana]g all the code i found 
[/FONT]sudo apt-get remove --purge apache2-*and reinstalled it with 

sudo aptitude purge apache2-common
sudo aptitude install apache2
also installed it again with only apt-get install apache2 and again the same
 the point is that i did something i found in a tutorial and changed in /etc/hosts
127.0.0.1 localhost 
i changed the localhost  with installapache2 [www.something.info]("http://www.something.info/") installapache2
and in /etc/apache2/sites-available/default
i wrote a new line ServerName [www.something.info]("http://www.xxxxxxx.info/")
the point is that i did it again and i wrote as the above [www.myserver.info]("http://www.myserver.info/") and removed it again 
and now i removed it again and when i type server.info in browser(lan  and pc i had the server) i see the empty index of server besides i  removed it 
i think that this is by chance and server.info is the common link for server info for everyone am i right????
also i have a problem i cannot see my server on my lan computers ( i  mean typing the ip in my lan pc and  say  It works ) what could be the  problem ? i tried with another linux machine and typing my ip in lan  computers seems to be ok (It works ) with firewalls everything  -something might be with the configuration but what?
i have to mention that before all this my server was working with no  problem without do anything after installin apache -i think afte some  updates this problems happens 

sorry for questions but i am not so familiar with apache yet  :smile:


idea somebody?
to make it clear i need something to try,any solution, why my server cannot load on lan computers by typing the server ip 
of course if someone has some answer in all these i say above that make me confused for some thimngs or something to read about plz let me know
thanks

---

### Post by reqqq on 2011-11-04
well ok i got the problem was due to ufw rules
but i have another question now
when ufw is enable with no rules i cannot access server from my other win pc 
when i set rule to allow port 80 i can access server to my other pc 
well if i set etc sudo ufw allow tcp/80 i have acces from my other pc 
is this rule right or i may have other problems?
thanks

---

