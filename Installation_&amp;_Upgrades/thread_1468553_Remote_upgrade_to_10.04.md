---
title: "Remote upgrade to 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2010-05-01
I have ssh access to a machine running 9.10. Now I want to remote upgrade it to 10.04.

What is the best/safest way to do that?

---

### Post by mistofeles on 2010-05-01
> **koma77 said:**
> I have ssh access to a machine running 9.10. Now I want to remote upgrade it to 10.04.

What is the best/safest way to do that?

DO NOT EVEN TRY !
I have now stoned three servers with upgrade from 9.10 srv to 10.04 srv. And I know for sure that I can dublicate the experience. The problem is not connected with hardware.
I found it mentioned that this kind of phenomenon had appeared in BETA 2 stage but neglegted.

The upgrade by itself went fast and without problems. Luckily I was a bit paranoid and opened another ssh to the server.
After the upgrade I tried to open third terminal. Putty asked three times for "password" and ansvered nothing.  Then three times threw another kind of pasword phrase: "root@myserver password" and ansvered "Permission denied, please try again.". Then at last:
"Received disconnect from 192.xxx.xxx.xxx: 2: Too many authentication failures for root"

In the ssh terminal which I have left open, I tried to change password for root and the sudo -user and got an error localized error message. For some #¤%&/ reason the system had installed the error messages with local language. For some ¤%&/&% reason there is no code key system for the error messages in Linux.

Then I tried to buld a new user. The system managed to add the lines to /etc/group and etc/passwd and build a directory /home/username. Then it gave a localised error message and died.

The first server was my test bench. The second was a production machine. The upgrade started by itself, when I asked "apt-get purge samba". The third was another test bench.

I was lucky, because I had ssh terminal open in the production machine. I had a possibility to copy my root log to another server and stop backup routines before the terminal halted. Another hit of luck is that I have allways installed two HD to my servers: another for system and data and another for backup. I have a full backup of all data and settings. Even the www -pages and my scripts are safe.

The server is in a rather distant place, with no easy access and behind locked doors and I don't have keys. This will cost me money and my customer is not very pleased.

It seems that there is no way to get in through SSH. I got to get there personally with an installation CD and wipe the whole installation out. The installation takes about an hour. 1 hour for the special network settings. Another 2 h will be spent returning the /home directories and their settings. Some 2 h for the www server and pages and data-I/O. 2 h for the scripts. The next day will be spent testing all and everything.

Somebody told that it takes about 20 minutes to get Ubuntu up and running. Maybe I do something wrong.
------------------------------------------------
root@zetor:~# ssh root@vikunja
Password:
Password:
Password:
root@vikunja's password:
Permission denied, please try again.
root@vikunja's password:
Permission denied, please try again.
root@vikunja's password:
Received disconnect from 192.xxx.xxx.xxx: 2: Too many authentication failures for root

------------------------------------------------

OPINION: there is a need for a tool, which can be used to make a safe upgrade to an remote server. The tool should have a watchdog: it the administrator don't respond in a preset time, the tool will downgrade back to earlier state or build some kind of root  terminal somehow.

OPINION 2: I do not like these distro carnivals. I would like more, if the programs will evolve one by one to a ripe state. This kind of carnival makes programmers throw too low tested version in the distro, because the packet has to be ready in some predetermined day. The world just don't evolve through predetermined states.

Darwin didn't speak anything about quantum leaps in his evolution theory.

---

### Post by koma77 on 2010-05-02
That sounds quite serious.

Are there any options on doing a remote install other than running the do-release-upgrade script?

Will X-forwarding and update-manager be a better alternative?

---

### Post by kat_ams on 2011-03-04
It sounds like someone forgot the principles of Ubuntu. There is no root user and ssh via root is turned off by default.

Launchpad has a way of automatically doing an dist upgrade. Maybe experiment on a test machine using Launchpad.

---

### Post by minigilani on 2011-04-22
> **kat_ams said:**
> There is no root user and ssh via root is turned off by default.


There **is** a root user; it's just locked. To enable it: just change the root password:
```

sudo -i
passwd
```

Considering the account of mistofeles's experience, i'd say he knew all this. Note the bold bits:
> 
**root**@zetor:~**#** ssh root@vikunja


---

