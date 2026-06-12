---
title: "Simple Q's about FusionDirectory"
date: 2023-08-29
forum: Installation &amp; Upgrades
---

### Post by civilpolisen on 2023-08-29
1. We had an error yesteray related with a conflict. This is now sorted out and the services are back on track! Where do I edit the logs!?

2. We're currently using Ubuntu 18.04 but for obvious reasons we sould like to upgrade the server to Ubuntu 20.04.We tried this two and it wasn't really working... Maybe it's working better today?

---

### Post by Holger_Gehrke on 2023-08-29
1. Why would you edit a log ? A log file is basically the history of what happened on your system. If the fix you did to sort out the conflict doesn't work in the long term, you might need to refer back to the original error message to devise a better fix and you couldn't do that if you edited the logs.

2. More details about the way the attempted upgrade failed would help us help you ...

Holger

---

### Post by civilpolisen on 2023-08-30
1. Bad English! My appology! I don't actually want to "edit the log files"! No! I write again!
1. Where in the user interface is there a setting to change the size of  the log? We don't need years and many gigs of saved, log-in data...

2. My boss told me...Generic... "I tried install Fusion Directory on  Ubuntu 20.04  two years ago and it was not working very well."
I've been looking at the website of Fusion Directory and FD seem to have  a pretty broad user base and I truely doubt they all use Ubuntu 18.04!

---

### Post by yancek on 2023-08-30
Ubuntu has logrotate installed by default and you can change settings if you need to.  The site at the link below gives an explanation of its use and some options for 20.04.

[https://www.digitalocean.com/community/tutorials/how-to-manage-logfiles-with-logrotate-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-manage-logfiles-with-logrotate-on-ubuntu-20-04)

---

### Post by civilpolisen on 2023-08-30
Thank you for advice! Now the console says "Usage of /:   42.6% of 18.53GB" when logging on... That's fair.

I've used another kind of log rotate... than described in the link. Either it works as well, or it's something else!

Are you all using Fusion Directory with Ubuntu 20.04? We use Ubuntu 18.04 and I don't like that... I would like to upgrade the operating system.
It would be possible to do a clone, upgrade the clone and see what errors that may occur.

---

### Post by TheFu on 2023-08-30
logrotate handles the text version of logs and is still necessary, for now.  Debian 12 doesn't have text logs anymore. They all reside inside the systemd-journald DB alone. We have a systemd-journald DB on Ubuntu too, since systemd was introduced ... 16.04-ish.
My notes:
```
== Log Files ==

  journalctl -xe            # See errors for last service, with eXtra information
  journalctl -b -1          # See prior boot log
  journalctl -b -3          # See 3 boot logs ago
  journalctl -b             # See current boot logs
  journalctl --list-boots   # See how many prior boots are available
  sudo journalctl -k        # See current kernel logs
  
  journalctl --since=today
  journalctl -S today       # See logs for today, from midnight, yesterday/tomorrow
  journalctl -xe -S today   # See errors for today, from midnight today
  
  sudo journalctl /usr/bin/anacron # logs for a specific executable (full path is required)
  journalctl UNIT=snap.lxd.activate # get messages for a specific systemd unit file
  journalctl -u nfs-kernel-server.service   # Unit file/service
  journalctl -u nfs-server.service -S -2h   # Unit file/service in the last 2 hrs
  
  sudo journalctl -S -1h    # See logs for last 1 hour m/w == minutes/weeks
  
  sudo journalctl _PID=751  # find logs for a specific PID
  sudo journalctl _UID=1000 # find logs for a specific user
  journalctl -p 0           # emergency
                1           # alert
                2           # critical
                3           # error
                4           # warning
                5           # notice
                6           # info
                7           # debug

  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```

The settings that tell journalctl how long and how large is in the/etc/systemd/journald.conf  file. There is a good manpage which explains all the many different settings. I know of no GUI for this.

Journald makes centralized logs easy.  It also makes getting just the logs for the specific daemons or error levels easier.  I'm not much of a systemd fan, but journald is totally A-W-E-S-O-M-E!

---

### Post by civilpolisen on 2023-09-01
Yesterday I created two local servers with Ubuntu 20.02 and 22.04 and installed the same packegages as below, Ubuntu 18.04. Both failed to start. 

```
Ubuntu 22.04
Fatal error: Class SetAttribute cannot extend final class Attribute in /usr/share/fusiondirectory/include/simpleplugin/attributes/class_SetAttribute.inc on line 0
```

Ubuntu 20.04 doesn't even try to connect in the browser... "Connection failed."
What am I missing!? Is there something special I need to know!?

```
civilpolisen@lynx:~$ apt list --installed | grep fusion

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

argonaut-fusiondirectory/bionic,now 1.0-1 all [installed]
fusiondirectory/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-alias/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-alias-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-argonaut/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-argonaut-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-autofs/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-autofs-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-community/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-community-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-dns/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-dns-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-dovecot/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-dovecot-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-ldapdump/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-mail/stable,now 1.3-1 all [installed,automatic]
fusiondirectory-plugin-mail-schema/stable,now 1.3-1 all [installed,automatic]
fusiondirectory-plugin-posix/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-postfix/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-postfix-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-spamassassin/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-spamassassin-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-ssh/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-ssh-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-sudo/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-sudo-schema/stable,now 1.3-1 all [installed]
fusiondirectory-plugin-systems/stable,now 1.3-1 all [installed,automatic]
fusiondirectory-plugin-systems-schema/stable,now 1.3-1 all [installed,automatic]
fusiondirectory-schema/stable,now 1.3-1 all [installed]
fusiondirectory-smarty3-acl-render/stable,now 1.3-1 all [installed,automatic]
civilpolisen@lynx:~$
```

---

### Post by TheFu on 2023-09-01
I know nothing about Fusion Directory, except what I could learn in 3 minutes with google.   [https://fusiondirectory-user-manual.readthedocs.io/en/1.4/fusiondirectory/install/index.html](https://fusiondirectory-user-manual.readthedocs.io/en/1.4/fusiondirectory/install/index.html) are the installaion instructions.  After packages are installed, those instructions say to run 'fusiondirectory-schema-manager'

I am looking for a nice interface into my centralized LDAP, but I was resigned to use Cockpit, though I want to avoid webapps for this critical task.

BTW, Bionic support ended in April, so unless you have ESM, it is a bad idea to still run it.

---

### Post by randyrue on 2023-12-19
Don't know if you're still getting alerts for this thread.

I just tried to install fusiondirectory on Ubuntu 22 LTS with the same error. Did you ever figure this out?

I installed straight from the Ubuntu repos. Anyone else have any information?

---

### Post by randyrue on 2023-12-20
Next question, if we run the steps at [https://fusiondirectory-user-manual.readthedocs.io/en/1.4/fusiondirectory/install/ubuntu/ubuntu-fd-install.html#fusiondirectory-schema-setup](https://fusiondirectory-user-manual.readthedocs.io/en/1.4/fusiondirectory/install/ubuntu/ubuntu-fd-install.html#fusiondirectory-schema-setup) to update the LDAP schema, how does the app know where to find the ldap it's messing with? I've spun up a test copy of our ldap server because I don't want to do this to our prod ldap untested.

---

