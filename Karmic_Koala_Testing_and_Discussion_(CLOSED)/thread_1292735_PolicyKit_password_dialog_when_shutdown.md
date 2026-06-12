---
title: "PolicyKit password dialog when shutdown"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dr_kabuto on 2009-10-16
Hi all,
before reporting a bug in LP, I post my problem here.
I get a password request from ConsoleKit everytime I shutdown my laptop. It say so because there is another user logged,  it's strange, since I'm the only one using the laptop, finger confirms so:

```
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
myUser  MyFullName            tty7       36  Oct 16 13:26 (:0)
myUser  MyFullName            pts/0      14  Oct 16 13:31 (:0.0)
myUser  MyFullName            pts/1          Oct 16 13:56 (:0.0)


```
Someone can tell me what's going on?

---

### Post by rburkartjo on 2009-10-16
everything fine on my end  i dont get the message unless my daughter is still logged on when i try to shut down

---

### Post by chrisccoulson on 2009-10-16
What is the output of "ck-list-sessions" before this happens?

---

### Post by dr_kabuto on 2009-10-19
HI Chris, sorry for the late response, just returned to work today. Here the output of ck-list-sessions:

```
Session1:
	unix-user = '121'
	realname = '(null)'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/???'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-10-19T06:36:52.097392Z'
	login-session-id = ''
Session4:
	unix-user = '1000'
	realname = 'MyFullName'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-10-19T06:37:36.632685Z'
	login-session-id = ''
```

Looking for user '121' in /etc/passwd i get this:

```
mythtv:x:121:129::/home/mythtv:/bin/sh
```

Seems that mythtv is the culprit, uninstalling it solve the problem. Should I file a bug report?

---

### Post by reviczky on 2009-10-19
It has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/445953](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/445953)

---

### Post by dr_kabuto on 2009-10-19
> **reviczky said:**
> It has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/445953](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/445953)

Thanks!

---

