---
title: "Partially installed packages"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Crinos512 on 2008-03-08
I have an issue with partially installed packages that will not complete. anyone care to try to trouble shoot this with me?? :)

```

crinos@Fortress:~$ [COLOR="Blue"]sudo aptitude --sort "installsize" --with-recommends full-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following partially installed packages will be configured:
  gnome-mount gnome-volume-manager hal network-manager network-manager-gnome network-manager-kde
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[COLOR="Red"]Setting up hal (0.5.10+git20080301-1ubuntu1) ...
 * Reloading system message bus config...                                                                                                                                      [ OK ]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1[/COLOR]
dpkg: dependency problems prevent configuration of gnome-mount:
[COLOR="Magenta"] gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured[/COLOR]
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-kde:
 network-manager-kde depends on network-manager (>= 0.6.2); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-kde (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-volume-manager
 network-manager
 network-manager-gnome
 network-manager-kde
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hal (0.5.10+git20080301-1ubuntu1) ...
 * Reloading system message bus config...                                                                                                                                      [ OK ]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-kde:
 network-manager-kde depends on network-manager (>= 0.6.2); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-kde (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-volume-manager
 network-manager
 network-manager-gnome
 network-manager-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

so I tryed configuring hal manually...

```

crinos@Fortress:~$ [COLOR="Blue"]sudo dpkg-reconfigure hal[/COLOR]
/usr/sbin/dpkg-reconfigure: hal is broken or not fully installed


crinos@Fortress:~$ [COLOR="#0000ff"]sudo dpkg --configure hal[/COLOR]
Setting up hal (0.5.10+git20080301-1ubuntu1) ...
 * Reloading system message bus config...                                                                                                                                      [ OK ]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hal

```

any thoughts???

---

### Post by oldos2er on 2008-03-08
Have you tried "sudo aptitude install -f" ?

---

### Post by Crinos512 on 2008-03-08
Just did.... looks similar.

```

