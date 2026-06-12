---
title: "Problems with Transmission installation/setup"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-03-07
I've been trying to setup the Transmission BitTorrent package on Trusty Tahr and can't get it to auto-start.

The Ubuntu TransmissionHowTo indicates I should be able to use:

 [FONT=courier new]sudo service transmission-daemon start[/FONT] 

but doesn't seem to work.  A re-boot didn't bring the daemon to life either.

Tha config file is also in a different location from that specified in the HowTo (now at [FONT=courier new]/etc/transmission-daemon/settings.json[/FONT] rather than [FONT=courier new]/var/lib/transmission-daemon/info/settings.json[/FONT]).

Clearly some things have changed since the HowTo was written.

So what should I do (simple steps please - newb here) to get it to autostart.

Thanks
Dave

---

### Post by papibe on 2016-03-07
Hi David_Partridge.

Which version of Ubuntu are you using?

Did you install it from the repos, or from a ppa?

Could you post the link to the tutorial you are mentioning?

Could you open a terminal, run these commands, and post back the results? (you can copy/paste the text)
```
apt-cache policy transmission-daemon 

sudo service transmission-daemon status

ls -l /etc/transmission-daemon/

cat /etc/default/transmission-daemon
```
Regards.

---

### Post by David_Partridge on 2016-03-07
Ubuntu Server 14.04,4 LTS

I *think I installed from ppa as I did

sudo add-apt-repository ppa:transmissionbt/ppa

The Instructions I was following are at 

[URL="http://help.ubuntu.com/community/TransmissionHowTo"]http://help.ubuntu.com/community/TransmissionHowTo
[/URL]
```
amonra@Charon:~$ apt-cache policy transmission-daemon
transmission-daemon:
  Installed: (none)
  Candidate: 2.92-0ubuntu0.15.04.1
  Version table:
     2.92-0ubuntu0.15.04.1 0
        500 [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) trusty/main amd64 Packages
     2.90-0ubuntu0.15.04.3 0
        100 /var/lib/dpkg/status
     2.82-1.1ubuntu3.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
     2.82-1.1ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
amonra@Charon:~
amonra@Charon:~$ sudo service transmission-daemon status
[sudo] password for amonra: 
transmission-daemon: unrecognized service
amonra@Charon:~$ ls -l /etc/transmission-daemon/
total 8
-rw-r--r-- 1 root                root                 303 Mar  1 21:15 README.json
-rw------- 1 debian-transmission debian-transmission 2267 Mar  7 18:33 settings.json
amonra@Charon:~$ cat /etc/default/transmission-daemon
cat: /etc/default/transmission-daemon: No such file or directory
amonra@Charon
```

---

### Post by papibe on 2016-03-07
Thanks.
```
 Installed: (none)
```
It looks like yo haven't install transmission-daemon yet. Do it like this:
```
sudo apt-get udpate

sudo apt-get install transmission-daemon
```
Hope it helps. Let us know how it goes.
Regards

---

### Post by Bucky Ball on 2016-03-07
For future reference, Transmission is in the official repos for your release. Just install from there. No need for a manual install of a PPA (and avoiding PPAs is a good thing as Canonical has no quality control over what goes in them). Always check Software Centre first. ;)

Just thought I mention it. Good luck.

---

### Post by David_Partridge on 2016-03-08
I'm such a newb here that I don't know what Software Centre is so wouldn't know how to check it first.

Should I remove the ppa entry I created for it and if so how?

Yes somehow transmission-daemon wasn't installed. How I have no clue.  Maybe I mistyped the name first time round.

I still get "transmission-daemon: unrecognized service" when I issue sudo service transmission-daemon stop :(

Dave

Follow up:

I did:

```
sudo add-apt-repository --remove ppa:transmissionbt/ppa
```

followed by:

```
sudo apt-get purge transmission-cli etc.
```

I then reinstalled from the "default" location and it installed 2.82 and entered it into the services list.

So looks like the installation/setup of version 2.92 at transmissionbt doesn't do everything that the Ubuntu tailored version does.

Thanks
Dave

---

### Post by papibe on 2016-03-08
EDIT: sorry I believe you have solved your problem. Let us know if you need more help with transmission-daemon. I personally use it a lot ;-)

original post
> 
transmission-cli is an independent client, much like rtorrent. There no service to start or stop.

transmission-daemon is a full service. It runs on the background and can be start and stop. It receives commands over transmission-remote (cmd line tool), over a web page, or both.

My assessment is that you want to install transmission-daemon, and use it over a web page, right? If so, install it like this:
```
sudo apt-get install transmission-daemon
```
Regards.

---

### Post by Bucky Ball on 2016-03-08
So the one in the repos worked for you? Please confirm.

Also,

> sudo apt-get install transmission

... would have done it for you. :)

---

