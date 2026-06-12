---
title: "https not working"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by nabilmalik on 2006-12-15
I have been using Drapper (Ubuntu 6.06) for the last 2 months. All this time, I was not able to access web sites that require the secure https connection including gmail and others.. However, http works perfectly fine.

I installed another web browser named Opera, and it also cannot access https sites. Also, Gaim (messanger software) doesn't let me connect to the msn messanger service. Perhaps that also requires the use of https.

However, when I installed kubuntu package for KDE, the KDE web brower 'Konqueror' can access https websites. But Firefox and Opera still cannot access https, even when I am using KDE as my windowmanager. Additionally, KDE specific messanger (forgot the name) also works very well..

I have been searching the Internet for a solution but failed to come across any. Only yesterday i went for a fresh reinstall of ubuntu 6.06, and was hoping that the problem would dissapper, but i was wrong..

Any help will be very appreciated, as I don't want to move back to MS Windows.

Thanks,

-Nabil.

---

### Post by nabilmalik on 2006-12-15
I have been using Drapper (Ubuntu 6.06) for the last 2 months. All this time, I was not able to access web sites that require the secure https connection including gmail and others.. However, http works perfectly fine.

I installed another web browser named Opera, and it also cannot access https sites. Also, Gaim (messanger software) doesn't let me connect to the msn messanger service. Perhaps that also requires the use of https.

However, when I installed kubuntu package for KDE, the KDE web brower 'Konqueror' can access https websites. But Firefox and Opera still cannot access https, even when I am using KDE as my windowmanager. Additionally, KDE specific messanger (forgot the name) also works very well..

I have been searching the Internet for a solution but failed to come across any. Only yesterday i went for a fresh reinstall of ubuntu 6.06, and was hoping that the problem would dissapper, but i was wrong..

Any help will be very appreciated, as I don't want to move back to MS Windows.

Thanks,

-Nabil.

---

### Post by wieman01 on 2006-12-15
I could only imagine that you are behind some kind of firewall. But you are saying that this is a fresh Ubuntu install and other computers can access HTTPS without problems, right?

---

### Post by budgie9 on 2006-12-15
This may be a wild guess but I would think that you may have a firewall problem. https uses a different port to http. 80 and 443 respectivly. MSN Messenger is 1863 
Here is a useful list of ports  [http://www.chebucto.ns.ca/~rakerman/port-table.html](http://www.chebucto.ns.ca/~rakerman/port-table.html)
If one program is accessing the port that may be known by the firewall, where as Firefox and certainly the far better Opera may not be so.

If this does not help, I hope thaere is someone else willing to give it a shot.

---

### Post by wieman01 on 2006-12-16
Damn it... Have just realized that I am having the same problem. Firewall is down, port 443 is open, port 80 is fine. But I cannot access any HTTPS sites at all. Odd!

_**EDIT 1:**_
It worked until two days ago. Strange thing... Have not changed a thing in the meantime.


_**EDIT 2:**_
Both Konqueror & Firefox have the same problem. All HTTPS requests bounce.

---

### Post by nabilmalik on 2006-12-16
All computers on my network are able to access https. Even my computer is able to access https when I use koquerer or MS Windows XP (both firefox and IE). I am not running any host based firewall and all iptable entires are clear.. Sooo wierd!

Where are all the linux gurus?? We need your help please..

-Nabil.

---

### Post by nabilmalik on 2006-12-16
All computers on my network are able to access https. Even my computer is able to access https when I use koquerer or MS Windows XP (both firefox and IE). I am not running any host based firewall and all iptable entires are clear.. Sooo wierd!

Where are all the linux gurus?? We need your help please..

-Nabil.

---

### Post by nabilmalik on 2006-12-16
ok, dcstar asked me to check if disabling ipv6 helps... I searched how to do it and every thing now works.. Please refer to the following post for disabling ipv6.

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Not that if you are using Drapper, please go ahead couple of pages for specific instructions for draper.. On second thought, i will past it here::

>>>>>>>>>>>>>>
In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in  /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).
<<<<<<<<<<<<<<

Thanks to all..!

-Nabil.

---

### Post by wieman01 on 2006-12-16
I have disabled IPV6 long ago for it may have serious impact on network performance. Funny thing is, today it seems to work. Not sure what the problem was but taking a break and not worrying about it did the job. ;-) Anyway, glad we both have eventually found a solution our way. :-)

---

### Post by cudjoe on 2007-01-26
I guess it is better to disable it on applications.

Look at about:config in Firefox, and filter on IPV6.
You can disable it, it solved my problems !

---

