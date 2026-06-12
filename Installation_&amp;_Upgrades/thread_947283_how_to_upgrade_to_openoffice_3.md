---
title: "how to upgrade to openoffice 3"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by esmailgad on 2008-10-14
Hi everyone
I downloaded openoffice 3 for linux asxxx.tar.bz2 archivefile. I decompressed it and now I do not know how can I upgrade my openoffice 2.4 to this new version
thank you for your help

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by Partyboi2 on 2008-10-14
You could try following [[COLOR=Blue]this [/COLOR]]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")howto

---

### Post by chozoboy on 2008-10-14
If I wait and upgrade to 8.10 when it comes out, will my OpenOffice upgrade also?

---

### Post by Sonic Reducer on 2008-10-14
the basic idea is to cd into the DEBS directory and run **sudo dpkg -i *.deb**

like this:
```
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ ls
[COLOR="Blue"]desktop-integration[/COLOR]                             [COLOR="Red"]ooobasis3.0-images_3.0.0-9_i386.deb
ooobasis3.0-base_3.0.0-9_i386.deb               ooobasis3.0-impress_3.0.0-9_i386.deb
ooobasis3.0-binfilter_3.0.0-9_i386.deb          ooobasis3.0-javafilter_3.0.0-9_i386.deb
ooobasis3.0-calc_3.0.0-9_i386.deb               ooobasis3.0-kde-integration_3.0.0-9_i386.deb
ooobasis3.0-core01_3.0.0-9_i386.deb             ooobasis3.0-math_3.0.0-9_i386.deb
ooobasis3.0-core02_3.0.0-9_i386.deb             ooobasis3.0-onlineupdate_3.0.0-9_i386.deb
ooobasis3.0-core03_3.0.0-9_i386.deb             ooobasis3.0-ooofonts_3.0.0-9_i386.deb
ooobasis3.0-core04_3.0.0-9_i386.deb             ooobasis3.0-ooolinguistic_3.0.0-9_i386.deb
ooobasis3.0-core05_3.0.0-9_i386.deb             ooobasis3.0-pyuno_3.0.0-9_i386.deb
ooobasis3.0-core06_3.0.0-9_i386.deb             ooobasis3.0-testtool_3.0.0-9_i386.deb
ooobasis3.0-core07_3.0.0-9_i386.deb             ooobasis3.0-writer_3.0.0-9_i386.deb
ooobasis3.0-draw_3.0.0-9_i386.deb               ooobasis3.0-xsltfilter_3.0.0-9_i386.deb
ooobasis3.0-en-us_3.0.0-9_i386.deb              openoffice.org3_3.0.0-9_i386.deb
ooobasis3.0-en-us-base_3.0.0-9_i386.deb         openoffice.org3-base_3.0.0-9_i386.deb
ooobasis3.0-en-us-binfilter_3.0.0-9_i386.deb    openoffice.org3-calc_3.0.0-9_i386.deb
ooobasis3.0-en-us-calc_3.0.0-9_i386.deb         openoffice.org3-dict-en_3.0.0-9_i386.deb
ooobasis3.0-en-us-draw_3.0.0-9_i386.deb         openoffice.org3-dict-es_3.0.0-9_i386.deb
ooobasis3.0-en-us-help_3.0.0-9_i386.deb         openoffice.org3-dict-fr_3.0.0-9_i386.deb
ooobasis3.0-en-us-impress_3.0.0-9_i386.deb      openoffice.org3-draw_3.0.0-9_i386.deb
ooobasis3.0-en-us-math_3.0.0-9_i386.deb         openoffice.org3-en-us_3.0.0-9_i386.deb
ooobasis3.0-en-us-res_3.0.0-9_i386.deb          openoffice.org3-impress_3.0.0-9_i386.deb
ooobasis3.0-en-us-writer_3.0.0-9_i386.deb       openoffice.org3-math_3.0.0-9_i386.deb
ooobasis3.0-gnome-integration_3.0.0-9_i386.deb  openoffice.org3-writer_3.0.0-9_i386.deb
ooobasis3.0-graphicfilter_3.0.0-9_i386.deb      openoffice.org-ure_1.4.0-9_i386.deb[/COLOR]
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ sudo dpkg -i *.deb
```

then cd into the desktop-integration and do the same thing (even though it's only one deb it's quicker to just hit the up arrow two or three times to bring up the **sudo dpkg -i *.deb** again)

