---
title: "Text login works, graphical doesn't after installing with existing /home"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by superian on 2014-04-25
I have a happily working Linux Mint 16 MATE 32-bit system with /home on its own partition.

I have put Xubuntu 14.04 64-bit on another partition, and told it to use the existing /home partition.

When I boot into LM16, it stays working.

When I boot into Xubuntu, I can use Alt-F2 to get a text login and see that everything looks ok, but if I use the graphical login, it accepts the password, but returns to the login screen after a second or two.

I have tried installing MATE in Xubuntu via the text login, but that doesn't help.

Before I can switch to Xubuntu, I would like to ensure that I can use the existing /home .. Suggestions?

---

### Post by steeldriver on 2014-04-25
Are the UIDs and primary GIDs the same for the 2 systems (Mint and Xubuntu)? Otherwise you are going to have issues sharing home directories since the ownership won't carry over

In fact you will likely have *some* issues even if the UIDs and GIDs are the same - you might want to have separate minimal /home directories in each system's / and then symlink or bindmount the various subdirectories (Documents, Pictures etc.) from the "home" partition

---

### Post by superian on 2014-04-25
I'll have a look, but yes, I think they are - if I use the text login, the files appear as mine.

I was wondering about doing it that way. Hmm.

---

### Post by jacobmar1ey on 2014-04-25
Iis there anything in your ~/.xsession-errors?

---

### Post by superian on 2014-04-26
Nothing at all gets written to .xsession-errors

/var/log/auth.log has some interesting info though...

```
Apr 26 12:39:48 zoo systemd-logind[874]: New seat seat0.
Apr 26 12:39:48 zoo systemd-logind[874]: Watching system buttons on /dev/input/event1 (Power Button)
Apr 26 12:39:48 zoo systemd-logind[874]: Watching system buttons on /dev/input/event0 (Power Button)
Apr 26 12:39:49 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:39:49 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:39:49 zoo lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 26 12:39:49 zoo systemd-logind[874]: New session c1 of user lightdm.
Apr 26 12:39:49 zoo systemd-logind[874]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Apr 26 12:39:49 zoo lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 12:39:50 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:39:50 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:39:50 zoo lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ian"
Apr 26 12:39:52 zoo dbus[745]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.28" (uid=0 pid=1572 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=986 comm="NetworkManager ")
Apr 26 12:39:57 zoo lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 26 12:39:57 zoo lightdm: pam_unix(lightdm:session): session opened for user ian by (uid=0)
Apr 26 12:39:57 zoo systemd-logind[874]: New session c2 of user ian.
Apr 26 12:39:57 zoo systemd-logind[874]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Apr 26 12:39:57 zoo lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 12:39:57 zoo systemd-logind[874]: Removed session c2.
Apr 26 12:39:57 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:39:57 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:39:57 zoo lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 26 12:39:57 zoo systemd-logind[874]: New session c3 of user lightdm.
Apr 26 12:39:57 zoo lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 12:39:57 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:39:57 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:39:57 zoo lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ian"
Apr 26 12:40:07 zoo login[936]: pam_unix(login:session): session opened for user ian by LOGIN(uid=0)
Apr 26 12:40:07 zoo systemd-logind[874]: New session c4 of user ian.
Apr 26 12:41:54 zoo lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 26 12:41:54 zoo lightdm: pam_unix(lightdm:session): session opened for user ian by (uid=0)
Apr 26 12:41:54 zoo systemd-logind[874]: New session c5 of user ian.
Apr 26 12:41:54 zoo systemd-logind[874]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Apr 26 12:41:54 zoo lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 12:41:54 zoo systemd-logind[874]: Removed session c3.
Apr 26 12:41:54 zoo systemd-logind[874]: Removed session c5.
Apr 26 12:41:54 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:41:54 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:41:54 zoo lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 26 12:41:54 zoo systemd-logind[874]: New session c6 of user lightdm.
Apr 26 12:41:54 zoo lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Apr 26 12:41:54 zoo lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 26 12:41:54 zoo lightdm: PAM adding faulty module: pam_kwallet.so
Apr 26 12:41:54 zoo lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ian"
```

---

