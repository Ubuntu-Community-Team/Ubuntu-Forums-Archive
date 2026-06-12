---
title: "upgrading fiasco 8.04 to 8.10"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by king vash on 2008-11-05
I started upgrading my laptop from 8.04 to 8.10 download went smoothly and everything was going fine. Then my laptop was shutdown. 

I booted selected one of the recovery kernals in grub and dropped to root shell. 
I tried "apt-get upgrade" it complained about "dpkg --configure -a"
I ran "dpkg --configure -a" it complained about to many unlinked (it had a different work) programs. I increased "--abort-after" to 200 and ran again. 
I tried "apt-get upgrade" "apt-get -f dist-upgrade" and couple of other things but nothing is working. 

I have a whole lot of packages download but almost all depend on uninstalled packages. "apt-get upgrade" will not connect to update the packages. I have a 8.10 cd but do not want to clean install. I want to keep my files and programs. 
What should I do?

---

### Post by pastalavista on 2008-11-05
I upgraded 8.04 to 8.10 with-- ```
sudo aptitude dist-upgrade
```
but before you do that run ```
sudo apt-get update -d
```
but before you do any of that, boot in recovery mode and select the option 'repair broken packages'

---

### Post by king vash on 2008-11-05
I tried running "repair broken package" it did nothing I will try "apt-get update -d" next

---

### Post by pastalavista on 2008-11-05
you might also try: ```
sudo aptitude reinstall -a
``` or.. ```
aptitude full-upgrade
``` they deny it, of course, but aptitude really does have mad cow powers.. ;)```
 man aptitude
```

---

