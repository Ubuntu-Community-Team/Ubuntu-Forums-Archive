---
title: "deeper level remove for software  is it possible?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2010-01-13
[COLOR=Blue][B]:o:o      hi guys

trying to remove and reinstall xmms2    since i seem to have upset it somehow   it crashes when changing tracks


now whether i use the synaptic (complete removal)

or the terminal with 


[/B][/COLOR]```
shantiq@shantiq-desktop:~$ sudo apt-get remove xmms2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  stk libstk0c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  xmms2
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
After this operation, **[COLOR=Red]123kB!!! [/COLOR]**disk space will be freed.
Do you want to continue [Y/n]? 

```[B][COLOR=Blue]


as you can see [  [/COLOR][/B]**[COLOR=Red]123kB!!! ] [/COLOR]**[B][COLOR=Blue]it removes almost nothing       which means when i do a complete removal and a reinstall i find even my playlist has remained the way it was before the whole operation



so is there a way to TRULY REMOVE AND REINSTALL so all settings are put back to new and the playlist does not show up



this also happened with audacious a while back


any ideas/??:KS
[/COLOR][/B]

---

### Post by fancypiper on 2010-01-13
Try this:

sudo apt-get purge xmms2

---

### Post by shantiq on 2010-01-13
[COLOR=Blue][B];);)  hi there thanx for the suggestion but same result as remove

[/B][/COLOR]```
shantiq@shantiq-desktop:~$ sudo apt-get purge xmms2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  xmms2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 232300 files and directories currently installed.)
Removing xmms2 ...
shantiq@shantiq-desktop:~$ 
```


**[COLOR=Green]still the paltry 123kb will be removed[/COLOR]**

---

### Post by shantiq on 2010-04-26
[B][COLOR="Blue"]the answer was i had forgotten to run

```
sudo apt-get update
```


this removes the whole lot[/COLOR][/B]

---

