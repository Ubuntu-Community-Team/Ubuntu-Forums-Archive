---
title: "How to upgrade behind company firewall"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by hogihung on 2006-06-22
[edit: I meant to put How to Install packages behind company firewall for subject.]

Hello,

First off I'm new to ubuntu (and linux in general.)  So I'm sure my questions will come off as very "basic" to many.  My apologies in advance.

At my work we are retiring many SUN boxes and our SUN/Linux guy has already left.  I have a set of applications that I need to move to a Linux solution.  I've chosen Ubuntu since it seems to be very stable and easy for me to handle.

I am using MON to monitor our network (routers/switches/servers).  I also require the following to complete my solution:
1.  mon
2.  mon-cgi
3.  PHP5
4.  Apache2
5.  MySQL (5.xx)
6.  phpMyAdmin
7.  TFTP (client and server)
8.  SHH (client and server)
9.  NTP (client)

I may have forgotten something.  My problem is I cannot seem to access the repositories through our firewalls.  Using our proxy in Firefox I can get around.  Pinging outside the company is restricted.  I've tried editing my /etc/apt/apt.conf file and inserting our proxy server info but that has not worked.

So I built an Ubuntu box at home.  I then went thru using Synaptic Package Manager to pick my applications but choose to download files only.  I copied the files from /var/cache/apt/archives to my home server and burnt a CD to bring to work.

This seemed to work fine at the beginning other than it took a long time and I had to figure out how to remove a couple packages because they were incompatible with another application (ie. first installed apache2 but when I went to install PHP5 there were issues.)

At that point I had only installed mon, mon-cgi, apache2, php5 and mysql.  But now I need to add more applications (see my list above.)  Is there a better way for me to do what I need to do?  This morning I burnt phpmyadmin to a CD and tried to install but I keep getting warnings - "Same version is available in software channel" and "Install unathenticated software?"  I tell it yes, but it won't install.

Sorry I went on so long, just wanted to accurately describe my scenario.  The best solution I would think would be to get access through the firewall.  If anyone has some ideas, I'd give them a shot.  If that can't be done, is there a better way to make a CD of exaclty what I need and how?

Thanks in advance,

Ho...

---

### Post by mips on 2006-06-22
How does your company firewall work ? Does it grant access to anyone via proxy or only those with username and password ???

You will have to configure Ubuntu to connect to the internet via proxy and not directly. I use Kubuntu and don't know where to do it in Ubunty but somewhere there should be an option (network settings ?) to configure the proxy settings.

I'm not familair with MON, [http://www.kernel.org/software/mon/](http://www.kernel.org/software/mon/)
All the other stuff you listed can basically be found in Synaptic.

Those old SUN boxes would make nice Ubuntu machines. There is a SPARC/SUN port of Ubuntu available if you are interested.

---

### Post by hogihung on 2006-06-22
Thanks for the reply.  Our proxies do not require a login/password.  When I plug in my Mac laptop I can get on the internet with no problems as long as I remember to have the company proxies settings turned on.

Ho...

ps.  The company won't let us use the old sparc equipment.  They sell it for pennies on the dollar to a salvager.  :(

---

### Post by mips on 2006-06-22
Go to System->Preferences->Proxy settings

If I was you I would offer the company money for those sparc boxes.

---

### Post by hogihung on 2006-06-22
Well I feel pretty stupid now.  I went back where you suggested to Network Proxy.  But this time I choose manual proxy instead of the Automatic Proxy Configuration.  And it is working!

Thanks so much for pointing me back in the right direction.

Ho...

---

