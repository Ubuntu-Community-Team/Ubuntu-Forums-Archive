---
title: "Upgrade from 16.04 to 16.10 and 16.04 did not uninstall"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by kd6mdv on 2016-11-03
I upgraded via Software Updater from 16.04 to 16.10 and 16.04 is still a boot option and is still on my HD causing me to get a disk full error. How do I uninstall 16.04 I thought it was automatically uninstalled when upgrading to 16.10. Thanks Tim

---

### Post by ka55o5 on 2016-11-03
You *may* have to look at some different ways to edit the Grub2 loader, depending on what had happened - for example, whether the upgrade actually happened and only the entries are mixed up, or if everything got (somehow) b0rked! xD

**Grub Customizer**,```
https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer
```
**GRUB2 Editor**,```
https://ksmanis.wordpress.com/projects/grub2-editor/
```[color=gray](This is a **KDE** "Control Module", so it's only for KDE-enabled distros; which are -almost- bloatware, depending on your point of view. :))[/color]

P.S. A couple of GRUB2 links @
[list][*]https://www.google.com/search?q=askubuntu.com+grub2
[*]http://www.howtogeek.com/196520/grub2-101-how-to-access-and-use-your-linux-distributions-boot-loader/
[*]http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/
[*]https://help.ubuntu.com/community/Grub2/
[*]https://help.ubuntu.com/community/Grub2/Setup[/list]

---

### Post by ka55o5 on 2016-11-03
Ugh, I'm *really not sure* how to edit /complete my answer /post above; how can we test to see what is, actually, installed - whether the CMDs will return the right answer... That is, IF you can even boot the system:
```
lsb_release -a
``````
uname -r -v
```

[list][*]http://manpages.ubuntu.com/manpages/xenial/en/man1/lsb_release.1.html
[*]http://manpages.ubuntu.com/manpages/wily/man2/uname.2.html
[*]http://manpages.ubuntu.com/manpages/wily/man1/uname.1.html[/list]
Oh and **by the way**, nothing is "uninstalled" when you update /upgrade to a new version - simply, files are replaced!.. Some things which could /can be removed are the PPA added-on settings, files...

[list][*]https://www.google.com/search?q=ubuntu+sources.list.d
[*]https://www.google.com/search?q=ubuntu+sources.list[/list]
**Edit**:
[https://superuser.com/questions/21634/how-do-you-find-the-ubuntu-version-release-number-name-from-the-command-line]("https://superuser.com/questions/21634/how-do-you-find-the-ubuntu-version-release-number-name-from-the-command-line")

[color=gray]Hope it helps! =)[/color]

---

