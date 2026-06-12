---
title: "package &amp; dependency problems - can't fix!!"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by wiseguy12851 on 2011-01-02
I'm having a big problem with dependencies all of a sudden, I've never encountered this situation before - It seems packages with dependency problems somehow got installed and synaptic didn't detect them, but that's really the best guess I can come up with.

The problem I'm facing is there are no corrupt or broken packages, everything works great with the exception that anytime I perform any task on new or existing software it completes the task and then starts to complain about recovering from errors on an installation I asked it to do a long time ago.

The weird thing is, if I ask it to do something like install fonts for example, they end up getting installed (or at least most of it installed) but it still complains about errors and recovering from them.

Here is the error message that came up in a dialog at the very end:
```
E: xemacs21-nomule: subprocess installed post-installation script returned error exit status 1
E: aplus-fsf-el: dependency problems - leaving unconfigured
E: xemacs21-mule-canna-wnn: subprocess installed post-installation script returned error exit status 1
E: xemacs21-mule: subprocess installed post-installation script returned error exit status 1
E: haml-elisp: subprocess installed post-installation script returned error exit status 1
E: xemacs21: dependency problems - leaving unconfigured

W: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
W: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
```it seems that whenever I try to just completely purge all of the xemacs21 stuff above it might purge some installations but one of these has to be installed all the time, as when I purge one thing the other has to be installed.

additionally the error message does differ depending on which packages I did manage to remove or purge.

---

### Post by Nuihc88 on 2011-04-18
I have the same problem with the same packages.

---

### Post by Nuihc88 on 2011-04-20
I was able to solve this problem with the following terminal command:
```
sudo apt-get purge xemacs21 xemacs21-nomule xemacs21-mule xemacs21-mule-canna-wnn xemacs21-bin xemacs21-supportel xemacs21-gnome-mule xemacs21-gnome-nomule xemacs21-gnome-mule-canna-wnn xemacs21-support xemacs21-basesupport xemacs21-mulesupport xemacs21-basesupport-el xemacs21-mulesupport-el
```
It only works when it's all one line, otherwise it just goes in a loop.

---

### Post by dkozhukhar on 2011-04-25
> **Nuihc88 said:**
> I was able to solve this problem with the following terminal command:
```
sudo apt-get purge xemacs21 xemacs21-nomule xemacs21-mule xemacs21-mule-canna-wnn xemacs21-bin xemacs21-supportel xemacs21-gnome-mule xemacs21-gnome-nomule xemacs21-gnome-mule-canna-wnn xemacs21-support xemacs21-basesupport xemacs21-mulesupport xemacs21-basesupport-el xemacs21-mulesupport-el
```It only works when it's all one line, otherwise it just goes in a loop.
Thanks for your idea.

I make the same with modification: put 'xemacs21' to the end of line, that purges it.

---

