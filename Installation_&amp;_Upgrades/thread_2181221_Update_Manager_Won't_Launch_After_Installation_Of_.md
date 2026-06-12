---
title: "Update Manager Won't Launch After Installation Of Unmet Dependencies"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by jeffroaltiere1 on 2013-10-16
Hi. Recently, I seem to have installed something with untrusted  dependencies, and now I can't run an update, install or uninstall  programs or updates. Everytime I try to, Update Manager tells me it's  been closed unexpectedly. I have this little bubble at the top bar that  tells me:
[PHP]The error was: Error: Opening the cache (E: Encountered a section  with no Package; header, E:Problem with MergeList  /var/lib/apt/listsus.archive.ubuntu.com_ubuntu_dists_raring_backports_main_i18n_Translation-en%5US,  E:The package lists or status file could not be parsed or opened.
)'.[/PHP]

---

### Post by ibjsb4 on 2013-10-17
Enter these terminal command lines one at a time:

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit
```

Found that here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9)

and terminal

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by jeffroaltiere1 on 2013-10-18
It's fixed now. Thanks!

---

