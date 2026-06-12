---
title: "HELP.... &quot;Impossible to calculate changes&quot;"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Uriel.Fanelli on 2011-04-28
Hello, I tried to update to Ubuntu 11.04 from 10.10, and I got a strange error like 

"Unable to calculate changes, package ubuntu-desktop is needed but not going to be installed". Then the sistem claimed to return back to the previous state, but now ALL the package are marked as "upgradable", and the Software Updater is suggesting me to do a "partial upgrade".

What happened? How I can get back with a coherent system?
 I don't installed the xubuntu-desktop, BTW.

thanks in advance.

---

### Post by zvacet on 2011-04-28
> I don't installed the xubuntu-desktop, BTW.

You have to install ubuntu-desktop matapackage.Without it you will not be able to upgrade,so go to the synaptic and install it.After that do the upgrade.

---

### Post by Uriel.Fanelli on 2011-04-28
> **zvacet said:**
> You have to install ubuntu-desktop matapackage.Without it you will not be able to upgrade,so go to the synaptic and install it.After that do the upgrade.

I actually have It installed. I don't have installed the xubuntu-desktop, but I have the ubuntu-desktop.
Please notice the "x" :)(I specified this because I had a google-look around and I see there is a problem when both are installed).

Perhaps I can't remove it, since it will remove too many dependencies I need. And now I can't really do changes with sinaptic due all packages are the ones for 11.04 , marked as upgradable, with missing dependencies that prevents any change.

---

### Post by zvacet on 2011-04-30
Do you have both (ubuntu and xubuntu) installed?If you do you installed two desktop environments and ubuntu-desktop and xubuntu-desktop are metapckages witch can be removed without removing dependencies.If you are not sure that this is truth mark xubuntu-desktop for removal and you should see witch dependencies will be removed with it.None I suppose.

> Please notice the "x"

Yes I did but look what message say

> "Unable to calculate changes, package **ubuntu-desktop** is needed but not going to be installed".

So go to the synaptic and in search box type ubuntu-desktop and if iti s not installed install it,because without it you can not do upgrade.

---

### Post by Uriel.Fanelli on 2011-04-30
> **zvacet said:**
> Do you have both (ubuntu and xubuntu) installed?If you do you installed two desktop environments and ubuntu-desktop and xubuntu-desktop are metapckages witch can be removed without removing dependencies.If you are not sure that this is truth mark xubuntu-desktop for removal and you should see witch dependencies will be removed with it.None I suppose.



Yes I did but look what message say



So go to the synaptic and in search box type ubuntu-desktop and if iti s not installed install it,because without it you can not do upgrade.

IT-IS-ACTUALLY-INSTALLED.

ubuntu-desktop -> INSTALLED (YES)
xubuntu-desktop -> NOT INSTALLED (NO)

---

### Post by zvacet on 2011-05-01
Let make this simple.Why do you even talk about xubuntu-desktop if you don´t have it installed and you don´t use Xubuntu?Message warning you that you have to install ubuntu-desktop matapckage to be able to upgrade your system.Go to the synaptic and mark ubuntu desktop package for reinstall and see if that will work.

---

### Post by Uriel.Fanelli on 2011-05-02
> **zvacet said:**
> Let make this simple.Why do you even talk about xubuntu-desktop if you don´t have it installed and you don´t use Xubuntu?


Because BEFORE of asking help I went thru the bug list, and there is a bug related with having both installed.

Perhaps I solved the problem. Actually, the problem is that BAnshee is poited both as a dependency of ubuntu-desktop and ubuntu-desktop is marked as a dependency in banshee in the current 10.10. 

Just removed banshee, and it worked.

---

