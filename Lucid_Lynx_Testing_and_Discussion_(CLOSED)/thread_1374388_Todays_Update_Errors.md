---
title: "Todays Update Errors"
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-01-06
When using the command

sudo aptitude update && sudo aptitude safe-upgrade

I get the following errors. Anyone else?

```
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by VMC on 2010-01-06
> **sparker256 said:**
> When using the command

sudo aptitude update && sudo aptitude safe-upgrade

I get the following errors. Anyone else?

```
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

Yes, I did get the language not set output.

---

### Post by VMC on 2010-01-06
I just went to System>Admin>Language Support and got language not installed completely. I checked remind me later.

---

### Post by ronacc on 2010-01-06
I got a gnome menus crash with a set locale error on startup but everything seems to be functioning normally , updated with synaptic and no errors or warnings .

---

### Post by dagrump on 2010-01-06
I got that several times during this evenings updates. After reboot gdesklet launcher bar errors out, & for some reason the stupid box won't connect to wireless. 
So I sure won't be updating any more boxes tonight, & of course I ran updates yesterday that kicked synaptic in the head...
So much for the boredom factor. I booted this one back to 8.10 to make sure it wasn't the network, oh well, I'm going go watch the KU kids thump some Ivy league kids.
This machine is really starting to tick me off!!

---

### Post by BwackNinja on 2010-01-06
I've got this too, mildly annoying and waiting for it to be fixed.

---

### Post by dino99 on 2010-01-07
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/504174](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/504174)

---

### Post by jppr on 2010-01-07
[https://launchpad.net/ubuntu/lucid/+source/gnome-menus/2.28.0.1-0ubuntu7](https://launchpad.net/ubuntu/lucid/+source/gnome-menus/2.28.0.1-0ubuntu7)

---

### Post by nebosuke on 2010-01-07
You can try the fix proposed here.
[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/504198](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/504198)

---

### Post by zika on 2010-01-07
[Title is a bit off topic because I was not sure what was going on at that moment](http://ubuntuforums.org/showthread.php?t=1374149). Everything went away as suddenly as it suddenly came...

---

### Post by dino99 on 2010-01-07
> **dino99 said:**
> [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/504174](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/504174)

Fix released in eglibc 2.11~20100104-0ubuntu2, but still waiting it  :(

---

### Post by philinux on 2010-01-07
Fixed with this from bug report. Also had to remove plymouth as I had graphics corruption. Talk about psychedelic, lynx on speed.

locale-gen --purge
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

---

### Post by dino99 on 2010-01-07
ok
locale is regenerated with this command, but i doubt that problem is solved because it's still the same package in repo.

about hard buggy package: [http://packages.qa.debian.org/e/eglibc.html](http://packages.qa.debian.org/e/eglibc.html)

---

### Post by philinux on 2010-01-07
> **dino99 said:**
> ok
locale is regenerated with this command, but i doubt that problem is solved because it's still the same package in repo.

about hard buggy package: [http://packages.qa.debian.org/e/eglibc.html](http://packages.qa.debian.org/e/eglibc.html)

Lynx is booting fine now though and no errors at all from desktop.

---

### Post by dino99 on 2010-01-07
> **philinux said:**
> Lynx is booting fine now though and no errors at all from desktop.

My bad, you're right Phil
will see at next boot.

---

### Post by darco on 2010-01-07
I am still seeing this after a safe-upgrade:

```
 lucid@lucid-desktop:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  empathy 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
E: Problem executing scripts DPkg::Post-Invoke 'if [ -x /usr/sbin/localepurge ] && [ $(ps w -p $PPID | grep -c remove) != 1 ]; then /usr/sbin/localepurge; else exit 0; fi'
E: Sub-process returned an error code
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

