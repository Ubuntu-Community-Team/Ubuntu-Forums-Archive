---
title: "Uninstall Wine"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by emma00 on 2010-01-23
Hi,
I want to know that how i remove wine,whenever i try to through Applications>Wine>Unistall wine software a window will appears which i don't understand.:confused:

and also how to reinstall it again.
Thanks.

---

### Post by d3v1150m471c on 2010-01-23
you have to uninstall it with synaptic package manager...or 

```

sudo aptitude remove wine

```

If you want to remove the crap that came with it


```

sudo aptitude remove wine && sudo apt-get autoclean && sudo apt-get autoremove

```

---

### Post by emma00 on 2010-01-23
thanks for your reply but should i do this with synaptic or through terminal.I have installed it through synaptic and it doest not work.

---

### Post by d3v1150m471c on 2010-01-23
Are you trying to install wine or remove it? Secondly, what do you mean by it not working?

---

### Post by emma00 on 2010-01-23
i have removed it through terminal.Thanks for your help but by which command i reinstall it through terminal.:o

---

### Post by c0mput3r_n3rD on 2010-01-23
sudo apt-get install wine     to reinstall.  Or you can use aptitude like others suggested to uninstall.

---

### Post by emma00 on 2010-01-28
I installed wine and installed Proteus through wine does not appear in uninstall wine software and it also does not work because you have to execute some license file which i did not figure out how to work it out.

Any Ideas???

Do i have to again remove wine and reinstall it?

---

### Post by ershibbu on 2010-01-28
> **emma00 said:**
> I installed wine and installed Proteus through wine does not appear in uninstall wine software and it also does not work because you have to execute some license file which i did not figure out how to work it out.

Any Ideas???

Do i have to again remove wine and reinstall it?
if u r using ubuntu9.10
than download wine1.1.37.deb
than read this:```
http://www.winehq.org/download/deb
```

---

### Post by emma00 on 2010-01-29
> **ershibbu said:**
> if u r using ubuntu9.10
than download wine1.1.37.deb
than read this:```
http://www.winehq.org/download/deb
```

From where to download wine1.1.37.deb???

its not listed in synaptic packet manager

---

### Post by s.fox on 2010-01-29
> **emma00 said:**
> From where to download wine1.1.37.deb???

its not listed in synaptic packet manager


Hello,

I found it on the deb [packages archive]("http://wine.budgetdedicated.com/archive/index.html") on the official site.  Please choose the correct one for your Ubuntu version.

Hope this helps.

-Silver Fox

---

### Post by emma00 on 2010-01-31
why after millions of time removing wine through terminal its still appears in applications and the programs also????

---

### Post by eldinv on 2010-04-13
im having same trouble mine was deleted 3 different methods and it still shows up under application

---

### Post by bumanie on 2010-04-13
This is from [here]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391"). It works, I have used the commands before.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

Please note that in the following commands there should be no spaces in the path, particularly between $HOME/ and .whatever.

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

---

### Post by emma00 on 2010-05-13
> **bumanie said:**
> This is from [here]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391"). It works, I have used the commands before.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

Please note that in the following commands there should be no spaces in the path, particularly between $HOME/ and .whatever.

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm


Thanks now i needed it......:)

---

### Post by amirmku on 2010-06-29
> > **bumanie said:**
> This is from [here]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391"). It works, I have used the commands before.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

Please note that in the following commands there should be no spaces in the path, particularly between $HOME/ and .whatever.

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm


Hey I tried the commands given above but still unable to get rid of  wine. wine still exist in application.
I m using ubuntu 10.04

---

