---
title: "automatix2 hangs"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by alfsborg on 2007-12-10
I just upgraded to Gutsy on my computer. When I install Automatix, i get the following error:
The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: tango-icon-theme but it is not installable
E: Broken packages
I have tried synaptic broken packages but that did not help. I tried:
 sudo dpkg --configure -a    and that did not work either?

Before I go back to Feisty, does anyone know of a fix?  ](*,)
Is this a bug?  :confused:
i have an Asus PN-SLI  SE Deluxe moterboard, Intel Conroe 7600 Chip, 4gb ram

Thank you

---

### Post by PmDematagoda on 2007-12-10
Please do not use Automatix, it can usually break your PC instead of making it. If you want to install something then just use the repositories, download the Deb from the proper web site or compile it from the source.

Or if you still want to use Automatix, then ask your question on their [Forums.]("http://www.getautomatix.com/forum/")

If you could tell us what application you are trying to install using Automatix then we could help you install it without Automatix.

---

### Post by taurus on 2007-12-10
On top of that, I bet you don't have any repos or limited number of repos in your /etc/apt/sources.list!

```
cat /etc/apt/sources.list
```

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

