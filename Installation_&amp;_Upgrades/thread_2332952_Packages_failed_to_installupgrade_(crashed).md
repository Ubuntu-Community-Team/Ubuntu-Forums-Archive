---
title: "Packages failed to install/upgrade (crashed)"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by mistcloud-misty on 2016-08-05
My installer froze at some point with 'shim-signed' in it. I'm afraid to restart because of the list of 'broken' packages it lists, including 
 grub-efi-amd64
 grub-efi
 less
 shim-signed

I have tried to manually uninstall and reinstall to no avail - too broken to do so. I've tried to configure and reconfigure dpkg. I've removed locks as I came across them but they continue to pop up.

I need help fixing this and I'm worried rebooting will make ubuntu unbootable.

So basically: sudo apt-get -f install brings me to this:
```
arcane@arcane-X555LB:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mokutil shim
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing package grub-efi (--configure):
 dependency problems - leaving unconfigured
Setting up less (481-2.1ubuntu0.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package less (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
 less
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At some point shim-signed vanished from the list but I don't know when or what happened with that.

Any help? I'm desperately hoping I don't get a suspend crash before it's fixed.

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Hello;

Rightfully so to be concerned about the ability to RE-boot .

Let's make sure of the status of the package manager and what it relates to the system as a whole.
What results:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```
Then we look at what is to be done .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2016-08-05
sudo apt update:
```
arcane@arcane-X555LB:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                                
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                              
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                  
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                          
Hit:6 http://packages.overdrivenetworks.com rlw InRelease                                     
Hit:7 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease                        
Hit:8 http://dl.google.com/linux/chrome/deb stable Release              
Fetched 94.5 kB in 1s (79.2 kB/s)                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```


sudo apt full upgrade
```
rcane@arcane-X555LB:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  mokutil shim
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing package grub-efi (--configure):
 dependency problems - leaving unconfigured
Setting up less (481-2.1ubuntu0.1) ...No apport report written because the error message indicates its a followup error from a previous failure.

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package less (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
 less
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


And lastly...

```
arcane@arcane-X555LB:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mokutil shim
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing package grub-efi (--configure):
 dependency problems - leaving unconfigured
Setting up less (481-2.1ubuntu0.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package less (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
 less
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Hey ...

I see you also have this issue active on IRC . Let's see how this plays out on IRC .
I do have a couple of thoughts on this .. but they ( my thoughts) are in regards to upstart. here is systemd with 16.04 .. I do not know that relationship between the 2 .

upstart:
> 
Steve Langasek (vorlon) wrote on 2011-09-19:
all Ubuntu systems are supposed to have a /etc/init.d/.legacy-bootordering flag file telling update-rc.d (and /etc/init.d/rc) not to use insserv/startpar, which will fail terribly on Ubuntu.

to my mind then systemd is not happy with the upstart script(s) ??

[INDENT][INDENT]I am often amazed
[INDENT][INDENT][INDENT]at what I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2016-08-05
I do not have such a file in my init.d folder... (even looking for the hidden files with ctrl+h). 

My initial plan was to remove three shim-signed and grub packages (I don't know what 'less' is so I wasn't going to remove it) and then reinstall them. Unfortunately I am unable to do so - I tried to remove the AMD 64 file which seemed to remove the shim-signed file but didn't remove itself because of errors.

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Maybe

We can muddle through this together .

Agreed that the file " /etc/init.d/.legacy-bootordering  " does not exist in 16.04 .
{ 14:04
> 
sysop@1404mini:~$ ls -al /etc/init.d/.legacy-*
-rw-r--r-- 1 root root 0 May 19  2013 /etc/init.d/.legacy-bootordering
sysop@1404mini:~$

}

And further .. I think I had my wires crossed with that of a similar thread .. and the inserv file is of no matter in this instance .. Sorry 'bout that .

To your issue:
Let's find what has the lock on the package manager.
/var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable -->
Please open a terminal window to figure out the PID of the process that is holding the lock, by running:

```

sudo fuser -v /var/cache/debconf/config.dat


```
Take a note of the PID number and then, again in the terminal window

```
 
sudo kill PID_number
sudo kill -9 PID_number  # if the first doesn't work

```
Afterwards, run again
```

sudo apt update
sudo apt upgrade

```

see now if they run clean, and if so we try and install grub's support packages .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2016-08-05
I got another lock on dpkg after but removed that and did both commands with no errors. :)

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Maybe

We are home free ??

what now :
```

sudp apt -f install

```

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Maybe

We are home free ??

what now :
```

sudo apt -f install

```

[INDENT]maybe ?
[/INDENT]

---

### Post by mistcloud-misty on 2016-08-05
Well apparently there is nothing to be fixed...

```
arcane@arcane-X555LB:~$ sudo apt -f install
[sudo] password for arcane: 
Sorry, try again.
[sudo] password for arcane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mokutil shim
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

Strange.

Checked the dpkg list for all of them and it states there are no errors and shim-signed has been purged. 
```
arcane@arcane-X555LB:~$ dpkg -l grub-efi-amd64
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-======================================================================
ii  grub-efi-amd64                   2.02~beta2-36ubuntu3. amd64                 GRand Unified Bootloader, version 2 (EFI-AMD64 version)
arcane@arcane-X555LB:~$ dpkg -l grub-efi
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-======================================================================
ii  grub-efi                         2.02~beta2-36ubuntu3. amd64                 GRand Unified Bootloader, version 2 (dummy package)
arcane@arcane-X555LB:~$ dpkg -l less
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-======================================================================
ii  less                             481-2.1ubuntu0.1      amd64                 pager program similar to more
arcane@arcane-X555LB:~$ dpkg -l shim-signed
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-======================================================================
pc  shim-signed                      1.18~16.04.1+0.8-0ubu amd64                 Secure Boot chain-loading bootloader (Microsoft-signed binary)
arcane@arcane-X555LB:~$ 

```

Was all the problems just a filesystem complaint?

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty; Uh Huh ...

All I can think of at this time is RE-boot and see what happens . Will not hurt my feelings in the least if we wait here for others here to offer an opinion on rebooting .
However, upfront. If there are problems with grub in UEFI; I am not qualified to offer advise in this realm .
I have no UEFI experience.

[INDENT][INDENT]one of those times
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2016-08-05
Alright.. I rebooted (but first I manually tried to install each of the problem packages other than shim-signed just to be safe, and each said it was installed and up to date).

Asus then refused to let me boot into Ubuntu by screaming about a secure boot violation (whatever that is)... and sent me straight to windows... after a few reboots and a little digging in BIOS I disabled secure boot in the settings and was able to boot without issue into Ubuntu - the screen, albeit, looked a little different (smaller text, wider display).. but it works!

I believe the secure boot issue is due to the removal of shim-signed, which I recall having some bios warning when I rebooted after it first got automatically installed.

System seems to be working fine. :)

---

### Post by Bashing-om on 2016-08-05
mistcloud-misty' Yeah ..

I agree must be the shim file required  to make secure boot happy. As advised . No experience here . Oldfred has the skinny on this when you search the forum I bet you find the way to properly install the files.

Are the graphics now good or we need to open a new thread on the graphics ?

where there are solutions
there are no problems

---

### Post by mistcloud-misty on 2016-08-05
I've been using the intel graphics since 16.04 (nvidia driver causes permanent login loop) and haven't had any issues. Works great for everything I need it for (videos, basic games, some slightly intensive games). 

For the time being I'm just looking for the best possible stability.

---

