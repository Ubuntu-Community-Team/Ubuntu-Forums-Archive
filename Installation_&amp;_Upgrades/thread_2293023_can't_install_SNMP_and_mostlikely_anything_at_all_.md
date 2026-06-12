---
title: "can't install SNMP and mostlikely anything at all - Could not open file /var/lib/dpkg"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by casper8 on 2015-09-02
Hi all

ok so im trying to install SNMP.. and i got this error

Could not open file /var/lib/dpkg/status - open (2: No such file or directory)

so i tried this

```
[COLOR=#111111][FONT=Consolas]$ sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status[/FONT][/COLOR]$ sudo apt-get update
[COLOR=#111111][FONT=Ubuntu]**Incase you get this error E: Lists directory /var/lib/apt/lists/partial is missing.**[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]$ sudo mkdir /var/lib/apt/lists/partial[/FONT][/COLOR]
```

didn't help

so i than tried this

```
[COLOR=#111111][FONT=Ubuntu]Try first:[/FONT][/COLOR]sudo rm /var/lib/dpkg/available 
sudo sudo touch /var/lib/dpkg/available  
sudo sh -c 'for i in /var/lib/apt/lists/*_Packages; do dpkg --merge-avail "$i"; done'
[COLOR=#111111][FONT=Ubuntu]Dangerous, if previous instruction does not solve the problem...[/FONT][/COLOR]
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean [COLOR=#111111][FONT=Consolas]sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]
```

didn't help either..

at the moment this is the error when i try to do

sudo apt-get install snmp snmpd snmp-mib-downloader

```
0 to upgrade, 140 to newly install, 0 to remove and 0 not to upgrade.Need to get 0 B/46.6 MB of archives.
After this operation, 138 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 1.
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 82, <$__ANONIO__> chunk 1.
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extract templates from packages: 21%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extract templates from packages: 42%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extract templates from packages: 63%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extract templates from packages: 84%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extract templates from packages: 100%
dpkg: error: syntax error in triggers deferred file `/var/lib/dpkg/triggers/Unincorp' at character `'
PuTTYE: Sub-process /usr/bin/dpkg returned an error code (2)

```

i don't know what to do now?

---

