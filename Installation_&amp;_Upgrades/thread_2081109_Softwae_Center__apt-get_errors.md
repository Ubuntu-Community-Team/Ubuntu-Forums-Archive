---
title: "Softwae Center / apt-get errors"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by umfunix on 2012-11-05
I have an error with either installing apps through Software Center or apt-get.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
seahorse is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have installed xampp which at first didn't worked.  The mysql service didn't want to start or stop.  I then uninstalled xampp, tried to install mysql server and a client from Software Center. It didn't complete (install errors).  I then removed them, restarted and reinstalled xampp.  This time it worked (that is my sql, php etc).

However, since then, whenever I install an app, either through the Software Center or apt-get, I get an error that a previous package was not installed fully and the installed app is not available.

How can I fix this error and starting using my apps?

---

### Post by Bashing-om on 2012-11-05
kaivy, Hi !

As the error is in mysql-server-5.5 ..how about trying to re-install the package?
with the server stopped try terminal code:
```
sudo apt-get install mysql-server-5.5 --reinstall 
```[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by umfunix on 2012-11-06
would that not mess up the xampp instsallation (which includes PHP, MySQL etc)?

---

### Post by umfunix on 2012-11-06
Hi

I tried it in any case and got the following error again...
```
Setting up mysql-client-5.5 (5.5.28-0ubuntu0.12.04.2) ...
Setting up mysql-server-core-5.5 (5.5.28-0ubuntu0.12.04.2) ...
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.28-0ubuntu0.12.04.2.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2012-11-06
at the present time the dependency is  on  mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) and the higher version on the system is (= 5.5.28-0ubuntu0.12.04.02) ............

Do not know how to downgrade the dependency to match the candidate, and if indeed it were to be downgraded ...the effect on other installed packages that depend on the 5.5.28 version ???

I am stumped !

[INDENT]I wish I had the answer ==> BDQ
 
[/INDENT]

---

### Post by umfunix on 2012-11-07
Thanks Bashing

I manager to get the error away (I don't know exactly how :confused: ).  But what happens now is that when I restart, the, lets say, original mysql starts up, while when I'm trying to develop my CMS (that's why I installed xampp), the xampp mysql doesn't start for obvious reason- the other one is running.  I therefore need to stop the original one and start the xampp one.  The reason for preferring the xampp at this stage is, I've already installed joomla and other modules.  The databases and config of the xampp-mysql is already established.  

So, my questions is therefore: how do I prevent the "original" one from starting at startup?

Thanks
(BTW, u guys are awesome. The community support makes the transition to Ubuntu (and Linux), child's play)

---

### Post by Bashing-om on 2012-11-07
well,, as we can not remove the original mysql package because of the inter dependencies, How bout just not starting it at all ->from the init script ?
See if the script is in /etc/init.d/ (older usage), may have to look around see if upstart starts the server and not start it from another source script.
[INDENT]hth <== BDQ

[/INDENT]

---

### Post by umfunix on 2012-11-24
I couldn't find the init script, but I'm ok with service mysql stop and then restarting the correct one as and when needed.

thanks for the help!

---

