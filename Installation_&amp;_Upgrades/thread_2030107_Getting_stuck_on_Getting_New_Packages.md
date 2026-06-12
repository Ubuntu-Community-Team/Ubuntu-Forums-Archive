---
title: "Getting stuck on Getting New Packages"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by sumithar on 2012-07-20
Trying to upgrade from Oneiric to 12.04 on a vmware virtual machine (base O/S is XP Pro 32 bit).

For nearly 20 hours it's getting new packages.

For the past 5 hours at least it's been
fetching file 1480 of 1480.

The orange bar with time remaining shows varying times
sometimes it will be 
About 1 second remaining, then, about 14 seconds, then it goes up, goes down.

Yesterday I tried once and after it was stuck on downloading package 979 of 1480 for a long time I cancelled and retried.

---

### Post by matt_symes on 2012-07-20
Hi

This could be anything. You may find it easier to backup and install a fresh 12.04.

Is it still trying to download/ install things ?

```
ps aux | grep -Ei  "apt|dpkg"
```

Did you update from the terminal or GUI ?

Kind regards

---

### Post by sumithar on 2012-07-20
Hi Matt,
I'm updating from GUI- the Update manager application.
Running that command gives
```

sumithar@ubuntu:~$ ps aux | grep -Ei "apt|dpkg"
root      6282  0.8  0.0   6988  1856 ?        S    Jul19  11:55 /usr/lib/apt/methods/http
root      6292  0.8  0.0   6988  1848 ?        S    Jul19  11:08 /usr/lib/apt/methods/http
sumithar 14148  0.0  0.0   4444   812 pts/1    S+   12:04   0:00 grep --color=auto -Ei apt|dpkg


```

When you say back up and install a fresh 12.04 you mean from a CD image?

---

### Post by matt_symes on 2012-07-20
Hi

> When you say back up and install a fresh 12.04 you mean from a CD image?Yes. Backup your data and install from a LiveCD/USB.
> 
root      6282  0.8  0.0   6988  1856 ?        S    Jul19  11:55 /usr/lib/apt/methods/http
root      6292  0.8  0.0   6988  1848 ?        S    Jul19  11:08 /usr/lib/apt/methods/httpIt looks like apt may have got stuck (possibly). You can try to debug it if you want to but i would suggest a fresh install.

Kind regards

---

### Post by sumithar on 2012-07-20
All righty, I will try that then, thanks!

---

### Post by sumithar on 2012-07-24
Hi,
I downloaded and created a CD of 12.04.  I put it in the drive, changed the boot sequence and booted up (I was surprised that the VM has a virtual bios too!)
It started me down the road to install from the CD but for some reason the option to upgrade the 11 to 12 is greyed out.  (See attachment).

you wouldn't happen to know why, would you?

---

### Post by matt_symes on 2012-07-24
Hi

I was under the impression that you could only use the alternate iso to upgrade versions. That may have changed though so I'm not sure why it is disabled.

Kind regards

---

### Post by sumithar on 2012-07-24
I downloaded and burnt the alt cd.  when I inserted it, it didn't give an option to upgrade the OS, went thru a series of steps and got to partition and format disks at which point I stopped.

---

### Post by sumithar on 2012-07-25
Hi,
I inserted the alternate CD after booting up in 11.10.  It saw it was an upgrade CD and kicked off the upgrade process.

Alas, it still goes back into that stupid window and gets stuck on getting new packages.  

I unchecked the option to connect to internet.

I don't understand, aren't all the packages on the CD itself?  Why can't it just do the upgrade "locally"?

I don't want to wipe and install- I've too many programs and their attendant settings and don't want to have to redo all that.

---

### Post by sumithar on 2012-07-26
I blanked out all the repositories and was able to complete the upgrade to 12.04.
I'm trying to run update manager to get the latest stuff from the internet but am running into this error message 
> It is impossible to install or remove any software.  Please use the package manager synaptic or run "sudo apt-get install -f" in a terminal to fix this issue at first. 

When I run the terminal command I get this
```
Removing libxml-sax-expat-perl ...
/var/lib/dpkg/info/libxml-sax-expat-perl.prerm: 12: /var/lib/dpkg/info/libxml-sax-expat-perl.prerm: update-perl-sax-parsers: not found
dpkg: error processing libxml-sax-expat-perl (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 libxml-sax-expat-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm about at the end of my tether...help!

Thanks!

---

### Post by sumithar on 2012-07-27
Just so I can mark this as closed...I manually deleted the offending package libxml-sax-expat-perl and was able to use update manager to get the latest greatest

---

