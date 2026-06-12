---
title: "Upgrade crash during upgrade 12.10 to 13.04"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by reyman on 2013-03-27
Hi,

I have big problem with the last update of my ubuntu.
I make a classic ```
gksu 'update-manager -d'
```  to upgrade my 12.10 version,
but during installation, i have a critical error on ld.so installation :-/

Update manager try to recover multiple time with dpkg configure -a, but finally it crash, and i have no choice, i need to reboot.
I ran into console and finish the install with```
 dpkg configure -a
```, without problem **BUT**

- **[Ok]** session screen work
- **[Ok]** xfce work
- **[Not OK]** unity don't work and display only black screen with mouse cursor
- **[Not Ok]** On xfce and unity i don't have any access to tty with Ctrl + Alt + number ...
- **[Not Ok]** I cannot change my sources.list in graphic mode, click on checkbox don't work ! 

> I try to find the log of corrupted install to retry installation of package which fail .. without success, can you help me to find that ? or to reinstall unity entirely ?
> Another question, how can i finish properly the upgrade ? 

THanks !

---

