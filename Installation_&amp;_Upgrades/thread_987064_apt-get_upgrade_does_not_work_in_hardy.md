---
title: "apt-get upgrade does not work in hardy"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by tekknokrat on 2008-11-19
I have done a fresh install of xubuntu-desktop 8.04 yesterday because downgrading inteprid to hardy worked not that well.
I need to downgrade because of [bluetooth issues](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=intrepid+bluetooth&search=Search+Bug+Reports&field.scope=all&field.scope.target=).

One thing that I dont understand now is that the "Upgrade Manager" shows me new updates to be installed.
As I am a commandline freak I only used to "apt-get upgrade -s" to show the installed updates and afterwards "apt-get upgrade -y" to install them but this doesnt work for this special updates:

$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  ssl-cert
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded

But when using aptitude (Mark Upgradeable) or using apt-get dselect-upgrade -s or using "Update Manager" Gui this upgrades are shown and upgrade would be proceeded.

Why not with apt-get upgrade ? And if it is kept back for some reasons than "Why not in all apt-applications?"

---

### Post by gabril on 2008-12-04
Did you update your repository before atempting this? 

try just:

$ sudo aptitude update && aptitude upgrade

should do the trick

also check your apt list... it might not have reverted to hardy... that can easly be fixed manually!

---

### Post by tekknokrat on 2008-12-04
Hi gabriel,

Like I wrote in my previous thread I am aware of that aptitude shows the upgrade in right way and would perform them correctly. I am just courious why this does not work with apt-get the same. 

So, do we have a inconsistency in upgrade behaviour in matter of client you are using? I am willing to accept that for dselect (which is deprecated) but not for the native apt tools.

---

### Post by gabril on 2008-12-04
Oh now i see, i think.

You do NOT have a problem with your apt! I think these are the file s for a distupgrade that is recommended... i use debian so this does not happen to me very much... lets say like this! Again this is only a theory! 

Imagine you downgrading your opsys, ubuntu backs up your old version (newer) and has the files available to upgrade again, aptitude feels that you are running an older version and states that an upgrade is possible but does not do this automaticly!

Does this clarify anything?

---

### Post by tekknokrat on 2008-12-04
OK, sorry to mention that I did a downgrade from intrepid as this seems to obfuscate the problem.

I did the downgrade with reinstalling ubuntu **completly** because downgrading directly from within intrepid is not recommended ( too many new! config files will resist ).

So the issue only happens for me with pure upgrades from hardy.
These are shown in aptitude but are kept back in apt-get.
When you look in /etc/apt/apt.conf.d/05aptitude you see some patterns match linux-image... I don't know the meaning of them, perhaps they influence aptitude's behaviour. But why did apt-get refuse to upgrade e.g. *bind-host* :confused:

---

### Post by gabril on 2008-12-04
That's a bery good question! As of now i do not know the answer to that question!

Ill be sure to look into it!

As for me i just use it as an general rule always to use aptitude!

---