like this:
```
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ cd desktop-integration
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS/desktop-integration$ ls
[COLOR="Red"]openoffice.org3.0-debian-menus_3.0-9354_all.deb[/COLOR]
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS/desktop-integration$ sudo dpkg -i *.deb
```

yeah, i did kind of copy the tutorial from the link, but you never know what might happen to the other site. thank you for the guidance **Hagar de l'Est**

---

### Post by vittalp88 on 2008-10-19
> **Sonic Reducer said:**
> the basic idea is to cd into the DEBS directory and run **sudo dpkg -i *.deb**

like this:
```
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ ls
[COLOR="Blue"]desktop-integration[/COLOR]                             [COLOR="Red"]ooobasis3.0-images_3.0.0-9_i386.deb
ooobasis3.0-base_3.0.0-9_i386.deb               ooobasis3.0-impress_3.0.0-9_i386.deb
ooobasis3.0-binfilter_3.0.0-9_i386.deb          ooobasis3.0-javafilter_3.0.0-9_i386.deb
ooobasis3.0-calc_3.0.0-9_i386.deb               ooobasis3.0-kde-integration_3.0.0-9_i386.deb
ooobasis3.0-core01_3.0.0-9_i386.deb             ooobasis3.0-math_3.0.0-9_i386.deb
ooobasis3.0-core02_3.0.0-9_i386.deb             ooobasis3.0-onlineupdate_3.0.0-9_i386.deb
ooobasis3.0-core03_3.0.0-9_i386.deb             ooobasis3.0-ooofonts_3.0.0-9_i386.deb
ooobasis3.0-core04_3.0.0-9_i386.deb             ooobasis3.0-ooolinguistic_3.0.0-9_i386.deb
ooobasis3.0-core05_3.0.0-9_i386.deb             ooobasis3.0-pyuno_3.0.0-9_i386.deb
ooobasis3.0-core06_3.0.0-9_i386.deb             ooobasis3.0-testtool_3.0.0-9_i386.deb
ooobasis3.0-core07_3.0.0-9_i386.deb             ooobasis3.0-writer_3.0.0-9_i386.deb
ooobasis3.0-draw_3.0.0-9_i386.deb               ooobasis3.0-xsltfilter_3.0.0-9_i386.deb
ooobasis3.0-en-us_3.0.0-9_i386.deb              openoffice.org3_3.0.0-9_i386.deb
ooobasis3.0-en-us-base_3.0.0-9_i386.deb         openoffice.org3-base_3.0.0-9_i386.deb
ooobasis3.0-en-us-binfilter_3.0.0-9_i386.deb    openoffice.org3-calc_3.0.0-9_i386.deb
ooobasis3.0-en-us-calc_3.0.0-9_i386.deb         openoffice.org3-dict-en_3.0.0-9_i386.deb
ooobasis3.0-en-us-draw_3.0.0-9_i386.deb         openoffice.org3-dict-es_3.0.0-9_i386.deb
ooobasis3.0-en-us-help_3.0.0-9_i386.deb         openoffice.org3-dict-fr_3.0.0-9_i386.deb
ooobasis3.0-en-us-impress_3.0.0-9_i386.deb      openoffice.org3-draw_3.0.0-9_i386.deb
ooobasis3.0-en-us-math_3.0.0-9_i386.deb         openoffice.org3-en-us_3.0.0-9_i386.deb
ooobasis3.0-en-us-res_3.0.0-9_i386.deb          openoffice.org3-impress_3.0.0-9_i386.deb
ooobasis3.0-en-us-writer_3.0.0-9_i386.deb       openoffice.org3-math_3.0.0-9_i386.deb
ooobasis3.0-gnome-integration_3.0.0-9_i386.deb  openoffice.org3-writer_3.0.0-9_i386.deb
ooobasis3.0-graphicfilter_3.0.0-9_i386.deb      openoffice.org-ure_1.4.0-9_i386.deb[/COLOR]
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ sudo dpkg -i *.deb
```

then cd into the desktop-integration and do the same thing (even though it's only one deb it's quicker to just hit the up arrow two or three times to bring up the **sudo dpkg -i *.deb** again)

like this:
```
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS$ cd desktop-integration
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS/desktop-integration$ ls
[COLOR="Red"]openoffice.org3.0-debian-menus_3.0-9354_all.deb[/COLOR]
ryan@ryan-desktop:~/Desktop/OOo 3/DEBS/desktop-integration$ sudo dpkg -i *.deb
```

yeah, i did kind of copy the tutorial from the link, but you never know what might happen to the other site. thank you for the guidance **Hagar de l'Est**

