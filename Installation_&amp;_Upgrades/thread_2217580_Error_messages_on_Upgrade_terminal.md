---
title: "Error messages on Upgrade terminal"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by mal3 on 2014-04-17
I bit the bullet on one of my two machines and updated from 13.10 to 14.04. 

But being bored I turned on the terminal and watched some of the scrips runnning past !!!.

rather perturbed to see many times text such as :

Fontfig error .........................  line 14
Fontfig error .........................  line 23
Fontfig error .........................  line 32

and

Likely this means system is broken 

and

file could not be read correctly - please consider raising a bug


I assume this script log is stored on the pc somewhere ( I'm new to this ) and i could find it and send it off if required.

Or is this normal.

14.04 seems to be working ok - ive only tried a few things though. 

Maybe I had better re-install 13.10 ??

---

### Post by 23dornot23d on 2014-04-17
Before you do that just check things out first .........

**cd** **/var/log**

or look in there using dolphin or nautilus file manager ..........

is where the logs are kept ........

You could have a good look through them - but did anything seriously go wrong ...... 
the search for the errors you report in google return little .........

have a look in the log files to be sure .........

or do

[B]sudo apt-get -f install

[/B]to see if anything should come up

Something like this on my own system .......  but you may just want to scan through dmesg
and see if it holds the information you need. [http://en.wikipedia.org/wiki/Dmesg](http://en.wikipedia.org/wiki/Dmesg)

Can either go through them in the terminal ...... or use a file manager and open whichever log you think the
errors applied to .........

Most of the logs usually appear in here .....

```

K53SV:[COLOR=#ff0000]**/var/log**[/COLOR]$ ls
alternatives.log    dmesg.0             prime-offload.log
alternatives.log.1  dmesg.1.gz          prime-supported.log
apport.log          dmesg.2.gz          rkhunter.log
apport.log.1        dmesg.3.gz          rkhunter.log.1
apport.log.2.gz     dmesg.4.gz          rkhunter.log.old
apport.log.3.gz     dpkg.log            samba
apport.log.4.gz     dpkg.log.1          speech-dispatcher
apport.log.5.gz     faillog             syslog
apport.log.6.gz     fontconfig.log      syslog.1
apport.log.7.gz     fsck                syslog.2.gz
apt                 gdm                 syslog.3.gz
aptitude            gpu-manager.log     syslog.4.gz
aptitude.1.gz       hp                  syslog.5.gz
auth.log            installer           syslog.6.gz
auth.log.1          kdm.log             syslog.7.gz
auth.log.2.gz       kdm.log.1           timeshift
auth.log.3.gz       kdm.log.2.gz        udev
auth.log.4.gz       kdm.log.3.gz        ufw.log
boot.log            kdm.log.4.gz        unattended-upgrades
bootstrap.log       kern.log            upstart
btmp                kern.log.1          wtmp
btmp.1              kern.log.2.gz       wtmp.1
clamav              kern.log.3.gz       Xorg.0.log
ConsoleKit          kern.log.4.gz       Xorg.0.log.old
cups                lastlog             Xorg.8.log
dirmngr             lightdm             Xorg.8.log.old
dist-upgrade        pm-powersave.log    Xorg.failsafe.log
dmesg               pm-powersave.log.1  Xorg.failsafe.log.old

K53SV:/var/log$ [COLOR=#ff0000]**less dmesg**[/COLOR]

K53SV:/var/log$ sudo apt-get -f install
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-19 linux-headers-3.13.0-19-generic linux-headers-3.13.0-22
  linux-headers-3.13.0-22-generic linux-image-3.13.0-19-generic
  linux-image-3.13.0-22-generic linux-image-extra-3.13.0-19-generic
  linux-image-extra-3.13.0-22-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
K53SV:/var/log$ 


```

I usually do commands on my own machine to show what they do and also to check they will
work ok .........

Could also check in this directory ...... mine has nothing in it ..... but this was a clean install

but it may have the log you need in it ....... if yours was a dist-upgrade .........

/var/log/dist-upgrade

---

### Post by mal3 on 2014-04-18
Many thanks for that - I have found the log;

Two main errors i have found so far - and I am a beginner at this !

(gtk-update-icon-cache-3.0:15282): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.



"Unpacking libaudit-common (1:2.3.2-2ubuntu1) over (1:2.2.2-1ubuntu4) ...
Processing triggers for man-db (2.6.5-2) ...
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 14: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 23: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 32: out of memory

and

---

