---
title: "Can't upgrade anymore, can anyone help??"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by chamont on 2007-03-01
Things have been humming along for months. Not sure what happened, but apt-get upgrade is completely broken. I'm just not sure where to go from here...I've spent way too much time messing around with this.

It seems to have something to do with libgnome-speech3, but I can't manage to remove that no matter what I try... Can anyone help out?

montyc@monty:~% sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2 firefox firefox-gnome-support libnspr4 libnss3 linux-restricted-modules-2.6.17-11-386 linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-common nvidia-glx
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/30.1MB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb (--unpack):
 unable to open files list file for package `libgnome-speech3': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by scxtt on 2007-03-01
check out the man page for apt-get:
```
[font=courier]       clean  clean clears out the local repository of retrieved package files. It removes  everything  but
              the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is
              used as a dselect(8) method, clean is run automatically. Those who do not  use  dselect  will
              likely want to run apt-get clean from time to time to free up disk space.[/font]
```

---

### Post by chamont on 2007-03-01
Wow, thanks for the quick reply!

I've cleaned and autocleaned too. I did it again just now for fun. Am I missing something from your reply?

```
montyc@monty:~% sudo apt-get clean
montyc@monty:~% sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2 firefox firefox-gnome-support libnspr4 libnss3 linux-restricted-modules-2.6.17-11-386 linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-common nvidia-glx
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://www.getautomatix.com edgy/main automatix2 1.1-2.16-6.10edgy_i386 [196kB]
Get:2 http://archive.ubuntu.com edgy-security/main firefox-gnome-support 2.0.0.2+0dfsg-0ubuntu0.6.10 [83.8kB]
Get:3 http://archive.ubuntu.com edgy-security/main libnspr4 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10 [158kB]
Get:4 http://archive.ubuntu.com edgy-security/main libnss3 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10 [786kB]
Get:5 http://archive.ubuntu.com edgy-security/main firefox 2.0.0.2+0dfsg-0ubuntu0.6.10 [9225kB]                                                                                                     
Get:6 http://archive.ubuntu.com edgy-security/restricted linux-restricted-modules-common 2.6.17.7-11.2 [20.2kB]                                                                                     
Get:7 http://archive.ubuntu.com edgy-security/restricted linux-restricted-modules-2.6.17-11-386 2.6.17.7-11.2 [7887kB]                                                                              
Get:8 http://archive.ubuntu.com edgy-security/restricted linux-restricted-modules-2.6.17-11-generic 2.6.17.7-11.2 [7682kB]                                                                          
Get:9 http://archive.ubuntu.com edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.7-11.2 [4066kB]                                                                                                 
Fetched 30.1MB in 3m13s (156kB/s)                                                                                                                                                                   
(Reading database ... dpkg: error processing /var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb (--unpack):
 unable to open files list file for package `libgnome-speech3': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by scxtt on 2007-03-01
see if you can delete (or not update) this file:

/var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb

so if it exists already, remove it - and if it doesn't, don't update automatix ...

also, see if there's a lock file anywhere in /var/cache/apt/archives or below ...

---

### Post by chamont on 2007-03-01
I was able to delete /var/cache/apt/archives/automatix2_1.1-2.16-6.10edgy%5fi386_i386.deb

Also, there was a lock file in /var/cache/apt/archives/

So they're both history...But 'sudo apt-get upgrade' fails just the same way.

Also, the lock file reappears every time. It's like apt-get (which calls dpkg??) is crashing midway through and leaving its lock file behind.

Is there some super-ruthless clean, destroy, rebuild apt-get flag I can use?

---

### Post by scxtt on 2007-03-01
i vaguely recall a problem somewhat similar when trying to reinstall proftpd ... i did a **sudo slocate -u**, **sudo slocate proftpd** and then removed ANYTHING proftpd related ... i would 1st suggest tho to NOT upgrade automatix since the entire problem may lay in that package ...

also, try to see what's up w/ the "libgnome-speech3" package ... (i don't use gnome or automatix or anything text-to-speech) ...

---

