---
title: "Unable to login after completing latest ubuntu 12.04 software update"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by jokemach on 2012-06-14
Hi,

After completing the latest software update for Ubuntu 12.04 (on a Dell XPS 13 Ultrabook) I was asked to reboot the system to complete the update process. Once rebooted I'm unable to login, the following message quickly flashed by as soon as I tried to login before throwing me back to the login screen:

-----
"Loading the sep3_8 driver:
Warning: sep3_4 driver "sep3_4-x32_64-3.2.0-25-genericsmp.ko" was not found in directory "."!
This means you may need to build sep3_4 driver from the provided driver sources. Please see the driver README for instructions."
-----
I'm not sure what the update process installed, google doesn't seem to provide any useful info either. 
Is this possible to fix this problem? or perhaps revert back to the state before the update?

Thanks

---

### Post by jokemach on 2012-06-14
The ser driver seems to have been added when I installed Intel VTune. But even uninstalling this application didn't help.
 
/var/log/lightdm/lightdm.log inclues:
------
[+6.26s] DEBUG: Greeter start authentication for jacob
[+6.26s] DEBUG: Started session 3015 with service 'lightdm', username 'jacob'
[+6.27s] DEBUG: Session 3015 got 1 message(s) from PAM
[+6.27s] DEBUG: Prompt greeter with 1 message(s)
[+10.12s] DEBUG: Greeter start authentication for guest account
[+10.12s] DEBUG: Session 3015: Sending SIGTERM
[+11.39s] DEBUG: Greeter requests default session
[+11.39s] DEBUG: Stopping greeter
[+11.39s] DEBUG: Session 2941: Sending SIGTERM
[+11.45s] DEBUG: Session 2941 exited with return value 0
[+11.45s] DEBUG: Greeter quit
------

I'm also seeing this in /var/log/auth.log:
------
Jun 14 18:14:08 jacob-laptop-w lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jun 14 18:14:08 jacob-laptop-w lightdm: pam_unix(lightdm:session): session opened for user jacob by (uid=0)
Jun 14 18:14:08 jacob-laptop-w lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jun 14 18:14:08 jacob-laptop-w lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jun 14 18:14:08 jacob-laptop-w lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jun 14 18:14:09 jacob-laptop-w lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "jacob"
Jun 14 18:14:09 jacob-laptop-w dbus[905]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.44" (uid=104 pid=3024 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=2580 comm="/usr/sbin/console-kit-daemon --no-daemon ")
------

Interestingly I'm able to enter the system through the guest account and switch user (su) to my own.

Could there be a problem with lightdm?
Perhaps a case of [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951404](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951404) ?

... I'm very open to suggestions at this point, I'd hate to reinstall the system...

Thanks,

---

### Post by iqtedar on 2012-06-15
I'm experiencing problems with lightdm under Ubuntu 12.04 as well so I'm using gdm now as my login manager. I don't know about the sep driver issue but have you tried any other login manager in place of lightdm? If you boot into lightdm, get to another console (such as alt+ctrl+f1) and run 'sudo service lightdm stop', then do 'sudo service gdm start'.

---

### Post by jokemach on 2012-06-17
iqtedar: Thanks, worked like a charm. Any idea what causes the issue with lightdm?

---

### Post by iqtedar on 2012-06-17
[FONT=monospace]Not exactly jokemach, but lightdm is known to have been been buggy before they ironed things out for Ubuntu 11.10 for which it became the default login manager. Now with 12.04 some problems seem to have crept in again. If you're happy with gdm instead of lightdm, you'll need to make it default. Get to a terminal and type: sudo dpkg-reconfigure gdm. Then select gdm. You can also try another login manager such as kdm.[/FONT]

---

