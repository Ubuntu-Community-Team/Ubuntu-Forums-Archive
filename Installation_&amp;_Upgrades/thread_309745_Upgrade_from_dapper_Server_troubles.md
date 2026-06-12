---
title: "Upgrade from dapper Server troubles"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by GoBieN on 2006-11-30
Hello all,

I'm havong some issues afterI tried apt-get dist-upgrade on my server when I replaced all dapper entries in the sources for edgy entries.

I cannot install or remove anything because of broken package courrier-authdaemon
> apt-get -f install
These packages will be updated:
  courier-authdaemon
1 package updaten, 1 new package installing, 0 deleting en 131 not up to date.
1 package not completely installed or deleted.
...
Reading changelogs... Done
dpkg: error while handling courier-authdaemon (--remove):
 Package is in a serious inconsistent state try to reinstall it prior to removing it.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors found while handling:
 courier-authdaemon
Aborted (core dumped)
root@ARES:/home/stan#

ps: I translated, because my system is in dutch.

What can I do to solve this issue ? I want to remove all those courier packages as I don't need them. But I can't, i have to reinstall it first it says, but i can't reinstall it due to dependecy problems.

Please help ;)

---

### Post by bapoumba on 2006-11-30
Hi,
try **sudo dpkg --force-remove courier-authdaemon**
If this is not working, there are more heavy duty options for dpkg, read **man dpkg**.

---

### Post by GoBieN on 2006-11-30
> **bapoumba said:**
> Hi,
try **sudo dpkg --force-remove courier-authdaemon**
If this is not working, there are more heavy duty options for dpkg, read **man dpkg**.
Hello maybe ther eis something wrong with your syntax, because I get the help output.

I'v tried the following:µ
sudo apt-get -f install courier-authlib
sudo apt-get -f install courier-authdaemon
dpkg --remove --force-all courier-authdaemon
dpkg --install --force-all courier-authdaemon

All without succes :(

Please help me

---

