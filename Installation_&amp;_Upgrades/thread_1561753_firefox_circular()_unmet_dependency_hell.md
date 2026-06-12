---
title: "firefox circular(?) unmet dependency hell"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by tromanow on 2010-08-26
Have the same problem and can't uninstall, seemingly due to circular  dependencies among firefox, firefox-3.0, firefox-branding and  firefox-3.0-branding. Any idea how to break out of that?

# apt-get remove firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0: Depends: firefox
  firefox-3.0-branding: Depends: firefox-branding
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
olution).


apt-get remove firefox-3.0
Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 You might want to run `apt-get -f install' to correct these:
 The following packages have unmet dependencies:
   firefox: Depends: firefox-3.0
   firefox-3.0-branding: Depends: firefox-branding
 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
 olution).
 

apt-get remove firefox-branding
 Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  You might want to run `apt-get -f install' to correct these:
  The following packages have unmet dependencies:
    firefox-3.0-branding: Depends: firefox-branding
  E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
  olution).
  

apt-get remove firefox-3.0-branding
  Reading package lists... Done
   Building dependency tree
   Reading state information... Done
   You might want to run `apt-get -f install' to correct these:
   The following packages have unmet dependencies:
     firefox: Depends: firefox-3.0-branding but it's not going to be installed
   E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
   olution).

---

### Post by lovinglinux on 2010-08-26
Try 'apt-get -f install' with no packages.

---

