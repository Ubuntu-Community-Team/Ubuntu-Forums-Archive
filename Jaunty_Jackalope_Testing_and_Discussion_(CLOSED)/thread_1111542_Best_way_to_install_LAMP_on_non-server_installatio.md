---
title: "Best way to install LAMP on non-server installation of Jaunty?"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-03-30
Is there a better/easier way to install LAMP rather than installing mysql-server, apache2 and the other packages *separately*?

Is there a how-to for LAMP on Jaunty? Thanks.

UPDATE: I want to install Postfix too.

---

### Post by doogy2004 on 2009-03-30
give the following a try:
```
sudo tasksel
```

---

### Post by MountainX on 2009-03-30
> **doogy2004 said:**
> give the following a try:
```
sudo tasksel
```

is tasksel compatible with the package database maintained by apt-get?

Tasksel only gives me an option for "manual package selection" (other than the desktop-oriented stuff I already have installed). This looks confusing enough that I might just stick to apt-get and install each package separately... 

what would happen if I burn a server install CD and stick it in the cdrom drive? Will it give me an option for installing the server packages?

---

### Post by doogy2004 on 2009-03-30
tasksel uses apt-get to install the packages

---

### Post by MountainX on 2009-03-30
OK, so I fixed tasksel. There was an error in my file /etc/apt/apt.conf.d/10periodic.

Now I have options for a LAMP server and a Mail server. :)

BTW, I didn’t know about tasksel. Thanks for telling me about it. For other interested in what this is you can read more here: [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

But I'm still wondering if tasksel is compatible with apt-get. The link above makes me think it is, but I'd like to be sure.

---

### Post by MountainX on 2009-03-30
> **doogy2004 said:**
> tasksel uses apt-get to install the packages

Thank you. Looks like I'm ready to go now. :)

---

### Post by MountainX on 2009-03-30
tasksel: aptitude failed (100)

UPDATE: ok, got it resolved. I had accepted the suggested value for myhostname, but that was not a valid value. (So why was it suggested?) 

syslog was showing this error:

Mar 30 20:31:53 MyServer postfix/sendmail[15000]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: xxxxx.

I edited the file and fixed the value and ran tasksel again and it completed the install. 

Now to get postfix working with gmail (google apps), I'm going to be looking at these guides:

  	 	 	 	 	 	   [COLOR=#000080]_[[SIZE=2]http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps[/SIZE]]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps")_[/COLOR]
  [COLOR=#000080]_[[SIZE=2]http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/[/SIZE]]("http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/")_[/COLOR]
  [COLOR=#000080]_[[SIZE=2]http://flurdy.com/docs/postfix/#config-simple-mta[/SIZE]]("http://flurdy.com/docs/postfix/#config-simple-mta")_[/COLOR]

---

### Post by MountainX on 2009-03-30
I found a really good (simple) how-to for postfix & gmail here:
[https://calomel.org/postfix.html](https://calomel.org/postfix.html)

Mine is working.

---

