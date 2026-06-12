---
title: "Fix Apache 2?"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by distorted on 2010-10-18
Hello guys/women,
[SIZE=1][B]
Install LAMP as Web Server (Linux+Apache+MySQL+PHP)
[/B][/SIZE][http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A)
[B][SIZE=1]I'm stuck at:
[/SIZE][/B]

[SIZE=1]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
I got the apache[/SIZE]2 on my computer, but an error on the website. 

[http://localhost/phpmyadmin/:](http://localhost/phpmyadmin/:)
**Not Found**

 The requested URL /phpmyadmin/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80
What's the problem, now?

---

### Post by Barriehie on 2010-10-18
> **distorted said:**
> Hello guys/women,
[SIZE=1][B]
Install LAMP as Web Server (Linux+Apache+MySQL+PHP)
[/B][/SIZE][http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A)
[B][SIZE=1]I'm stuck at:
[/SIZE][/B]

[SIZE=1]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
I got the apache[/SIZE]2 on my computer, but an error on the website. 

[http://localhost/phpmyadmin/:](http://localhost/phpmyadmin/:)
**Not Found**

 The requested URL /phpmyadmin/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80
What's the problem, now?

[help.ubuntu.com](help.ubuntu.com) might be a better help source than youtube.  Did you enable phpmyadmin in apache?
```

Include /etc/phpmyadmin/apache.conf
```

[https://help.ubuntu.com/community/ApacheMySQLPHP#Edit Apache Configuration](https://help.ubuntu.com/community/ApacheMySQLPHP#Edit Apache Configuration)

---

### Post by distorted on 2010-10-18
Thanks for the quick response. I will go to the site.

---

### Post by Barriehie on 2010-10-19
> **distorted said:**
> Thanks for the quick response. I will go to the site.

Maybe try adding the Include line to the bottom of your apache2.conf file and then restart and see if phpmyadmin comes up; could be quicker. :)

---

### Post by crichard on 2010-10-19
> **distorted said:**
> Hello guys/women,
[SIZE=1][B]
Install LAMP as Web Server (Linux+Apache+MySQL+PHP)
[/B][/SIZE][http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A)
[B][SIZE=1]I'm stuck at:
[/SIZE][/B]

[SIZE=1]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
I got the apache[/SIZE]2 on my computer, but an error on the website. 

[http://localhost/phpmyadmin/:](http://localhost/phpmyadmin/:)
**Not Found**

 The requested URL /phpmyadmin/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at localhost Port 80
What's the problem, now?

FYI, the URL you pointed is incorrect, remove the colon which is at the last

Try this [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by distorted on 2010-10-19
Hello,

I restarted my computer, this showed up:
```

sudo apt-get install apache2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I'm a newbie on this. Help me, please.

---

### Post by Barriehie on 2010-10-20
> **distorted said:**
> Hello,

I restarted my computer, this showed up:
```

sudo apt-get install apache2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I'm a newbie on this. Help me, please.

When did this show up? This looks like more than one package manager running at a time.  Perhaps synaptic in a gui and you at the terminal?

---

### Post by distorted on 2010-10-20
Yes, I'm in the terminal. I'm figuring out all the ubuntu buttons. ex: Ctrl+Alt+Del is on Windows XP/Vista/7 for Task Manager. What is the ubuntu button(s) for all the current programs?

---

### Post by Barriehie on 2010-10-20
> **distorted said:**
> Yes, I'm in the terminal. I'm figuring out all the ubuntu buttons. ex: Ctrl+Alt+Del is on Windows XP/Vista/7 for Task Manager. What is the ubuntu button(s) for all the current programs?

That would be the **ps** command first comes to mind.  It looks like this:
```

$ >ps
  PID TTY          TIME CMD
 4487 ?        00:00:00 gnome-session
 4534 ?        00:00:00 ssh-agent
 4537 ?        00:00:00 dbus-launch
 4538 ?        00:00:00 dbus-daemon

```

You can take the output of ps and pass it to grep to find a specific job.
In this case I'm telling it to find all jobs by user barrie and then 'grepping' the output to find only the ones with vim in the output.  grep uses [regular expressions](http://www.regular-expressions.info/tutorial.html) and if you perservere with this you will come to like them!
```
> ps -u barrie | grep vim
 5966 ?        00:00:00 vim
 5974 ?        00:00:00 vim
 5979 ?        00:00:00 vim
10:03:27 /home/barrie/tmp $ >>
```

This will find all jobs launched by root that are the gnome display manager.
```

10:05:55 /home/barrie/tmp $ >> ps aux | grep -E ^root.*gdm$
root      4310  0.0  0.0 121196  1920 ?        Ss   16:48   0:00 /usr/sbin/gdm
root      4316  0.0  0.1 131860  3300 ?        S    16:48   0:00 /usr/sbin/gdm
10:06:54 /home/barrie/tmp $ >>

```

There's a gui for it also. gnome-system-manager

There's also ```
top
```

ctrl-alt-arrow moves between desktops; these are settable.

alt-tab switches between process'; in FF ctrl-tab switches between open tabs.

You will come to like the terminal!  :)

Barrie

---

### Post by Barriehie on 2010-10-20
In regards to terminals there are many out there. I like to use mrxvt.

---

