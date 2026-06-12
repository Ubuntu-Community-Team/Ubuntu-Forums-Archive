---
title: "unable to login via lightdm"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by michael37 on 2013-10-15
I just upgraded from 12.04 to 13.04 (using do-release-upgrade, via 12.10).  Overall, the upgrade went pretty smoothly.

However, I can't login as my primary user anymore from the GUI lightdm prompt. The screen blinks, shows me the background, and restarts back into the lightdm login screen.

I can successfully login as my primary user from the text prompt (ctl-alt-F1), so I know that the username and password works fine, and the home dir mounts successfully.

X log shows nothing of particular interest. Lightdm log shows a successful beginning and completion of a session.

I can also successfully login as guest. I get a normal conventional unity session with nothing wrong.

Any ideas what could be going wrong with my primary user? 

I also installed Openbox just for testing, and tried login in into an Openbox session. Same result: unable to login.

---

### Post by michael37 on 2013-10-15
Look like I may have hit a bug [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1114418](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1114418)

---

### Post by michael37 on 2013-10-15
OK made some progress. I can login now.

I modified /etc/lightdm/ligthdm.conf to 
```

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
```

If you replace it with greeter-session=lightdm-greeter, then it will break.

I still see a bunch of errors such as "Session 1989 terminated with signal 15; Session 1989 failed during authentication", but someone it does let me log in afterwards.

```

$ sudo cat /var/log/lightdm/lightdm.log 
[+2.06s] DEBUG: Stopping Plymouth, X server is ready
[+2.11s] DEBUG: Connecting to XServer :0
[+2.11s] DEBUG: Starting greeter
[+2.11s] DEBUG: Started session 1415 with service 'lightdm-greeter', username 'lightdm'
[+2.95s] DEBUG: Session 1415 authentication complete with return value 0: Success
[+2.95s] DEBUG: Greeter authorized
[+2.95s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+2.96s] DEBUG: Session 1415 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+4.57s] DEBUG: Greeter connected version=1.6.0
[+4.57s] DEBUG: Greeter connected, display is ready
[+4.57s] DEBUG: New display ready, switching to it
[+4.57s] DEBUG: Activating VT 7
[+6.48s] DEBUG: Greeter start authentication for mike
[+6.48s] DEBUG: Started session 1989 with service 'lightdm', username 'mike'
[+6.49s] DEBUG: Session 1989 got 1 message(s) from PAM
[+6.49s] DEBUG: Prompt greeter with 1 message(s)
[+6.51s] DEBUG: Greeter start authentication for mike
[+6.51s] DEBUG: Session 1989: Sending SIGTERM
[+6.51s] DEBUG: Started session 1990 with service 'lightdm', username 'mike'
[+6.51s] DEBUG: Session 1989 terminated with signal 15
[+6.51s] DEBUG: Session 1989 failed during authentication
[+6.52s] DEBUG: Session 1990 got 1 message(s) from PAM
[+6.52s] DEBUG: Prompt greeter with 1 message(s)
[+9.87s] DEBUG: Continue authentication
[+10.35s] DEBUG: Session 1990 authentication complete with return value 0: Success
[+10.35s] DEBUG: Authenticate result for user mike: Success
[+10.37s] DEBUG: User mike authorized
[+10.38s] DEBUG: Greeter requests session cinnamon
[+10.38s] DEBUG: Using session cinnamon
[+10.38s] DEBUG: Stopping greeter
[+10.38s] DEBUG: Session 1415: Sending SIGTERM
[+10.40s] DEBUG: Greeter closed communication channel
[+10.40s] DEBUG: Session 1415 exited with return value 0
[+10.40s] DEBUG: Greeter quit

```

---

