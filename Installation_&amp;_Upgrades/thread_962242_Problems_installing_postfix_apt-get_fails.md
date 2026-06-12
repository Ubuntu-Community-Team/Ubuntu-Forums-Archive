---
title: "Problems installing postfix: apt-get fails"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by damiendusha on 2008-10-29
Hello all,

I am taking my first tentative step in the world of mail servers, though I may have accidental taken one before... hmmm...

Anyway, I am trying to install postfix, but am having problems with step 1: installing it.   Here's the dialogue from apt-get

```

damien@mediabox:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but it is not going to be installed
                      Conflicts: mail-transport-agent
  postfix: Conflicts: mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damien@mediabox:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  exim4-config
The following NEW packages will be installed:
  exim4-config
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1293kB of archives.
After this operation, 1053kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package exim4-config.
(Reading database ... 163396 files and directories currently installed.)
Unpacking exim4-config (from .../exim4-config_4.69-2_all.deb) ...
Selecting previously deselected package exim4-base.
Preparing to replace exim4-base 4.69-2 (using .../exim4-base_4.69-2_amd64.deb) ...
Unpacking replacement exim4-base ...
Setting up exim4-config (4.69-2) ...

Setting up exim4-base (4.69-2) ...

damien@mediabox:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql procmail resolvconf sasl2-bin
The following packages will be REMOVED:
  exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/1230kB of archives.
After this operation, 709kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 163499 files and directories currently installed.)
Removing exim4-daemon-light ...
 * Stopping MTA                                                                                                                                       /sbin/start-stop-daemon: warning: failed to kill 7246: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
dpkg: exim4-config: dependency problems, but removing anyway as you request:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is to be removed.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is to be removed.
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is to be removed.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is to be removed.
Removing exim4-config ...
dpkg: exim4-base: dependency problems, but removing anyway as you request:
 exim4-daemon-light depends on exim4-base (>= 4.69).
Removing exim4-base ...
 * Stopping MTA                                                                                                                                       /sbin/start-stop-daemon: warning: failed to kill 7246: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-base (--remove):
 subprocess post-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-daemon-light
 exim4-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
damien@mediabox:~$

```

I have tried sudo apt-get -f install to clean up, but I am a little lost as to the next step.   Does anyone have any ideas as to the next step I should take?

Cheers,
Damien

---

