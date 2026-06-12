---
title: "tasksel install lamp-server --- hangs at the end on &quot;installed php5-mysql&quot; ???"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by aktxyz on 2007-12-03
I am ssh'd in over a network trying to setup lampp, I did...

sudo tasksel install lamp-server
answered the mysql password question
the setup hit 100% after about 5 minutes

but now it's been sitting at 100% "installed php5-mysql" for about 30 minutes !

any log I can check?
it looks like the install is done (mysql running, can login, etc)
any ideas??? 

thanks a bunch!

---

### Post by Evgeni Sergeev on 2008-02-08
Same here. Exactly. So I tried

```
es@mahkron:~$ ps -a
  PID TTY          TIME CMD
 8063 pts/1    00:00:00 tasksel
 8073 pts/1    00:00:00 frontend
 8079 pts/1    00:00:00 debconf-apt-pro
 8082 pts/1    00:00:01 apt-get <defunct>
 8115 pts/1    00:00:00 whiptail
 9029 pts/0    00:00:00 ps
es@mahkron:~$ sudo kill -9 8082
```

But it didn't kill it! Look, it's still there:
```

es@mahkron:~$ ps -a
  PID TTY          TIME CMD
 8063 pts/1    00:00:00 tasksel
 8073 pts/1    00:00:00 frontend
 8079 pts/1    00:00:00 debconf-apt-pro
 8082 pts/1    00:00:01 apt-get <defunct>
 8115 pts/1    00:00:00 whiptail
 9032 pts/0    00:00:00 ps
```

So I killed tasksel first and then apt-get.

Is this the correct behaviour for tasksel? Should it rather let the user exit normally?

---

### Post by Evgeni Sergeev on 2008-02-08
Update: had to restart apache2 manually to see phpinfo.php being processed. Without restarting, it asked whether I wanted to download and save the file.

Perhaps tasksel was stuck doing that?

---

### Post by Evgeni Sergeev on 2008-02-08
Now I tried to install phpMyAdmin and it said:
```
es@mahkron:/var/www$ sudo aptitude install phpmyadmin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

That must be because I had to kill tasksel.

---

### Post by deejross on 2008-04-03
I am currently having the same problem. I read somewhere that someone left it running overnight and it finally finished. Is this true or is there a workaround for this problem?

Also, Evgeni Sergeev, you said you killed the tasksel and apt-get processes. Have you noticed any problems with the lamp installation after killing them?

Thanks, Ross

---

### Post by deejross on 2008-04-03
I found that if open another terminal and restart apache2, the install will finish.

---

