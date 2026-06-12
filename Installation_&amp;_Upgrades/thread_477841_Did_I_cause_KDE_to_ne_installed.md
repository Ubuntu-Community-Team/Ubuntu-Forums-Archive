---
title: "Did I cause KDE to ne installed?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-18
I installed K3b, a KDE CD recorder, the other day.

When I ran updates, lots of KDE related stuff seemed to get updated.

Where possible, I want to use only GNOME.

I ASSuME that I can uninstall K3b and install GnomeBaker.
But, how do I then get rid of, if any, extra KDE stuff that was installed.

I suppose that this means I need to install Bluefush, an HTML editor, instead of Nvu.

What should I do?

---

### Post by dreadlord_chris on 2007-06-18
> **Howard Kaikow said:**
> I installed K3b, a KDE CD recorder, the other day.

When I ran updates, lots of KDE related stuff seemed to get updated.

Where possible, I want to use only GNOME.

I ASSuME that I can uninstall K3b and install GnomeBaker.
But, how do I then get rid of, if any, extra KDE stuff that was installed.

I suppose that this means I need to install Bluefush, an HTML editor, instead of Nvu.

What should I do?

You didn't install all of KDE, just the minimum libs necessary to run KDE apps.

You can install the package **deborphan** - this will give you a new **Custom Filter** in Synaptic that will list all the packages that are installed on your system that are no longer being used.

---

### Post by Howard Kaikow on 2007-06-18
Thanx, i'll give it a shot on the 'morrow.

---

### Post by HotShotDJ on 2007-06-18
I've always found this works great: ```
sudo apt-get autoremove k3b
```
Of course, you can replace "k3b" with whatever package you need to uninstall along with the dependencies it pulled in.

---

### Post by Howard Kaikow on 2007-06-18
> **HotShotDJ said:**
> I've always found this works great: ```
sudo apt-get autoremove k3b
```
Of course, you can replace "k3b" with whatever package you need to uninstall along with the dependencies it pulled in.

Thanx.

Since I intend to only remove one app, this may be safer, and is decribed in at least one book I have.
But first, I will backup te linux partition.

---

### Post by merlinus on 2007-06-18
Why not use Synaptic, and choose Mark for Complete Removal?

-merlin

---

### Post by Tynach on 2007-06-18
Why would having KDE installed prevent you from using non-KDE apps? I say go ahead and keep the libs, because some usefull applications, like Acetone ISO, are only available as QT (KDE) apps, instead of GTK (Gnome) apps.

---

### Post by Howard Kaikow on 2007-06-19
I thought that I read that Synaptic would not remove configuration files.

using --purge with apt-get supposedly removes those files.

---

### Post by Howard Kaikow on 2007-06-19
> **Tynach said:**
> Why would having KDE installed prevent you from using non-KDE apps? I say go ahead and keep the libs, because some usefull applications, like Acetone ISO, are only available as QT (KDE) apps, instead of GTK (Gnome) apps.

Because I am new to linux and I want to see how far I can get with just GNOME apps.

Is Acetone ISO a  CD writer?
If so, why is it better than Gnomebaker?

---

### Post by Howard Kaikow on 2007-06-19
I ended up doing the following.

sudo apt-get --purge autoremove k3b

And then to confirm that k3b was no longer installed.

sudo apt-get --purge remove k3b

Which confirmed that k3b was no longer installed.

However, it may be useful to use deborphan peridically to see how much crap has accumulated.

---

