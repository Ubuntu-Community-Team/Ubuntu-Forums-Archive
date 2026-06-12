---
title: "Software index is broken"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by kathrin on 2007-08-20
I've got an upgrade icon on my tool bar and when I go to upgrade it brings up:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue first.

I have done both of these things the former being useless, Synaptic package manager has shown me that Gnome games is the broken package but I cannot remove it or anything. When I did the latter this happened:

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic openoffice.org-draw libstlport5.1
  openoffice.org-math libwps-0.1-1 linux-headers-2.6.20-15 myspell-en-za
  openoffice.org-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-games
Suggested packages:
  gnome-hearts
Recommended packages:
  gnome-games-extra-data
The following packages will be upgraded:
  gnome-games
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1558kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 11071 package `gnome-games':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Can anyone help, please!!! 

Thanks 

kathrin

---

### Post by forestpixie on 2007-08-20
I've not been in a position to need to do this but I had a look on [google]("http://www.google.co.uk/search?source=ig&hl=en&q=dpkg%3A+parse+error%2C+in+file+ubuntu&btnG=Google+Search") 
and found a few that are similar errors - looked at these

[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)
[https://answers.launchpad.net/ubuntu/+question/9593](https://answers.launchpad.net/ubuntu/+question/9593)
[http://ubuntuforums.org/archive/index.php/t-307510.html](http://ubuntuforums.org/archive/index.php/t-307510.html)

It would appear that you can do two things replace the status file with the old one (if you have an old one) or clear the information the system holds.

to do the first open a terminal and do these two enter after each
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

then run this to update and upgrade
```

sudo apt-get update && sudo apt-get upgrade
```

or to do the second one the command apparently is ( check man dpkg to be sure for yourself) 

```
sudo dpkg --clear-avail && sudo apt-get update
```

then see if you can upgrade with
```

sudo apt-get upgrade
```

---

### Post by kathrin on 2007-08-20
Thanks I had a look in the status file and there was a weird character in a dependency of gnome-games called guile-lib, where the weird character was in place of 'l' in lib. I just removed the weird character and put an 'l' in and it works. Thanks again

---

