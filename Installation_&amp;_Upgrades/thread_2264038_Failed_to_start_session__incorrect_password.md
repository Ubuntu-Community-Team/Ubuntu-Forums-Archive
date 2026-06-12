---
title: "Failed to start session / incorrect password"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by Michal_Dadk on 2015-02-05
Hi everyone, I need a help with Ubuntu 14.04. I can`t log in after start Ubuntu. There is always message "failed to start session", if i try to do somethink with the command as sudo....etc. there is also a message "incorrect password". 

the password is ok. What I can do?

> Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:41:06 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  4 22:41:14 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:41:14 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:41:14 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  4 22:46:36 dankaichal-Lenovo-C560 systemd-logind[622]: New seat seat0.
Feb  4 22:46:36 dankaichal-Lenovo-C560 systemd-logind[622]: Watching system buttons on /dev/input/event2 (Power Button)
Feb  4 22:46:36 dankaichal-Lenovo-C560 systemd-logind[622]: Watching system buttons on /dev/input/event0 (Power Button)
Feb  4 22:46:36 dankaichal-Lenovo-C560 systemd-logind[622]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb  4 22:46:39 dankaichal-Lenovo-C560 dbus[564]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1179 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=834 comm="NetworkManager ")
Feb  4 22:46:40 dankaichal-Lenovo-C560 systemd-logind[622]: Watching system buttons on /dev/input/event9 (Video Bus)
Feb  4 22:46:40 dankaichal-Lenovo-C560 systemd-logind[622]: Watching system buttons on /dev/input/event10 (Video Bus)
Feb  4 22:46:40 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:46:40 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:46:40 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  4 22:46:40 dankaichal-Lenovo-C560 systemd-logind[622]: New session c1 of user lightdm.
Feb  4 22:46:40 dankaichal-Lenovo-C560 systemd-logind[622]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Feb  4 22:46:40 dankaichal-Lenovo-C560 dbus[564]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1179 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=834 comm="NetworkManager ")
Feb  4 22:46:41 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:46:41 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:46:41 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  4 22:46:46 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:46:46 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:46:46 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  4 22:47:21 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:47:21 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:47:21 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  4 22:48:26 dankaichal-Lenovo-C560 login[1094]: pam_unix(login:auth): check pass; user unknown
Feb  4 22:48:26 dankaichal-Lenovo-C560 login[1094]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost= 
Feb  4 22:48:29 dankaichal-Lenovo-C560 login[1094]: FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN', Authentication failure
Feb  4 22:48:33 dankaichal-Lenovo-C560 systemd-logind[622]: Power key pressed.
Feb  4 22:48:33 dankaichal-Lenovo-C560 systemd-logind[622]: Powering Off...
Feb  4 22:48:33 dankaichal-Lenovo-C560 systemd-logind[622]: System is powering down.
Feb  4 22:48:33 dankaichal-Lenovo-C560 systemd-logind[622]: Operation finished.
Feb  4 22:49:09 dankaichal-Lenovo-C560 systemd-logind[630]: Watching system buttons on /dev/input/event2 (Power Button)
Feb  4 22:49:09 dankaichal-Lenovo-C560 systemd-logind[630]: Watching system buttons on /dev/input/event0 (Power Button)
Feb  4 22:49:09 dankaichal-Lenovo-C560 systemd-logind[630]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb  4 22:49:09 dankaichal-Lenovo-C560 systemd-logind[630]: New seat seat0.
Feb  4 22:49:10 dankaichal-Lenovo-C560 systemd-logind[630]: Watching system buttons on /dev/input/event11 (Video Bus)
Feb  4 22:49:10 dankaichal-Lenovo-C560 systemd-logind[630]: Watching system buttons on /dev/input/event12 (Video Bus)
Feb  4 22:49:11 dankaichal-Lenovo-C560 dbus[572]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1184 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=837 comm="NetworkManager ")
Feb  4 22:49:12 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  4 22:49:12 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  4 22:49:12 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  4 22:49:12 dankaichal-Lenovo-C560 systemd-logind[630]: New session c1 of user lightdm.
Feb  4 22:49:12 dankaichal-Lenovo-C560 systemd-logind[630]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Feb  4 22:49:12 dankaichal-Lenovo-C560 dbus[572]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1184 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=837 comm="NetworkManager ")
Feb  4 22:49:17 dankaichal-Lenovo-C560 systemd-logind[630]: System is rebooting.
Feb  5 05:51:02 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:51:02 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:51:02 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  5 05:51:05 dankaichal-Lenovo-C560 dbus[561]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.41" (uid=0 pid=1448 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=809 comm="NetworkManager ")
Feb  5 05:51:15 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:51:15 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:51:15 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:51:22 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:51:22 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:51:22 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:52:18 dankaichal-Lenovo-C560 login[933]: pam_unix(login:auth): check pass; user unknown
Feb  5 05:52:18 dankaichal-Lenovo-C560 login[933]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty3 ruser= rhost= 
Feb  5 05:52:22 dankaichal-Lenovo-C560 login[933]: FAILED LOGIN (1) on '/dev/tty3' FOR 'UNKNOWN', Authentication failure
Feb  5 05:51:05 dankaichal-Lenovo-C560 dbus[561]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.41" (uid=0 pid=1448 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=809 comm="NetworkManager ")
Feb  5 05:53:44 dankaichal-Lenovo-C560 systemd-logind[653]: Watching system buttons on /dev/input/event2 (Power Button)
Feb  5 05:53:44 dankaichal-Lenovo-C560 systemd-logind[653]: Watching system buttons on /dev/input/event0 (Power Button)
Feb  5 05:53:44 dankaichal-Lenovo-C560 systemd-logind[653]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb  5 05:53:44 dankaichal-Lenovo-C560 systemd-logind[653]: New seat seat0.
Feb  5 05:53:46 dankaichal-Lenovo-C560 systemd-logind[653]: Watching system buttons on /dev/input/event9 (Video Bus)
Feb  5 05:53:46 dankaichal-Lenovo-C560 systemd-logind[653]: Watching system buttons on /dev/input/event10 (Video Bus)
Feb  5 05:53:47 dankaichal-Lenovo-C560 dbus[588]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1158 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=847 comm="NetworkManager ")
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  5 05:53:48 dankaichal-Lenovo-C560 systemd-logind[653]: New session c1 of user lightdm.
Feb  5 05:53:48 dankaichal-Lenovo-C560 systemd-logind[653]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:53:48 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:53:48 dankaichal-Lenovo-C560 dbus[588]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1158 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=847 comm="NetworkManager ")
Feb  5 05:53:56 dankaichal-Lenovo-C560 systemd-logind[653]: System is rebooting.
Feb  5 05:54:16 dankaichal-Lenovo-C560 systemd-logind[640]: New seat seat0.
Feb  5 05:54:16 dankaichal-Lenovo-C560 systemd-logind[640]: Watching system buttons on /dev/input/event2 (Power Button)
Feb  5 05:54:16 dankaichal-Lenovo-C560 systemd-logind[640]: Watching system buttons on /dev/input/event0 (Power Button)
Feb  5 05:54:16 dankaichal-Lenovo-C560 systemd-logind[640]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb  5 05:54:19 dankaichal-Lenovo-C560 dbus[564]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1178 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=799 comm="NetworkManager ")
Feb  5 05:54:20 dankaichal-Lenovo-C560 systemd-logind[640]: Watching system buttons on /dev/input/event9 (Video Bus)
Feb  5 05:54:20 dankaichal-Lenovo-C560 systemd-logind[640]: Watching system buttons on /dev/input/event10 (Video Bus)
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  5 05:54:20 dankaichal-Lenovo-C560 systemd-logind[640]: New session c1 of user lightdm.
Feb  5 05:54:20 dankaichal-Lenovo-C560 systemd-logind[640]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Feb  5 05:54:20 dankaichal-Lenovo-C560 dbus[564]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1178 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=799 comm="NetworkManager ")
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:54:20 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:54:26 dankaichal-Lenovo-C560 systemd-logind[640]: System is rebooting.
Feb  5 05:54:26 dankaichal-Lenovo-C560 systemd-logind[640]: Operation finished.
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:54:51 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:54:51 dankaichal-Lenovo-C560 dbus[601]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.20" (uid=0 pid=1294 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=847 comm="NetworkManager ")
Feb  5 05:54:52 dankaichal-Lenovo-C560 dbus[601]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.20" (uid=0 pid=1294 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=847 comm="NetworkManager ")
Feb  5 05:55:20 dankaichal-Lenovo-C560 dbus[623]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1162 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=782 comm="NetworkManager ")
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:55:21 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:55:21 dankaichal-Lenovo-C560 dbus[623]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1162 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=782 comm="NetworkManager ")
Feb  5 05:55:35 dankaichal-Lenovo-C560 lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=dankaichal
Feb  5 05:55:37 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:55:37 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:55:37 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"
Feb  5 05:55:43 dankaichal-Lenovo-C560 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Feb  5 05:55:43 dankaichal-Lenovo-C560 lightdm: PAM adding faulty module: pam_kwallet.so
Feb  5 05:55:43 dankaichal-Lenovo-C560 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dankaichal"

---

### Post by ajgreeny on 2015-02-05
Has this always happened or is this a new install that will not start at the first reboot?

Are you sure about the password, which is case sensitive?

You could try resetting the password by following the info at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) but tell us first more about what has possibly caused this problem; if you have logged in previously, what might you have done to cause this problem.

Also hit Ctrl+Alt+F1 at the login screen and try to login to the command line using your username and what you think to be your password which will not show on screen but will be entered when you type, so type carefully and hit enter, then tell us what errors you see, if any, or if the command line allows you to login OK.

---

### Post by Michal_Dadk on 2015-02-05
It´s happening always, so I can´t log in to my desktop, only with the USB boot

I have only small letters in my password so I am sure about it

It is happening after I updated/upgraded Ubuntu. 
Also I installed, If I am sure 3 themes, after that there was also some failures (for example I couldn´t mark two or more folders/directories, if I did it the window closed spontaneously)

---

### Post by ajgreeny on 2015-02-05
Sounds like a bad update, if all was OK before that.

Can you log in OK at the command line as I suggested before?

---

### Post by Michal_Dadk on 2015-02-05
I tried the command but there is a message "login incorrect"

It is not possible to change the password according to your instructions (mount -o rw,remount / ). it didn't happen anythink, I mean there wasn't any next step)

---

### Post by ajgreeny on 2015-02-05
You will not see anything special happen after using that command at the command line; all it does is remount the filesystem as read/write instead of read only.  You then have to use the commands as shown in my link, ie.

 To reset the password, type 
**passwd *username***

 where *username* is the username you want to reset. In this case, your username 

  You'll then be prompted for a new password. When you type the password you will get [no visual response acknowledging your typing]("http://www.psychocats.net/ubuntu/passwordinterminal"). Your password is still being accepted. Just type the password and hit *Enter* when you're done. You'll be prompted to retype the password. Do so and hit *Enter* again. 
 Now the password should be reset. Type 
**exit**
 to return to the recovery menu. 
After you get back to the recovery menu, select *resume normal boot*, and use Ubuntu as you normally would—only this time, you actually know the password!

---

