---
title: "No internet connection with dapper drake"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by MoxJet on 2006-06-05
I upgraded to Dapper yesterday and internet worked nicely, but after reboot I cannot get contact any longer. It's nothing wrong with the hardware on the computer, I can still reach internet from Windows XP. Any idea what could be wrong? Where can I get information about how to configure internet connections in ubuntu? 

Thanks in advance.

---

### Post by kryptosaint on 2006-06-05
Found the software and support @ [http://eciadsl.flashtux.org/modems.php](http://eciadsl.flashtux.org/modems.php) very helpful.

---

### Post by ouphe on 2006-06-05
My cable-provider requires my pc to send it's hostname in order to get an ip-adress. For some strange reason Ubu has removed the DHCP setup part from the installation menus. 

If this is the case, just do
```
sudo nano -w /etc/dhcp3/dhclient.conf
```

and uncomment and change the first configuration line:
```
send host-name "yourhostname";
```

The hostname should be the same as in Windows.

---

