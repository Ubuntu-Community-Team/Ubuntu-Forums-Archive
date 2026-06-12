---
title: "Lost of packages not configured, build-dep doesn't work"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-10-14
When tryint to install anything, I get the following error:

```


jesse@jesse:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Everything else ( besides 2 kernels ( see other thread in this section)) work after my new upgrade. How can I solve this rather urgent problem?

Thanks greatly in advance :)

---

### Post by xyzzyman on 2005-10-14
I would uninstall postfix, then reinstall if you need it. msttcorefonts won't work for me, so whenever it's 'installed', it tries fixing it after i do anything else with apt/synaptic, and gives an error.

---

### Post by Jessehk on 2005-10-14
[QUOTE=xyzzyman]I would uninstall postfix, then reinstall if you need it. msttcorefonts won't work for me, so whenever it's 'installed', it tries fixing it after i do anything else with apt/synaptic, and gives an error.[/QUOTE]


when I mark postfix for uninstallation, I get a bunch of other, necessary, packages marked for removal as well. 

Thanks for the reply, but I am going to wait for more advice :)

---

### Post by az on 2005-10-15
Open a terminal and try

sudo apt-get -f install

---

### Post by Jessehk on 2005-10-15
Thanks, but I get the same error:

```


jesse@jesse:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by wgscott on 2005-10-15
Issue 

sudo synaptic

and then try to do it with the dialog box.  I found it sorted things out more readily than apt-get (which up until then I preferred).

---

### Post by az on 2005-10-15
Yep.  Remove postfix, fix everything and then reinstall it.

Possibliy, you need to kill it first?

sudo /etc/init.d/postfix stop

---

### Post by dcostelloe on 2005-10-15
I upgraded and found too many problems. My setup for mail server from the : [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Failed on pretty much everything.

To get every thing back to a working order I did a complete rebuild using Breezy. Steps I tool below:

Backup to cd or send the configurations to your yahoo or something

Postfix: /etc/postfix
main.cf
Master.cf
directory: /etc/postfix/sasl

all the mysql_ files (if you used flurdy How To)
postfix.key

Courier:
pretty much everything in the directory

Spamassassin
Everything except the init.pre

Clamav:
all the .conf

Problems that you will encounter:

missing packages:

libsasl7
libsasl-modules-plain

Trying to get these myself

---

