---
title: "Cannot install krb5-user"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by cbreaker on 2007-04-07
Greetings,

I'm not new to linux but this is the first time I've used apt and Ubuntu, so bear with me.

I installed a fresh 6.10-server with no optional packages during install.   I then installed sshd and samba, and now I want to install kerberos support.

This is my problem:

```
root@MANTLE:~# apt-get install krb5-user 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.2 is to be installed
             Depends: libkadm55 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.2 is to be installed
E: Broken packages
root@MANTLE:~# 
```

I don't even know where to go to manually fix this to force it to be installed.

Any ideas?

Thanks.

---

### Post by pt123 on 2007-04-11
You need to enable more repos in you your /etc/apt/sources.list

---

### Post by simonb_sgp on 2007-04-13
The error message I saw was:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-doc
E: Package krb5-user has no installation candidate[/COLOR]

apt-get install krb5-doc returned:

[COLOR="blue"]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR]

The install of krb5-doc then worked fine, but I cannot find /etc/krb5.conf to complete the instructions descibed in [http://ubuntuforums.org/archive/index.php/t-91510.html](http://ubuntuforums.org/archive/index.php/t-91510.html) 

Any idea?

Thank you.

---

### Post by pt123 on 2007-04-13
That guide is missing a few files, there is a more expanded version to get active directory working with a similar title to that thread try searching for it.

---

### Post by simonb_sgp on 2007-04-13
Thanks, however, all the how-to articles are based on krb5-user/config. I cannot get those libraries to load - apt-get install krb5-doc replaces them it seems (certainly -user).

The issue is now that I cannot find the krpb5.conf file to make the changes.

Other links of interest are:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

I can find nothing that deals with what seems to be the 'latest' version of krb5.

Thanks.

---

