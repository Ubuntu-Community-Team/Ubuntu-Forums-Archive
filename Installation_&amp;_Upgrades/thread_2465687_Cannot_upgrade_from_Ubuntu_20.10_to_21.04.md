---
title: "Cannot upgrade from Ubuntu 20.10 to 21.04"
date: 2021-08-08
forum: Installation &amp; Upgrades
---

### Post by riyaaz2021 on 2021-08-08
I am currently experiencing issues when trying to upgrade from Ubuntu 20.10 to 21.04 on my Raspberry Pi4 (4GB).

I've tried running sudo do-release-upgrade, with no luck as of yet.

I've ran this via SSH/Telnet/Ubuntu Desktop UI and get the same below.

How do I get around this to upgrade to the latest release 21.04?

Even when I connected via RDP to the Ubuntu UI Desktop, then went ot Software Updater, I got the option to "Upgrade", but after selecting that nothing happened thereafter.
The window just disappeared, and then when going back to the same screen, the "Upgrade" option is there.

Anyone else experiencing the same issues?


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Hit [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) groovy InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security InRelease
Fetched 0 B in 0s (0 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
=== Command detached from window (Sun Aug  8 18:18:25 2021) ===
=== Command terminated with exit status 1 (Sun Aug  8 18:18:35 2021) ===

---

### Post by ActionParsnip on 2021-08-08
I don't suggest you upgrade remotely. The upgrade process will restart the services you are connected to and, because the upgrade process is a child of your login process, will kill the upgrade when you are kicked off the server.
Always do upgrades sat in front of the server / via VM console / via ILO/DRAC etc.

---

### Post by ActionParsnip on 2021-08-08
If you run:
```

sudo apt update
sudo apt full-upgrade 

```
Does it upgrade the system as normal and without issue?

---

### Post by riyaaz2021 on 2021-08-09
Yeah I was thinking the same thing w.r.t to the remote upgrade to 21.04 via SSH. According to most of the support KB articles and forums I've come across to date it seems that most others can and have upgraded successfully via SSH to newer releases. So long as the "Prompt" = normal in config file all other update/upgrade commands then it should work.

I originally set up my RPi 4 with Ubunti Server (headless) and worked great, until now where I cannot remotely update to the latest release. After all the failed attempts to remotely upgrade, I then manually installed Desktop UI, then tried to do the same via UI through RDP session, still failed. It would seem odd though that one cannot upgrade remotely via SSH for a headless server instance?

I tried both command updates as well, everything is already updated okay.

I am no Linux guru at all, just an average user tbh. I tried looking via the DMESG logs, but couldnt find anything there, and what is a little frustrating is that when the Upgrade "aborts" it doesnt even spit out an error message/code, so you've got no idea why it even failed.

I will try via direct connection to the server instance, seems like the only option at this point.

---

### Post by MAFoElffen on 2021-08-10
i have Pi4... And I support Ubuntu Server, which it would be ludicrous to think that you should be standing in front of a bunch of racks, or even be in the computer room, to just do an upgrade. (think of cloud instances) Nor should you have to install a desktop to upgrade a Linux system...

1. Is is a wired connection?
2. Do you have your ssh keys copied over?
3. Does it resolve to the Ubuntu backports Repo if you just do
```
sudo update
```
4,. Have you looked at the Release upgrade logs to identify the specific problem that cause it to exit the process?
```
ls /var/log/dist-upgrade/*.log
```
The three main logs you want to look at are main.log, apt.log and term.log. They are two big to post. The main hint will be the main.log file. If you open it in an editor and search on "ERROR" it should point you to what happened. It don't see any added PPA's, so it may be from a manually installed package, or what not.

You may quickly find it doing:
```
egrep "ERROR" /var/log/dist-upgrade/main.log
```

---

### Post by riyaaz2021 on 2021-08-13
Hi,

Thank you for the detailed feedback and suggestions.

[COLOR=#000000]1. Is is a wired connection?
[/COLOR]--> Yes its a wired connection from my RPi4 directly to the Router.
[COLOR=#000000]2. Do you have your ssh keys copied over?
[/COLOR]--> Nah dont at present, not even sure how to do that will have to check
[COLOR=#000000]3. Does it resolve to the Ubuntu backports Repo if you just do
[/COLOR]--> Doing a " sudo update " comes up with sudo: update: command not found

When I checked the main.log file via [COLOR=#000000][FONT=&quot]/var/log/dist-upgrade I get the below extract:
Only part that stands out to me is the one in red?

Other 2 x log files apt and term had basically nothing there....

[/FONT][/COLOR]2021-08-08 18:15:56,827 INFO Using config files '['./DistUpgrade.cfg', '/etc/update-manager/release-upgrades.d/ubuntu-advantage-upgrades.cfg']'
2021-08-08 18:15:56,827 INFO uname information: 'Linux ubuntu 5.8.0-1032-raspi #35-Ubuntu SMP PREEMPT Wed Jul 14 10:51:21 UTC 2021 aarch64'
2021-08-08 18:15:57,582 INFO apt version: '2.1.10ubuntu0.3'
2021-08-08 18:15:57,582 INFO python version: '3.8.10 (default, Jun  2 2021, 10:49:15)
[GCC 10.3.0]'
2021-08-08 18:15:57,589 INFO release-upgrader version '21.04.16' started
2021-08-08 18:15:57,604 INFO locale: 'en_US' 'UTF-8'
2021-08-08 18:15:58,068 DEBUG Using 'DistUpgradeViewText' view
2021-08-08 18:15:58,249 DEBUG enable dpkg --force-overwrite
2021-08-08 18:15:58,502 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2021-08-08 18:16:12,850 DEBUG lsb-release: 'groovy'
2021-08-08 18:16:12,851 DEBUG _pythonSymlinkCheck run
2021-08-08 18:16:12,861 DEBUG openCache()
2021-08-08 18:16:12,861 DEBUG quirks: running PreCacheOpen
2021-08-08 18:16:12,862 DEBUG running Quirks.PreCacheOpen
2021-08-08 18:16:14,614 DEBUG Comparing 5.8.0-1029 with
2021-08-08 18:16:14,614 DEBUG Comparing 5.8.0-1032 with 5.8.0-1029
2021-08-08 18:16:14,920 DEBUG /openCache(), new cache size 60024
[COLOR=#ff0000]2021-08-08 18:16:14,922 DEBUG need_server_mode(): can not find a desktop meta package or key deps, running in server mode[/COLOR]
2021-08-08 18:16:14,922 DEBUG checkViewDepends()
2021-08-08 18:16:14,938 DEBUG running doUpdate() (showErrors=False)
2021-08-08 18:16:19,236 DEBUG openCache()
2021-08-08 18:16:21,034 DEBUG Comparing 5.8.0-1029 with
2021-08-08 18:16:21,035 DEBUG Comparing 5.8.0-1032 with 5.8.0-1029
2021-08-08 18:16:21,365 DEBUG /openCache(), new cache size 60024
2021-08-08 18:16:21,366 DEBUG doPostInitialUpdate
2021-08-08 18:16:21,366 DEBUG quirks: running hirsutePostInitialUpdate
2021-08-08 18:16:21,366 DEBUG running Quirks.hirsutePostInitialUpdate
2021-08-08 18:18:23,401 DEBUG abort called
2021-08-08 18:18:23,402 DEBUG openCache()
2021-08-08 18:18:25,145 DEBUG Comparing 5.8.0-1029 with
2021-08-08 18:18:25,146 DEBUG Comparing 5.8.0-1032 with 5.8.0-1029
2021-08-08 18:18:25,444 DEBUG /openCache(), new cache size 60024

Just to see I tried re-running the upgrade via SSH again and below is the extract:

Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Hit [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) groovy InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports InRelease
Hit [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security InRelease
Fetched 0 B in 0s (0 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
=== Command detached from window (Fri Aug 13 17:41:15 2021) ===
=== Command terminated with exit status 1 (Fri Aug 13 17:41:25 2021) ===

---

### Post by riyaaz2021 on 2022-01-08
Found issue.

Had to remove snapd and then re-running upgrade worked fine!

---

