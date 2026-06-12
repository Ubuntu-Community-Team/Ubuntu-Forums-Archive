---
title: "URGENT: Lost GUI during upgrade from Ubuntu Gnome 16.04 to 18.04"
date: 2019-06-19
forum: Installation &amp; Upgrades
---

### Post by Yuval_Khalifa on 2019-06-19
Hi,

I have (or perhaps "had" :confused:) Ubuntu GNOME 16.04 installed on my laptop and I decided to upgrade it to the newly released Ubuntu 18.04 so ran apt upgrade, apt-get autoremove and finally do-release-upgrade from a terminal window. I did that about 3 hours ago and at some point the GUI screen turned black and I could see some of the boot messages (such as "[ OK ] Started <so and so service>") and I had no way to tell if the upgrade is still running in the background, has already finished or failed (God forbid).

So here's the list of things that I did to find out the current status:
I hit Ctrl+Alt+F1 to switch to another TTY and then ran the following commands:
1. uptime (to see if the computer has rebooted while I wasn't looking... it says that the system is up 09:37:35 which means that it's up for 9 hours, right? so no reboot has occurred)
2. ps -efl | grep apt (to see if the upgrade process is running any apt-get commands... No such commands were found)
3. ps -efl | grep dpkg (to see if the upgrade process is running any dpkg commands... Only one such command is currently running: /usr/bin/dpkg --force-overwrite --status-fd 113 --configure procps:amd64)
4. ps -efl | grep python (to see if the upgrade process is running any python commands... three such commands are currently running:
                /usr/bin/python3 /tmp/ubuntu-release-upgrader-71680w5j/bionic --mode=server --frontend=DistUpgradeViewTest (This one for some reason runs twice)
                /usr/bin/python3 /usr/share/unattended-upgrade-shutdown --wait-for-signal
                python3 /usr/lib/software-properties/software-properties-dbus
5. cat /etc/*-release (It says that my current version is 18.04 and VERSION="18.04.2 LTS (Bionic Beaver)"

So... is it safe to do sudo reboot? 
What do you say....

Tnx,
Yuval

---

### Post by Rubi1200 on 2019-06-19
Hi Yuval,

drop to a TTY and run the following commands, posting the output here between code tags if there are any error messages.

```
sudo dpkg --configure -a
```

```
sudo apt update
```

Let's see if there are any issues being reported.

Thanks.

---

### Post by Yuval_Khalifa on 2019-06-19
Thanks Rubi1200 for your quick reply.

In both commands I get a message saying that a file is locked:
dpkg: error: dpkg frontend is locked by another process

and:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavialable)
E: Unable to lock directory /var/lib/apt/lists/

What to do?

---

### Post by Yuval_Khalifa on 2019-06-19
Just as a P.S.... I tried to see which process currently using this directory so I ran lsof | grep /var/lib/apt/lists/ and found that there are two PIDs that are currently using this folder and I used ps -efl to grep for them and found that both of them are the processes of "/usr/bin/python3 /tmp/ubuntu-release-upgrader-71680w5j/bionic --mode=server --frontend=DistUpgradeViewTest" (which I already mentioned that it was running twice) 

Also, I started the installation about six hours ago... Could it still be running or doing anything? I also tried to run iotop and I see that the total disk write and read are always on zero, and the top process is gnome-session....

Do you think it is safe to assume that the installation is complete? How can I make sure that if I'll reboot I'll get back to my OS correctly?

---

### Post by Rubi1200 on 2019-06-19
What does this show?

```
ps -A | grep apt
```

---

### Post by Yuval_Khalifa on 2019-06-19
Hi...

It returned no processes at all.

---

### Post by Rubi1200 on 2019-06-19
That's interesting. Normally a lock message means more than one package management process is running. Find the PID, kill process and then run dpkg again to check all is okay.

This post suggest removing the file to resolve the problem:
[https://askubuntu.com/questions/1109982/e-could-not-get-lock-var-lib-dpkg-lock-frontend-open-11-resource-temporari](https://askubuntu.com/questions/1109982/e-could-not-get-lock-var-lib-dpkg-lock-frontend-open-11-resource-temporari)

Also here:
[https://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/](https://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/)

Not sure what else to suggest right now.

---

### Post by Yuval_Khalifa on 2019-06-19
Thanks. I have killed (nicely, not with -9) the two processes that held the lock and ran sudo dpkg --configure -a and for a moment it seemed like it's continuing the installation from the point it left but after installing few files it ended up with this: 
Errors were encountered while processing:
.
.
.
.
bunch of packages such as krita, modemmananger, openjdk-8-jdk:amd64
.
.
.
.
Processing was halted because there were too many errors.




What to do???:confused:

---

### Post by Rubi1200 on 2019-06-19
I hate to ask this but do you have solid backups of all your data?

If yes, it might be better to just do a fresh install and then restore your data.

Too many errors? That does not sound good :-(

---

### Post by Yuval_Khalifa on 2019-06-19
Hi again,

Just updating that after I tried to run it again and reached the same result I decided to try and use apt to install one of the packages the usual way and ran sudo apt install gdm3 and I received an error saying that I should run sudo apt-get -f install, so I did that and it installed lots of packages and then returned to the command prompt. I tried to run it again and this time it just listed a bunch of packages and recommended that I'd run sudo apt autoremove but I decided not to do that, instead I ran sudo dpkg --configure -a and it immediately returned to the prompt without displaying anything.

Does it mean that I can reboot safely now?

---

### Post by Rubi1200 on 2019-06-19
You can safely run apt autoremove, it will clean up package dependencies that are not needed.

Safely reboot?

No error messages is usually a pretty good sign ;-)

I honestly do not know but keeping fingers crossed if you decide to do it.

---

### Post by Yuval_Khalifa on 2019-06-20
Hi,

Just to close this thread: Yesterday, I decided to reboot the system and somewhat surprisingly, it came back alive and well. Well, sort of... I ran sudo apt update and it couldn't get to any of the URLs of the repos, I quickly found out that the reason for that was that it could not resolve hostnames to IPs. I looked at /etc/network/interfaces and found out that the dns-nameservers line was commented out, probably by the setup, I uncommented it and rebooted and tried again and this time it worked, so I ran sudo apt upgrade and it listed a huge list of packages that required an upgrade (probably those it couldn't update during setup) and I allowed it to continue with the upgrade and after about an hour or so, it finished the installation and requested a reboot, I rebooted and went to "Software" and then clicked "Updates", there was only one package to update now, I did that and now it seems to be working perfectly and if I go to see system details in the settings tool I see that it is running Ubuntu 18.04.2 and also if I run cat /etc/*-release I see the same version so I think it is now ready for work again and I can finally start breathing normally. I have upgraded and lived to tell the tail... (-:

Thanks a lot for all your help,
Yuval.

---

### Post by Rubi1200 on 2019-06-20
Very pleased to hear this Yuval :-)

It is always a nervous experience when things don't go exactly to plan but you persevered and now everything is good.

Please mark this Solved using Thread Tools at the top of the page.

And good luck!

---

