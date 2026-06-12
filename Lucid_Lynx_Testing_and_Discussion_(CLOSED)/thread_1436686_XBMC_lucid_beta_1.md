---
title: "XBMC lucid beta 1"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uppitychev on 2010-03-23
I couldn't find any support through XBMC in lucid. The repo has only a few packages in it! 

I do realize it is just at beta stages and many things are not finished but has anyone successfully installed XBMC in the 10.04 beta 1?

thanks!

--

Worked on this all day. tried compiling from source.
I give up, ill just wait for the packaged official release in april (hopefully).

EDIT::

simple fix. i'm an idiot.

---

### Post by ElSlunko on 2010-03-23
> **Uppitychev said:**
> I couldn't find any support through XBMC in lucid. The repo has only a few packages in it! 

I do realize it is just at beta stages and many things are not finished but has anyone successfully installed XBMC in the 10.04 beta 1?

thanks!

--

Worked on this all day. tried compiling from source.
I give up, ill just wait for the packaged official release in april (hopefully).

EDIT::

simple fix. i'm an idiot.

What was the problem/fix?

---

### Post by tnat on 2010-03-23
I'm also interested in finding out, how to install XBMC without compiling!

---

### Post by meborc on 2010-03-23
you could just use the karmic xbmc ppa to install it... i have not tried it, but should be possible ;)

EDIT: seems i was right - [http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

---

### Post by mullerjk on 2010-03-23
I'm also tried and no sucess too.

to me was should this message.

xbmc-standalone:
 Depende: xbmc-data mas não será instalado
 Depende: xbmc-skin-confluence mas não será instalado ou
     xbmc-skin-pm3-hd mas não será instalado
 Depende: xbmc-web-pm3 mas não será instalado

:) i'm from Brazil.

---

### Post by mullerjk on 2010-03-23
> **meborc said:**
> you could just use the karmic xbmc ppa to install it... i have not tried it, but should be possible ;)

EDIT: seems i was right - [http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

This Step-by-step doesn't work to me.

I also tried first :(

---

### Post by tcchris on 2010-03-23
You can add "http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu" to the Software sources and install

I did this , the menus worked fine , but movies just show a brown screen with sound . This could be due to my video card/driver though

---

### Post by Uppitychev on 2010-03-23
I tried adding the karmic PPA to install from that with no success
i eventually just used svn, installed all the dependencies individually and compiled.

but i did need a few of the packages from the karmic repository and that was the fix, i hadnt changed the distro in /etc/apt/sources.list from lucid to karmic yet.

But i successfully compiled from the xbmc svn.
everything works!

EDIT

i used this page for help ([http://wiki.xbmc.org/?title=HOW-TO_compile_XBMC_for_Linux_from_source_code](http://wiki.xbmc.org/?title=HOW-TO_compile_XBMC_for_Linux_from_source_code))
i just installed the required packages listed in README.linux by hand as opposed to using 
```

$ sudo apt-get build-dep xbmc
```

---

### Post by Rob2687 on 2010-03-23
As mentioned above it's in the Lucid team-xbmc-svn ppa.

For some reason it doesn't show up on the launchpad page but the packages are there.

---

### Post by cnewsgrp on 2010-04-10
> **mullerjk said:**
> I'm also tried and no sucess too.

to me was should this message.

xbmc-standalone:
 Depende: xbmc-data mas não será instalado
 Depende: xbmc-skin-confluence mas não será instalado ou
     xbmc-skin-pm3-hd mas não será instalado
 Depende: xbmc-web-pm3 mas não será instalado

:) i'm from Brazil.
I am from USA and I get same message in English

---

