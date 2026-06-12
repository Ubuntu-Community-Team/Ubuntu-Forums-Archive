---
title: "apt-listchanges and gconf"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-14
Hi all, 
 I got this error and hence filed bug [lpbug]317340[/lpbug]

How to get this. 

install apt-listchanges using aptitude/apt-get or synaptic. 

Then do

```
$ sudo dpkg-reconfigure apt-listchanges
```

Select the following things :-

1. Select xterm-pager as front-end
2. e-mail address (remain as root or whatever is needed)
3. Say yes to confirmation to move ahead (meaning apt-listchanges need a confirmation before doing progressing ahead)
4. say yes to saving previous changes in a database so everytime you don't have to look at the whole change from the beginning. 
5. say both when asked whether one wants to view changelogs or news . 

with this your /etc/apt/listchanges.conf should look like this :-

```


$ cat /etc/apt/listchanges.conf
[apt]
frontend=xterm-pager
email_address=root
confirm=1
save_seen=/var/lib/apt/listchanges.db
which=both

```

Now run an update/upgrade and I got the traceback as given in the bug. 

Can anybody triage the same?

---

