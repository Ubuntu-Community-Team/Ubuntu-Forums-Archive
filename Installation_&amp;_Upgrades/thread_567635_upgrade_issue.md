---
title: "upgrade issue"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by ndihmo on 2007-10-04
Hi!
I'm having an issue with the #aptitude full-upgrade command.

this is what i get:

```

root@host:/home/user# aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  bind9-host cups-pdf cupsys dnsutils evolution-data-server evolution-data-server-common hal hal-device-manager kdebase-bin kdebase-kio-plugins kdesktop 
  libbind9-30 libcamel1.2-10 libdns32 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 
  libegroupwise1.2-13 libexchange-storage1.2-3 libgda3-3 libgda3-common libglade2.0-cil libglib2.0-cil libgtk2.0-cil libhal-storage1 libisc32 libisccc30 
  libisccfg30 libkonq4 liblwres30 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono2.0-cil libnautilus-extension1 libruby1.8 libssl0.9.8 libx11-6 libx11-data libx11-dev libxml2 libxml2-utils lsb-release mono-common 
  mono-gac mono-jit mono-runtime nautilus nautilus-data ntpdate openssl ppp python-libxml2 ruby1.8 synaptic 
67 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/37.1MB of archives. After unpacking 3727kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 131128 files and directories currently installed.)
Preparing to replace cupsys 1.3.2-1ubuntu3 (using .../cupsys_1.3.2-1ubuntu4_i386.deb) ...
Ignoring nonregistered document cupsys
 * Stopping Common Unix Printing System: cupsd                                                                                                        [ OK ] 
Unpacking replacement cupsys ...
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/libcupsys2/CREDITS.txt', which is also in package libcupsys2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
root@host:/home/user#

```

Can anyone help me?

thank you.
Edmond.

---

### Post by Pumalite on 2007-10-04
Did you run:

sudo dpkg --configure -a

---

### Post by ndihmo on 2007-10-04
yes, I just did it but there was nothing changed.

help :(

---

### Post by Pumalite on 2007-10-04
To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________

---

### Post by n3tfury on 2007-10-04
i'm on gutsy and it's telling me there's an upgrade, but when i do it says it can only do a partial upgrade.  anyway i can see details of this "error"?

---

### Post by Pumalite on 2007-10-04
I have Gutsy Beta installed and get the message of 'partial updates' all the time. I accept the partial updates and keep on going.

---

### Post by n3tfury on 2007-10-04
> **Pumalite said:**
> To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________

that seems like more of a workaround than a fix.  i'm getting the same error as the OP after i successfully updated everything else.  see image:

---

### Post by n3tfury on 2007-10-04
thanks to samnsparky's post about the same issue, i found this:

STEP 1: Run

```

 # dpkg -i --force-overwrite /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb
```

STEP 2: Since conflict has already been resolved (forcefully), proceed with normal installation
Run :
```
  # apt-get -f install
```

---

### Post by Paradigm_Shift on 2007-10-05
I ran into the same problem that ndihmo reported. I got around the problem by doing the following:

1. uninstalling cupsys
sudo apt-get remove cupsys

2. updating the sources
sudo apt-get update

3. performing a dist-upgrade
sudo apt-get dist-upgrade

4. Once all of that was finished, I re-installed cupsys.
sudo apt-get install cupsys

---

### Post by ndihmo on 2007-10-05
Thank you gyus. My problem was solved with 

# dpkg -i --force-overwrite /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb

and after the with

# apt-get -f install




Thank you all!!!!

---

### Post by owlhoot on 2007-10-07
Thanks for this thread guys. I had a partial install hang on me and this got me through it and back into synaptic. Then I simply went in and did a search for the "installed" program after editing the status file and uninstalled it using synaptic. That seems to have gotten me going again.

---

### Post by leon_mcnichols on 2007-10-08
leonardo@Hal:~$ dpkg --configure -a


dpkg: requested operation requires superuser privilege
leonardo@Hal:~$ 
leonardo@Hal:~$ 
leonardo@Hal:~$ sudo dpkg --configure -a
[sudo] password for leonardo:
rondleonardo@Hal:~$ 

KABOOOM!!!

Whoops, command-not-found has crashed! Please file a bug report at:
[https://bugs.launchpad.net/ubuntu/+source/command-not-found](https://bugs.launchpad.net/ubuntu/+source/command-not-found)
Please include the following information with the report:
No module named CommandNotFound
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 10, in <module>
    from CommandNotFound import CommandNotFound
ImportError: No module named CommandNotFound
Python version: 2.5.1 final 0
bash: editted: command not found
leonardo@Hal:~$ 
This is what I got when I tried to run sudo dpkg --configure -a   because I kept getting a cannot install on certain updates.

---

### Post by flashingcurser on 2007-10-08
full-upgrade?

dist-upgrade

---

### Post by leon_mcnichols on 2007-10-09
257 upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
186 not fully installed or removed.
Need to get 0B/245MB of archives.
After unpacking 39.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 257080 files and directories currently installed.)
Preparing to replace kmail 4:3.5.6-0ubuntu6 (using .../kmail_4%3a3.5.7enterprise20070926-0ubuntu1_i386.deb) ...
Unpacking replacement kmail ...
dpkg: error processing /var/cache/apt/archives/kmail_4%3a3.5.7enterprise20070926-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/config.kcfg/customtemplates_kfg.kcfg', which is also in package kpilot
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kmail_4%3a3.5.7enterprise20070926-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
leonardo@Hal:~$ 
Thats wha I'm getting now when I go thru term and did the sudo apt-get upgrade  
And it was a distro update

---

### Post by leon_mcnichols on 2007-10-09
(Reading database ... 289404 files and directories currently installed.)
Preparing to replace kitchensync 4:3.5.6-0ubuntu6 (using .../kitchensync_4%3a3.5.7enterprise20070926-0ubuntu2_i386.deb) ...
Unpacking replacement kitchensync ...
dpkg: error processing /var/cache/apt/archives/kitchensync_4%3a3.5.7enterprise20070926-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/ksync/ksyncui.rc', which is also in package ksync
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kitchensync_4%3a3.5.7enterprise20070926-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Thats what I get now after fixing the other issues and bypassing some of the other packages.  Anyone got a fix for this one? Besides applying Thor's Hammer to the Drive?

---

### Post by plm99 on 2007-10-20
I'm getting the exact same error, has any figured this one out yet?

---

### Post by ndihmo on 2007-10-20
> **ndihmo said:**
> Thank you. My problem was solved with 

# dpkg -i --force-overwrite /var/cache/apt/archives/**cupsys_1.3.2-1ubuntu4_i386.deb**

and after the with

# apt-get -f install




Thank you all!!!!

in you case you need to give the name of the package that is givin you problems

dpkg -i --foce-overwrite /var/cache/apt/archive/<namepackage>
apt-get -f install

---

### Post by procrastinator on 2007-10-22
I'm having a variant of this problem, with the added flavor of being unable to boot and having nothing more than a malfunctioning terminal. dpkg won't run ("read-only file system") and neither will much else. Is there somehow I can recover my installation through the live-cd?

---

### Post by procrastinator on 2007-10-22
I've booted from the live-cd and mounted and chroot'ed into my installation. So far so good. I can then run dpkg --configure -a, and at first it seems to be working as it should -- it sets up different packages. But then it reaches "Caching application data..." where it hangs. My harddisk seems to keep working hard, but after two hours I gave up and decided to try something else. Am I too impatient, or have I got other problems?

My dpkg-log:[http://pastebin.com/m2d84f149](http://pastebin.com/m2d84f149)

---

