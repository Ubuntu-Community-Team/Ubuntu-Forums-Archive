---
title: "router configuration d-link dsl-g604t"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by brianmay1984 on 2005-06-26
hi I'm one the new linux users and as soon as i've seen ubuntu i decided that i had to convert to it. During the installation i had no problem but when i tried to connect to internet i couldn't do it. To connect to internet i have a d-link dsl-g604t  wireless router. A friend of mine told me that i had to configure the dhcp on  my ethernet card and i did it; then told me to check the **ifconfig.conf** file and see if there were the program lines 

iface eth0 .....inet dhcp.         

Guess what? Those lines were there. so now i'm 
desperate because i don't know what to do anymore. CAN anyone that had my problem or knows the solution or that has just mercy of me HELP ME? please! ](*,)

---

### Post by manicka on 2005-06-26
> **brianmay1984]hi I'm one the new linux users and as soon as i've seen ubuntu i decided that i had to convert to it. During the installation i had no problem but when i tried to connect to internet i couldn't do it. To connect to internet i have a d-link dsl-g604t  wireless router. A friend of mine told me that i had to configure the dhcp on  my ethernet card and i did it said:**
> (*,)
 I have the same router and it doesn't handle the dns name servers properly. It will try to use the router's gateway address instead of your providers dns server. Enter the dns server information manually into the networking CP. Administration ---> Networking

I also think about setting up  all my settings manually if you only have a couple of machines connected to the router. If you enter them correctly then you'll know that they should always work. Most of the information you'll need  is available from the router's webmin interface.

HTH

---

### Post by brianmay1984 on 2005-06-26
[QUOTE=manicka]I have the same router and it doesn't handle the dns name servers properly. It will try to use the router's gateway address instead of your providers dns server. Enter the dns server information manually into the networking CP. Administration ---> Networking

I also think about setting up  all my settings manually if you only have a couple of machines connected to the router. If you enter them correctly then you'll know that they should always work. Most of the information you'll need  is available from the router's webmin interface.

HTH[/QUOTE]

thanx man! \\:D/  Hope that with this it'll work....  \\:D/

---

