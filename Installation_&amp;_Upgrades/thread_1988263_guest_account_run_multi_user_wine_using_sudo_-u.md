---
title: "guest account: run multi user wine using sudo -u"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by go4unkwn on 2012-05-27
Hello all

I have to run MS Office 2007 in the guest account using /usr/sbin/guest-account.
I modified the sript in order to adapt the sudores file using sed.

[CENTER][LEFT]In the wine set up I followed "Howto: Install Wine applications for Multiple Users".
(Link: [http://ubuntuforums.org/showthread.php?t=917422](http://ubuntuforums.org/showthread.php?t=917422))

Additionally I created a wrapper script (as a bash newby) to start the wine applications:
------
#!/bin/bash

WINEPROG="EXCEL.EXE"

PID=$(pgrep ${WINEPROG})

if [ $? -ne 0 ]
then
    export WINEPREFIX=/home/windows/.wine/
    xhost +local:windows
    sudo -u windows -H wine /home/windows/.wine/drive_c/Programme/Microsoft\ Office/OFFICE11/${WINEPROG}
else
    exit 0
fi
------

After finishing the this setting I can run MS Office 2007 applications from different non admin users (for example: user test) without any problems.

But when I login as Guest, an run the wrapper in a termina I get an error message:
sudo unable to change to sudoers gid

Does Ubuntu 12.04 treat user Guest in another way than other non-admin users in relation to sudo -u (see wrapper).

Any help would be appreciated!

Kind regards, go4unkwn.
[/LEFT]
[/CENTER]

---

### Post by go4unkwn on 2012-05-27
Hello (it's me again)

Til now I found out, that **apparmor** is the reason, that guests couldn't use the multiple user wine setup.

If I teardown apparmor profiles (/etc/init.d/apparmor stop/teardown) userrs of the guest account are able to run MS Office applications.

Now my questions is, how to adapt apparmor, in order to run apparmor and to allow guest users to run MS Office applications.

Any hint would be appreciated.

Kind regards, go4unkwn.

---

