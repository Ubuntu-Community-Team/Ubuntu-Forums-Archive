---
title: "hardy upgrade causes wine problems"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ilutis on 2008-04-29
hi, today i recently upgraded from gutsy gibbon to hardy heron.  things look great except i'm having one -extremely- big problem.

i run an application using wine and it worked flawlessly in gutsy gibbon.  however, upgrading to hardy heron causes this program to not open new windows when it should, and it messes up the way the application's window looks when i go from desktop to desktop.

i tried uninstalling and reinstalling wine.  i even upgraded to wine-0.9.60.  i'm very frustrated and i can't seem to figure out how to fix the problem.  any help is greatly appreciated.

---

### Post by Lord Landis on 2008-04-29
Did you have any custom configs set up for Wine with your old install?  Honestly, the best advice I can think of is to uninstall Wine completely and then re-install from the new version, rather than just trying to upgrade the package you've already got installed.

---

### Post by glendavee on 2008-04-29
I had a similar problem running Microsoft Money.
This fixed it 
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
Best of luck

---

### Post by ilutis on 2008-04-29
1. sorry if i was not clear before - i have uninstalled wine and i reinstalled it fresh with the repositories.  i also did not have any custom configs before either.

2. the "sudo sysctl -w vm.mmap_min_addr=0" seemed to sort of fix my problem.  it now opens windows when it should, however, when i swap from desktop to desktop, it causes problems with the application's window resolution - it basically extends the window to the bottom of my screen and i can't see it anymore.  it also causes problems using alt-tab, namely it won't swap back to the application being run by wine.

thanks for your help.

---

