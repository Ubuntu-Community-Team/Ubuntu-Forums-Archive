---
title: "Packages missing when installing subversion"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by ralfzurich on 2012-04-08
Hi to everybody,

sorry in advance should I post this message in the wrong forum / way or similar. I am a newbee to Ubuntu and Ubuntu forums

I just managed to install Ubuntu 11.10 on i386 and am now struggling to get subversion installed. I found this one [http://ubuntuforums.org/showthread.php?t=1876156](http://ubuntuforums.org/showthread.php?t=1876156), executed it and now get the following messages. Originally some of them were in German. I translated them. So some of the messages might not be phrased exactly as if the language was English originally:
```

$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This could mean that you 
requested an impossible situation or, if you are using the unstable distribution,
that some necessary packages have not been created or did not leave incoming.
Maybe the following information helps you to resolve the situation:

The following packages have unsatisfied dependencies :
 subversion : Depends: libsvn1 (= 1.7.4-1+WANdisco) but shall not be installed
              Depends: libneon27-gnutls (>= 0.29.0) but is not installable
E: Unable to correct problems, you have held broken packages.

```Does anybody have some advice?

Thanks in advance & Kind regards
Ralf

---

### Post by jerrrys on 2012-04-09
Can't help you with subversion. But open a terminal and try this:

sudo apt-get install -f

This command will attempt to fix broken packages.

---

### Post by ralfzurich on 2012-04-09
Here is the result:

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 updated, 0 newly installed, 0 to be removed and 0 not updated.

```Did not help me with subversion. The result of ```
$ sudo apt-get install subversion
``` is still the same

Anyway thanks for your hint

Kind regards

---

### Post by ralfzurich on 2012-04-09
Issue resolved. Tha installation did not automatically amend the following packages to /etc/apt/sources.list:

```

deb http://de.archive.ubuntu.com/ubuntu oneiric main restricted universe multiverse deb-src http://de.archive.ubuntu.com/ubuntu oneiric main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu oneiric-updates main restricted universe multiverse 
deb-src http://de.archive.ubuntu.com/ubuntu oneiric-updates main restricted universe multiverse  
deb http://de.archive.ubuntu.com/ubuntu oneiric-security main restricted universe multiverse 
deb-src http://de.archive.ubuntu.com/ubuntu oneiric-security main restricted universe multiverse

```

---

### Post by Amof on 2012-05-02
Kudos. That fixed my problem as well. It seems the 12.04 installer didn't disable all my third party repositories and when I was trying to install my software (LibreOffice) I was getting the same error message. 

If you have this issue:
[LIST]
[*] use Synaptic to dump out all third party repositories
[*] Open ```
/etc/apt/sources.list
``` and MAKE SURE all third party Repositories are removed. (I had one that didn't show in Synaptic)
[*] ```
sudo apt-get update && sudo apt-get install upgrade
```
[*] Done
[/LIST]

---

