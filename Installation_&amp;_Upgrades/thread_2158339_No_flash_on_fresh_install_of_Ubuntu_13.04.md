---
title: "No flash on fresh install of Ubuntu 13.04"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by Arunomi on 2013-06-28
Hi 

I have installed Ubuntu 13.04 and Im tryinge to get Flash to work.

In firefox I only get a white or black box and then no more.
In Chromium I get a Can't loade flash.

I have tried to purge flashplugin-installer
and reinstal it but same result.

I have tried to install Adobe-flashplugin and that do not work better.

When I run Chromium from terminal I get this
[22:22:0628/210147:ERROR:webplugin_delegate_proxy.cc(380)] PluginMsg_Init returned false
[22:22:0628/210147:ERROR:webplugin_impl.cc(253)] Couldn't initialize plug-in

When I run Firefox from terminalen I get this
(process:4740): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed


Pleas is there som one that can help me.

---

### Post by kc1di on 2013-06-28
Hello Arunomi,

have in install ubuntu-restricted-addons and ubuntu-restricted-extras if not try that.

you can do it in a terminal with the following command.

```
sudo apt-get install ubuntu-restricted-extra ubuntu-restricted-addons
```

---

### Post by grahammechanical on 2013-06-28
This may work for chromium

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

I have also been able to use the Software Centre to install adobe flash plugin for mozilla and that works also for Chromium and I have this working in 13.04. How are you doing the installing?

Regards.

---

