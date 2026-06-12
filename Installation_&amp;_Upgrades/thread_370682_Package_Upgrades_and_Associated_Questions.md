---
title: "Package Upgrades and Associated Questions"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2007-02-26
I have been having a couple minor problems with my software packages and I'm hoping to get some answers.  I need to find out how to remove all traces of a package manually.  My samba package is messed up somehow, and synaptic cannot update or remove it because the uninstall script is messed up.  I could either overwrite it with someone else's install script if you can tell me how to get that, or just remove the whole thing so synaptic thinks it does not exist.  That will solve one of my problems.

The question I have is on the updating of packages.  How often are they updated?  My FlightGear install seems to be an old version, but I got it through synaptic.  I am thinking of downloading the newest source and compiling it, but I'd rather get it through synaptic if there is any chance of the ubuntu package being updated any time soon.  Also, my GTK-Gnutella program, also through synaptic, says "old version" on the status bar at the bottom.  Basically what I'm seeing is that ubuntu packages don't look like they are updated too frequently, and I'm wondering why?

---

### Post by 23meg on 2007-02-26
> I have been having a couple minor problems with my software packages and I'm hoping to get some answers. I need to find out how to remove all traces of a package manually. My samba package is messed up somehow, and synaptic cannot update or remove it because the uninstall script is messed up. I could either overwrite it with someone else's install script if you can tell me how to get that, or just remove the whole thing so synaptic thinks it does not exist. That will solve one of my problems.```
sudo apt-get --purge remove samba
``` should completely remove it.

> The question I have is on the updating of packages. How often are they updated?Stable releases of Ubuntu only get security updates. In other words, you don't get new versions of software until the next release, with the exception of security related updates for software in the Main component.

[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by nexus_2006 on 2007-02-26
Nope.  I'v tried every sort of automated removal that exists AFAIK.  I need somewhere I can lookup the exact files and where they are put and also what kinds of changes the install makes to system config files.  This thing is busted.

```
nexus@Lithium:~$ sudo apt-get --purge remove samba
Password:****************
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 125701 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
nexus@Lithium:~$

```

Thanks for the info though. Guess I will be compiling the new version of FlightGear.  Any advice Ubuntu specific?  I'v compiled programs before, though not FlightGear and not on Ubuntu.

---

### Post by nexus_2006 on 2007-02-28
figured it out!!! 

I looked really closely at the error message, deleted the file it mentioned, the package was able to remove itself.  Installed the newest one, everything's kosher.  I had to remove /etc/rc2.d/K(something or other sama something....)

---

