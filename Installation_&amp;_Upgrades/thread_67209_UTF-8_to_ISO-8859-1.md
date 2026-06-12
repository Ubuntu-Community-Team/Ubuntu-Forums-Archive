---
title: "UTF-8 to ISO-8859-1??"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-09-19
How do I change the default character encoding to ISO-8859-1 in Ubuntu? Currently it uses UTF-8 But I login to a lot of systems that use ISO-8859-1 and would like to change Ubuntu to use ISO-8859-1 instead.

Hope someone can help!

---

### Post by macgyver2 on 2005-09-19
Open up a terminal and type

sudo dpkg-reconfigure locales

Make sure the ISO-8859-1 option for you language of choice is selected (you can leave the UTF-8 one selected too).  When you go to the next page it should ask which one you want as default.  Choose the ISO-8859-1 for your language.

I think that should do it.

---

### Post by AndyT on 2005-09-20
[QUOTE=macgyver2]Open up a terminal and type

sudo dpkg-reconfigure locales

Make sure the ISO-8859-1 option for you language of choice is selected (you can leave the UTF-8 one selected too).  When you go to the next page it should ask which one you want as default.  Choose the ISO-8859-1 for your language.

I think that should do it.[/QUOTE]
 It doesn't seem to work for me, I get the following error message:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed

```

---

### Post by mlomker on 2005-09-20
> LANGUAGE = "en_GB:en",

That doesn't look valid to me.  Perhaps you've made a few changes already trying to figure this one out?

**locale** should give you the current settings and **locale -a** the available option.

You may have to edit your /etc/environment file so that it is a valid option. An alternative to the reconfigure command is to edit the /etc/locale.gen file and then execute **sudo locale-gen** afterward.  You'll want your new locale listed first.

---

### Post by charlieg on 2005-11-23
This fixed things for me:
```
$ apt-get install -f
```

I did it in the middle of the upgrade from Hoary to Breezy (after something else failed) and it made those locale error messages disappear for the subsequent apt-get dist-upgrade.

---

