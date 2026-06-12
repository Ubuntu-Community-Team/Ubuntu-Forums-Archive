---
title: "skim in 10.10"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by efranor on 2011-01-10
I installed the whole scim/skim package with it's repositories and dependencies as i did always and i got this when i started it:
efranor@Sindabra:~$ skim &
[1] 2097
efranor@Sindabra:~$ kbuildsycoca running...
KCrash: Application 'skim' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

[1]+  Exit 253                skim

Would appreciate some help with it as i have to reinstall everything else i had on my sys because of a few problems with my hdd.

---

### Post by Zorael on 2011-01-11
SCIM and Skim are old. To my knowledge SCIM is no longer being actively developed, and to begin with Skim is for KDE3. I'm not sure if I would recommend you to try and debug this error, or if your time is better spent migrating to another input method engine, such as IBus or UIM. IBus is the new standard in both Ubuntu (as of ~10.04) and Kubuntu (as of 10.10). I prefer UIM myself.

For IBus you need the packages **ibus**, **ibus-gtk** and **ibus-qt4** - as well as some package for the language you wish to use this input method engine for. **ibus-anthy** for Japanese, **ibus-pinyin** for Chinese Pinyin, **ibus-hangul** for Korean, **ibus-m17n** for the plethora of languages available via the m17n libraries, etc. You probably know which one to go for if you have experience with SCIM.

IBus sadly lacks a good Qt4 frontend. There is a plasma widget (**plasma-widget-kimpanel-ibus**), but last I tried it it didn't work very well. You can still use the GTK toolbar and/or tray icon, but they may look ugly as sin unless you go through some extra hoops with startup scripts. They get started just as you log in, which is sadly before the QtCurve/gtk-oxygen theming has been applied.

For UIM you need **uim** and **uim-qt**. If you're still using any Qt3 programs, grab **uim-qt3**. Like in IBus, the language-specific packages are pretty easy to identify by their names; **uim-anthy**, **uim-pinyin**, **uim-hangul**, **uim-m17nlib**, etc.

UIM has a Qt4 panel, although it still tries to use KDE3 Crystal icons. It has some extra features over IBus, like input prediction.

The **uim-qt** package installs its Qt4 toolbar, but the **uim-toolbar-qt** option that you choose in im-switch (the preferred way to tell X to use UIM) starts the Qt3 toolbar. You can fix that with an easy oneliner;
```
$ sudo sed -ie 's/toolbar-qt)/toolbar-qt4)/g' /etc/X11/xinit/xinput.d/uim-toolbar-qt
```
I haven't gotten around to filing a bug report for that one yet.

---

### Post by efranor on 2011-01-12
Ah thank you. UIM was not so my thing but Ibus works great. I don't care for the fronting or graphics in qt4 just that i can access my files and folders trough the terminal...
But to be frank it was abhorrent to change from SKIM/SCIM because i used it from the beginning.
So once more thank you. Was kinda sad to read that more and more people changed to Ibus or UIM...

---

