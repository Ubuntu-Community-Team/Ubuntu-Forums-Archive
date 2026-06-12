---
title: "Upgrade to 10.04 caused a few problems"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2010-05-06
Just upgraded to 10.04 and have some problems:

[LIST=1]
[*]E: /var/cache/apt/archives/bugzilla3_3.2.5.1-2_all.deb: subprocess new pre-installation script returned error exit status 2


[*]Firefox starts as background task, but never shows anything on screen.
[*]Prism based applications derived from web pages used to work but do not work now. (possibly related to firefox failure...?).
[/LIST]

Computer is AMD Dual-core 64-2300 running 32-bit Ubuntu-Gnome 10.04 with 1GB RAM and 500GB HDD.

_._

---

### Post by arvevans on 2010-05-06
More Info:
[INDENT]arv@arv-desktop:~$ firefox
Attempting to load the system libmoon 
Segmentation fault
arv@arv-desktop:~$ [/INDENT]

---

### Post by arvevans on 2010-05-06
Further Information:

[INDENT]Uninstalled "libmoon" and now Firefox works.[/INDENT]

Do I need libmoon and it's support for "Silverlight" applications,
or can I just forget it with no consequences?
_._

---

### Post by arvevans on 2010-05-06
Bugzilla3 still buggy:

I removed it and then tried installing again using apt-get...setup part still exits with Error-2

[INDENT]arv@arv-desktop:~$ sudo apt-get install bugzilla
[sudo] password for arv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bugzilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bugzilla3
E: Package bugzilla has no installation candidate
arv@arv-desktop:~$ sudo apt-get install bugzilla3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libcppunit-1.12-1 python-numeric
  linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  bugzilla3-doc libnet-ldap-perl libmime-tools-perl libhtml-scrubber-perl
  libauthen-radius-perl libsoap-lite-perl patchutils
The following NEW packages will be installed:
  bugzilla3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,265kB of archives.
After this operation, 21.5MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bugzilla3.
(Reading database ... 341397 files and directories currently installed.)
Unpacking bugzilla3 (from .../bugzilla3_3.2.5.1-2_all.deb) ...
Setting up bugzilla3 (3.2.5.1-2) ...
Installing new version of config file /etc/bugzilla3/index.html ...
Installing new version of config file /etc/cron.daily/bugzilla3 ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla3.conf
sanity check failed for dbc_dbuser.
sanity check failed for dbc_dbuser.
Please run /usr/share/bugzilla3/lib/checksetup.pl yourself.

Processing triggers for python-central ...
arv@arv-desktop:~$ /usr/share/bugzilla3/lib/checksetup.pl
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/pre-checksetup.d
run-parts: executing /etc/bugzilla3/pre-checksetup.d/10fixcompiledtemplates
run-parts: executing /etc/bugzilla3/pre-checksetup.d/30copyetcskins
run-parts: executing /etc/bugzilla3/pre-checksetup.d/30copyetctemplate
run-parts: executing /etc/bugzilla3/pre-checksetup.d/50patchtemplatefordebian
/etc/bugzilla3/pre-checksetup.d/50patchtemplatefordebian: 26: cannot create /var/lib/bugzilla3/template/fr/default/search/search-plugin.xml.tmpl: Permission denied
run-parts: /etc/bugzilla3/pre-checksetup.d/50patchtemplatefordebian exited with return code 2
arv@arv-desktop:~$ ^C
arv@arv-desktop:~$ 
[/INDENT]

Seems that it is still broke.  Is anybody looking at bugzilla?  We need it in order to submit bugs regarding the new update.  Without it the Debian menu item "Report A Problem" is also broken.

---

### Post by arvevans on 2010-05-07
Bugzilla3 still broken.

---

### Post by ken78724 on 2010-05-07
Apologies, I have an acer laptop and Mirus PC booged down with incompleted tries at installing or updating with Lucid 10.04. my query appears 

closer to yours than others I see; regardless I ask all to bare with the difference from the main thread. unbeknowingly I disabled my system folder icon, logout icon, firefox icon, opera, open office, thunderbird icons on my desktop; I believe this happened after I started a Lucid 10.04 LTS 64 amd on my ACER laptop. The only symptom allied with this was a hyper active keyboard. It was simultaneous with a hot night, last night herein Austin texas.

I cannot find a forum discussing this or bug report giving a solution for this bug related to an aborted download, brought to a stop at the point where it says how many programs will be removed and how many Lucid will reinstall. Maybe that is where the critical repopulating program was disabled and then the hyperactive keyboard began a little more furiously than normal. Or, it could be my blood was purring too hard. regardless, I cannot figure out where to turn or even how to do an incident report.

I do have access to terminal but not to Systems files or another PC or laptop to begin a work around.
2nd problem is on my Mirus PC 80 gig which has a grub loader locked that prevents a 10.04 install from 9.04. finally, I went back to 8.04 okay but cannot install 10.04 ubu; 10.04 ubuStudio or 10.04 Kubuntu. All this makes it tough to do a work around. 

Any/all help will be appreciated.  
thanks a bunch

---

### Post by emlinux on 2010-05-07
10.04 LTS Graphics problem on Dell D800 laptop w/ Nvidia Geforce4 Ti graphics chip.
Worked ok on 8.04 and other previous upgrades before 10.04.
10.04 kernel 2.6.32 has a problem - icons, task bar and mouse pointer
are pixelated and distorted, but text and background pix are OK.
10.04 kernel 2.6.31 has a different (minor) problem - all is ok except that horiz and vert size is off.
X.log shows missing nouveau_vieux_dri.so
Tried re-installing xserver-xorg-video-nouveau and libdrm-nouveau1, 
but this did not install this file or fix the problem.

---

### Post by arvevans on 2010-05-07
I see that a couple of people have hijacked my thread.  So, just to 
keep the topic focused on my report...

[INDENT]**Bugzilla3 is still broken**
[/INDENT]

Arv
_._

---

### Post by arvevans on 2010-05-09
OK...looks like nothing is happening toward fixing Bugzilla3.
Might as well close this and get it off the list of open problems.

If Bugzilla3 worked I could submit a bug report, but guess it is 
not going to happen.

_._

---