Should I remove the old OOo form synaptic?
The other site says so. Or is it enough if I just do this directly?

---

### Post by Sonic Reducer on 2008-10-19
> **vittalp88 said:**
> Should I remove the old OOo form synaptic?
The other site says so. Or is it enough if I just do this directly?

thanks for pointing that out, i tried just installing it without removing the old packages, but it doesn't work. it cites a package conflict or something that IIRC.

open up synaptic, search for openoffice, and remove everything installed. **[COLOR="Red"]be careful, at first i simply highlighted all installed packages matching "openoffice" and i almost took out ubuntu-desktop with it. this is bad.[/COLOR]**

i went through, maybe highlighting and removing 3 or 4 at a time. if it comes up with the dialog asking if you want to remove other packages with it, read it carefully. some packages try to take ubuntu-desktop or gnome-applets with it.

after i did that i ran a _sudo apt-get autoremove_ to take out any remaining packages that aren't needed.

after you do that, then follow my original post

---

### Post by Partyboi2 on 2008-10-20
> **Sonic Reducer said:**
> thanks for pointing that out, i tried just installing it without removing the old packages, but it doesn't work. it cites a package conflict or something that IIRC.

open up synaptic, search for openoffice, and remove everything installed. **[COLOR=Red]be careful, at first i simply highlighted all installed packages matching "openoffice" and i almost took out ubuntu-desktop with it. this is bad.[/COLOR]**

i went through, maybe highlighting and removing 3 or 4 at a time. if it comes up with the dialog asking if you want to remove other packages with it, read it carefully. some packages try to take ubuntu-desktop or gnome-applets with it.

after i did that i ran a _sudo apt-get autoremove_ to take out any remaining packages that aren't needed.

after you do that, then follow my original post
ubuntu-desktop is a metapackage and is easy to reinstall, as removing it does not remove any other packages.

---

### Post by Sonic Reducer on 2008-10-20
> **Partyboi2 said:**
> ubuntu-desktop is a metapackage and is easy to reinstall, as removing it does not remove any other packages.

oh, well it sounded important

---

### Post by Partyboi2 on 2008-10-20
> **Sonic Reducer said:**
> oh, well it sounded important
Yep, it is important, specially if you wanted to install ubuntu-desktop on a machine that has not got it installed. :)

---

### Post by vijaym on 2008-10-20
it works and is easy. Much faster as well.

---

### Post by vice1 on 2008-11-03
Add

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

to your sources list

and reload or in the terminal

sudo apt-get update

proceed with upgrading OOo

Hope this helps.

---

### Post by slimx3m on 2008-11-28
> **vice1 said:**
> Add

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

to your sources list

and reload or in the terminal

sudo apt-get update

proceed with upgrading OOo

Hope this helps.

i tried this with hardy but it didn't work. any thoughts?

---

### Post by Skripka on 2008-11-28
> **slimx3m said:**
> i tried this with hardy but it didn't work. any thoughts?

The PPA packages have been taken down, due to a problem with Gnome and OOo3-which might result in a borked OOo3.  All you can do is wait for the problems to be resolved.

---

### Post by bangmalley on 2008-11-28
> **slimx3m said:**
> i tried this with hardy but it didn't work. any thoughts?
use the hardy version

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

---

### Post by slimx3m on 2008-11-28
> **Skripka said:**
> The PPA packages have been taken down, due to a problem with Gnome and OOo3-which might result in a borked OOo3.  All you can do is wait for the problems to be resolved.

thanx for the info, i didn't know this

> **bangmalley said:**
> use the hardy version

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

that is what i've been trying and when i try to update i get nothing :(.  but apparently there is some issues with the ppa packages.  hopefully this will be solve soon.

---

### Post by Hyper Tails on 2008-11-28
Thanks I want open office 3.0 too

---

### Post by ptreaster on 2009-04-18
After upgrading to Ooo3, my clipart gallery with all those extra graphics is gone! There is just the default set that you get with the Windows install and nothing more. I've tried to re-install the open clipart, but still no. Where do I go to find them once again?
Thanks y'all.:popcorn:

---

### Post by abn91c on 2009-04-18
> **ptreaster said:**
> After upgrading to Ooo3, my clipart gallery with all those extra graphics is gone! There is just the default set that you get with the Windows install and nothing more. I've tried to re-install the open clipart, but still no. Where do I go to find them once again?
Thanks y'all.:popcorn:
Are you on windows or linux? the clipart in found in synaptic
you can do also```
sudo apt-get install openclipart-openoffice.org
```

---

