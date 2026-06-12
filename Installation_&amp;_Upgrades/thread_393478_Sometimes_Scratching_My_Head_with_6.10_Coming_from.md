---
title: "Sometimes Scratching My Head with 6.10 Coming from 5.10: DynDns &amp; Contab?"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-25
I have to wonder why I "upgraded" to 6.10 from 5.10.

If I recall, I was up and running within and hour or two with 5.10. I have taken a lot more time getting 6.10 to where I want it to be. Perhaps the documentation for 6.10 is lacking?

Case in point:

[U6.10: How to assign Hostname to local machine with dynamic IP using free DynDNS service]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service")

[U5.10: How to assign Hostname to local machine with dynamic IP using free DynDNS service ]("http://ubuntuguide.org/wiki/Ubuntu_si#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service")

There is a BIG difference between the above. In the second link you have:

[B]export EDITOR=gedit && sudo crontab -e

00 * * * * sudo sh /root/dyndns_update.sh[/B]

If I recall, the latter two lines allowed ipcheck to run hourly. 

I just purposefully released/renewed the connection on my router and waiting over an hour to see if Ubuntu would run ipcheck and "fix" the IP address but it did not.

Can I run the above two lines in 6.10 and get the same result as I did in 5.10?

---

### Post by Holzmann on 2007-03-25
I have the feeling I need to add:

**00 * * * * sudo sh /etc/ppp/ip-up.d/dyndns_update**

BUT I do not know where to add it.

Either to /etc/crontab or as some sort of new object (?) in /etc/cron.hourly ???

---

### Post by Holzmann on 2007-03-25
I simply did crontab -e and entered 

**00 * * * * sudo sh /etc/ppp/ip-up.d/dyndns_update**

I hope that does the trick.

---

### Post by Holzmann on 2007-03-25
Okay, that worked.

/Thread

---