crinos@Fortress:~$ sudo aptitude install -f
[sudo] password for crinos:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following partially installed packages will be configured:
  gnome-mount gnome-volume-manager hal network-manager network-manager-gnome network-manager-kde
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up hal (0.5.10+git20080301-1ubuntu1) ...
 * Reloading system message bus config...                                                                                                                                      [ OK ]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-kde:
 network-manager-kde depends on network-manager (>= 0.6.2); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-kde (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-volume-manager
 network-manager
 network-manager-gnome
 network-manager-kde
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hal (0.5.10+git20080301-1ubuntu1) ...
 * Reloading system message bus config...                                                                                                                                      [ OK ]
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-kde:
 network-manager-kde depends on network-manager (>= 0.6.2); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-kde (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-volume-manager
 network-manager
 network-manager-gnome
 network-manager-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

I did have a oops earlier where I overwrote all of the /usr and sub directories permissions to root.... I had to 

[COLOR="Blue"]sudo chmod -R 755 /usr[/COLOR]

I also did 
[COLOR="#0000ff"]sudo chmod -R 755 /usr/bin 
sudo chmod -R 755 /usr/sbin 
sudo chmod -R 755 /usr/local
sudo chmod -R 755 /usr/share
[/COLOR]
Just to be sure.... Maybe a file didn't get the memo?

---

### Post by Crinos512 on 2008-03-11
Any other ideas?

I figured that UID 0 is root (or sudo)
and UID 107 is probably my login...

why would root not be able to access a file my login has rights to?

---

### Post by Crinos512 on 2008-03-13
um bump?... still having the problem.

Anyone care to post the Owner and Permissions of the files related to hal so that I can compare them?

---

### Post by zvacet on 2008-03-14
```
sudo dpkg --configure -a
```

or 

```
sudo apt-get install --reinstall hal
```

---

### Post by Crinos512 on 2008-03-14
> **zvacet said:**
> sudo dpkg --configure -a

```

Setting up hal (0.5.10-5ubuntu7) ...
chown: cannot access `/var/run/hal': No such file or directory
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio-module-hal:
 pulseaudio-module-hal depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing pulseaudio-module-hal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 pulseaudio-module-hal

```

> sudo apt-get install --reinstall hal

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 265 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up hal (0.5.10+git20080301-1ubuntu2) ...
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations foruid 107 (requires org.freedesktop.policykit.read)
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations foruid 107 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio-module-hal:
 pulseaudio-module-hal depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing pulseaudio-module-hal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 pulseaudio-module-hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Crinos512 on 2008-03-16
no response?

dang... OK then, if I reinstall from a CD will it wipe out my home directory and all of my installed programs?

---

### Post by Pumalite on 2008-03-16
If you have a separate /home partition, you can use it in your new installation. If not, you can save /home and reinstall it. Your programs you will have to reinstall, but some of them you can save with AptOnCD: [http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)

---

### Post by Crinos512 on 2008-03-17
heh... oh hell.

can I resize my current partition and move my home to a new one created from the freed space?

(and how could I do that?)

barring that I am going to attempt to copy my [COLOR="Blue"]/home[/COLOR] and [COLOR="#0000ff"]/var/cache/apt/archives[/COLOR] across my home network to another PC... if I can get my PC to see the other one.

---

### Post by Shinku's fan on 2008-03-26
[QUOTE=Crinos512;4517855]```

Setting up hal (0.5.10-5ubuntu7) ...
chown: cannot access `/var/run/hal': No such file or directory
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio-module-hal:
 pulseaudio-module-hal depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing pulseaudio-module-hal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 pulseaudio-module-hal

```

I'm pretty sure by now you reinstalled or whatnot, and probably this isn't the problem... but I recently upgraded to hardy beta and was getting a similar problem with the hal package.
If you notice it tells you that it can't find  `/var/run/hal', now after a bit of guessing i thought maybe for some reason someone assume it existed, so I opened up nano and created a blank file named hal in /var/run as root and ran aptitude again, et voila, it worked.

just my two cents... :)

---

### Post by Crinos512 on 2008-03-26
yeah, I've completely wiped my HDD and reinstalled from scratch.

This time I have a separate /home partition so I can recover gracefully from future glitches.

---

### Post by sds50 on 2008-04-10
I just had a similar problem, and solved it rather simply.

The errors are all about policy kit authorisation, especially "uid 0 is not authorized to..." implies that something is set wrong in the .policy files. As a quick fix, I simply reinstalled any package with a name relating to policy kit, and everything started working fine again.

I'm not sure which of them did it, although I suspect the policykit package. One could probably achieve the same effect by digging in .policy files, but I can't be bothered.

hope that helps anyone with the same problem.

---

### Post by scarneiro on 2008-04-26
Hi...

Did you try setuid the Policykit files ?  I had a similar problem and it worked...  I set the setuid permission on all the files on the /usr/lib/polickit...


Hope that helps you !

Best Regards,

Sebastián Carneiro

---

### Post by Shaoline on 2008-04-28
I can also add to this, as I had close to exact same problem as these other people.

I just did a search in Synaptic for "policykit" and reinstalled the "policykit" and the "policykit-gnome" (if I recall the names correctly) and problem was solved!

---

### Post by esox123 on 2008-06-19
I just had a similar problem. Caused coz I copied /etc/group from an existing ubuntu 8.04 system (recently upgraded from ubuntu 7) to a new  8.04 install ... and ....

+ grep polkituser /etc/group <== copied from the upgraded system
polkituser:x:125:
+ grep polkituser /etc/group.orig <== from the brand new 8.04 install
polkituser:x:122:

Turned out that in my case the thing about ....
"uid 0 is not authorized to read authorizations for uid 107" 
.... was a red herring. 

The real clue was the message:
"polkit-read-auth-helper: needs to be setgid polkituser"

re-instating the "new install" /etc/group (and then appending my local group IDs) fixed my problem

---

### Post by known on 2008-07-12
I fixed polkituser hell on LXDE by doing 

apt-get remove --purge pcmanfm

I downloaded deb package (stable version)from pcmanfm.sf.net 
dpkg -i pcmanfm.deb

---

