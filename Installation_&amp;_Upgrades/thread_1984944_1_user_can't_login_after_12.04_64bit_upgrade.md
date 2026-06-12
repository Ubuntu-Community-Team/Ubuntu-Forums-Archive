---
title: "1 user can't login after 12.04 64bit upgrade"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by donovanjf on 2012-05-22
I just upgraded to 12.04 Precise and after power cycling I can't login to my ID. A message flashes up on the screen too quickly to see, and I'm returned to the password prompt. I am currently logged into the the other admin account so I'm assuming there is something wrong with mine. Here is the auth.log entry for my (donovan) attempts:

```
May 22 14:22:05 BigDaddy lightdm: pam_succeed_if(lightdm:auth): 
requirement "user ingroup nopasswdlogin" not met by user "donovan"
May 22 14:22:06 BigDaddy dbus[1004]: [system] Rejected send message, 2 
matched rules; type="method_call", sender=":1.163" (uid=104 pid=4887 
comm="/usr/lib/indicator-datetime/indicator-datetime-ser") 
interface="org.freedesktop.DBus.Properties" member="GetAll" error
name="(unset)" requested_reply="0" destination=":1.19" (uid=0 pid=1737 
comm="/usr/sbin/console-kit-daemon --no-daemon ")
```What did I mess up or how can I login "minimal" to my ID?

---

### Post by angadsg on 2012-05-23
I have the same issue. Its a login loop and it seems like on startup, some application/script is trying to run sudo and has 3 incorrect password attempts.
It happened after I did a apt-get upgrade and rebooted. Something broke with the update.

Here is my auth.log

```
May 23 14:52:01 ubuntu-desktop lightdm: pam_unix(lightdm:session): session closed for user lightdm
May 23 14:52:02 ubuntu-desktop lightdm: pam_unix(lightdm:session): session opened for user angad by (uid=0)
May 23 14:52:02 ubuntu-desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): conversation failed
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [angad]
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): conversation failed
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [angad]
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): conversation failed
May 23 14:52:02 ubuntu-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [angad]
May 23 14:52:02 ubuntu-desktop sudo:    angad : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/angad ; USER=root ; COMMAND=/bin/bash
May 23 14:52:05 ubuntu-desktop lightdm: pam_unix(lightdm:session): session closed for user angad
May 23 14:52:06 ubuntu-desktop lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
May 23 14:52:06 ubuntu-desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
May 23 14:52:07 ubuntu-desktop lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "angad"
May 23 14:52:07 ubuntu-desktop dbus[936]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.166" (uid=104 pid=7935 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1426 comm="/usr/sbin/console-kit-daemon --no-daemon ")
```

---

