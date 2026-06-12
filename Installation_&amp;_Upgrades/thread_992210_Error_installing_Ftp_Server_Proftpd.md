---
title: "Error installing Ftp Server Proftpd"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Sarethan on 2008-11-24
I am brand new to Ubuntu and like it so far. After several attempts to migrate from Windows to Linux i think i finally have it. I was a bit confused as how to fix this problem. While trying to get an ftp server to run in Ubuntu, i chose Proftpd but noticed that i kept getting errors that in the details stated (E; system-tools-backends: subprocess post-installation script returned error exit status 1) Now have working,building,selling, computers since the age of 6 and am now 23 but that made no sense to me and i don't know what to do or where to start. Can anyone help me out?

---

### Post by cariboo on 2008-11-24
There apparently is a bug in system-tools-backends. See [Bug# 294389]("https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/294389").

The work around to fix the problem is:

> ***TEMPORARY WORKAROUND***
After the upgrade has failed, you will get an error every time you run dpkg or apt-get saying that system-tools-backends is not configured. "sudo dpkg --configure -a" will not fix this. To recover, please perform the following 2 steps:

1) sudo invoke-rc.d system-tools-backends stop
2) sudo dpkg --configure -a

***TEST CASE FOR SRU***
1) With current version (2.6.0-1ubuntu1.1) of system-tools-backends installed, open up 2 terminals.
2) In the first terminal, type "users-admin", but don't press enter to run it yet.
3) In the second terminal, run "sudo apt-get install --reinstall system-tools-backends".
4) As soon as this line appears in the second terminal, hit enter in the first terminal to run users-admin: "* Stopping System Tools Backends system-tools-backends"

The reinstall will fail. Once this has happened follow the workaround above to recover, then upgrade to 2.6.0-1ubuntu1.2.

Once upgraded, repeat steps 1 - 4, and note that the reinstall never fails.

Jim

---

### Post by Sarethan on 2008-11-24
Ok i have done the first two steps and the synaptic manger allowed me to install and shows it with a green box (installed) but the add remove applications thing doesn't list it as installed and i can figure out how to run it....(use to windows) :(

---

### Post by cariboo on 2008-11-24
Proftpd is an ftp server. Depending on how you set it up, it is probably running already. To find out if the ftp server is running in a Applications-->Accessories-->Terminal type:

```
ps ax | grep proftpd
```

You should get a result something like this:

```
 ps ax | grep proftpd
 5353 ?        Ss     0:03 proftpd: (accepting connections)
```

To access your ftp server from another computer on your network open up your favorite ftp client and type in the ip address of your ftp server and use the user name and password for the computer the server is on.

If you you need to change anything in the configuration the files ares located in /etc/proftpd/. they are well commented so you should find most of what you need there. For more info in a terminal type:

```
man proftpd
```

Jim

---

### Post by Sarethan on 2008-11-26
Tank you....yes it was running. wow this is way diff but far more reliable. So how do i learn the commands to do common task like that? Is there a reference guide or is it with trial and error?

---

