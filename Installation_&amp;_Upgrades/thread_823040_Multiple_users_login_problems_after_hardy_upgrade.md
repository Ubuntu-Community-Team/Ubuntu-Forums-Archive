---
title: "Multiple users login problems after hardy upgrade"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Juan_VCS on 2008-06-08
I have a main user whos session I keep always open. Then I have a separate user for anyone else who wants to use the computer.

Since I upgraded to Hardy, whenever the separate user logs in after my user's session is locked, it comes to a point when that separate user automatically leaves its session, goes to the gdm screen, re-authenticates and continues with its session while mine is killed.

Here's the auth.log at the time the separate user logs in:

```
Jun  8 19:51:20 SYSTEMNAME gdm[17180]: pam_nologin(gdm:auth): cannot determine username
Jun  8 19:51:25 SYSTEMNAME gdm[17180]: pam_unix(gdm:session): session opened for user SECONDUSER by (uid=0)
Jun  8 20:07:06 SYSTEMNAME gdm[7478]: pam_unix(gdm:session): session closed for user FIRSTUSER
Jun  8 20:07:13 SYSTEMNAME gdm[17917]: pam_nologin(gdm:auth): cannot determine username
Jun  8 20:07:17 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): check pass; user unknown
Jun  8 20:07:17 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Jun  8 20:07:19 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): check pass; user unknown
Jun  8 20:07:19 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Jun  8 20:07:20 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): check pass; user unknown
Jun  8 20:07:20 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Jun  8 20:07:22 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): check pass; user unknown
Jun  8 20:07:22 SYSTEMNAME gdm[17917]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
# it keeps going until
# the separate user
# ends its session
```

Any clues on this?

---

### Post by Juan_VCS on 2008-06-14
I'm getting this in /var/log/syslog at the exact moment the first user crashes

```
WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

---

### Post by Juan_VCS on 2008-06-16
Seems like I fixed it by going to System -> Preferences -> Session -> Session Options and activating "Automatically remember running applications when logging out".
At least it's working fine for now.

Thanks to "beagle" on the #ubuntu-es IRC channel @ FreeNode for the suggestion.

---

### Post by Juan_VCS on 2008-06-17
...And yeah, it wasn't really fixed. Happened again. No one else has this problem?

---

### Post by Juan_VCS on 2008-06-25
I made a fresh install and it still happens! Come on, someone take a look at this.

---

### Post by Juan_VCS on 2008-07-01
Updated the nvidia video driver, installed all the updates from the backports... Still no luck.

---

### Post by Juan_VCS on 2008-07-08
It just happened to me even before loggin the second user in. I'm guessing there's something wrong with gdmflexiserver. I made a bug report, hopefully someone will help

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737)

---

