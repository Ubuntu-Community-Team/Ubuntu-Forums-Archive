---
title: "gcin not loading after KDE4 -&gt; KDE3 downgrade..."
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by taiwanjohn on 2008-08-26
I recently switched from Ubuntu 8.04 to Kubuntu 8.04, and got gcin working for Chinese input. However, after a few days I decided that KDE4 was not what I wanted, so I removed it and installed KDE3 (with "apt-get install kubuntu-desktop"). So far, everything seems to be working fine, except gcin... Now, gcin doesn't load on X startup. And if I run it manually, it doesn't load its input tables. 

The gcin icon is there in the system tray (showing "EN") but ctrl-space does not switch it to Chinese input. If I middle-click on the icon, it shows a whole list of IM's, but choosing them has no effect... the icon stays as "EN". 

Right-clicking on the icon, I can go into the config screen, and it shows my preferred IM's all selected, just as I've always had them set before (implying that the config files haven't changed through all this). 

My startup file is still there in /etc/X11/Xsession.d/73custom-gcin_startup just where it's always been: 

```
export XMODIFIERS="@im=gcin"
export GTK_IM_MODULE="gcin"
export XIM_PROGRAM="gcin"
export QT_IM_MODULE="gcin"

```

I have uninstalled/reinstalled the gcin package, but that didn't help... 

Can anyone point me towards a list of what files and settings are required to get gcin working? I've already checked everything I know to check, and it's still not working. 

Thanks! 

--jrd

---

### Post by taiwanjohn on 2008-08-26
I just installed "gcin-qt3-immodule" and now it works. ;-) 

I don't know why it worked without this package in KDE4, but not KDE3... but I'm just happy it's working. 

Anyway, I'll leave this thread on the board, in case someone else has a similar problem. 

Cheers, 

--jrd

---

