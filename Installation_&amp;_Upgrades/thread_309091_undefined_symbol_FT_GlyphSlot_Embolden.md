---
title: "undefined symbol: FT_GlyphSlot_Embolden"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by nefch on 2006-11-29
I try to run update-manager and get this error message:

[FONT="Courier New"]root@nef-ubuntu6:/home/nef# update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in ?
    import gtk
  File "/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden[/FONT]

What's this supposed to mean??? I think the latest thing I tried to install was Eclipse.
I'm using Ubuntu 6.10.

Regards
Christof

---

### Post by nefch on 2006-11-30
I have installed libcairo.so.2.9.2 (1.2.4-1ubuntu2) and libfreetype.so.6.3.10 (2.2.1-5). I did install **everything** with Synaptic Package Manager - so how can it possibly happen that there are undefined symbols???

Please help! Ubuntu 6.10 is totally useless the way it is now! ](*,)

Christof

---

### Post by DonLorenzo on 2007-09-23
I have a similar problem running XAMPP on Feisty (7.04).

This post on the Debian bug report system seems to describe the root cause of the problem. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=353706](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=353706)

Accroding to the debian report, package python2.3-gnome2 and
python-gnome2 might be downlevel in both 6.10 and 7.04.

---

### Post by sacrosancttayyar on 2008-06-12
i have the same problem with XAMPP panel

updated the packages but still have the same error.
so i am suing that code.

```
cd /opt/lampp/share/xampp-control-panel
sudo ./xampp-control-panel 
```

--
Hasan Tayyar BE&#350;&#304;K

---

