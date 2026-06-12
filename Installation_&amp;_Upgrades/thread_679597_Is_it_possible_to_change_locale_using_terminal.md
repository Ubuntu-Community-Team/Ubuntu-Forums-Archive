---
title: "Is it possible to change locale using terminal?"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2008-01-27
Good day everyone!
I write a postinstall script that installs additional packages, languages, tweaks gnome, etc, etc... My locale in ru_RU but the interface is english by default (I choose english during installation 'cause many machines I deal with do not have internet connection), Is it possible to change it to Russian or any other language in terminal without using gnome-language-selector?

---

### Post by jeffus_il on 2008-01-27
Use the LANG environment variable:
> **Using Linux in your native language**

  Though I personally hate seeing improvised Norwegian translations of popular English computer terms, a lot of people find it easier to use Linux in their native language. Although localization settings for software like Gnome or KDE may be altered simply by using a control panel, users of other software solutions may need to change some settings called environment variables. The names of these variables begin with LC_, and LC_CTYPE should be the most important one for enabling input methods.  Additionally, LANG and in rare cases LANGUAGE might be needed to change the language in some programs.  Changing these variables is as simple as finding the country code for your country, and using a command line. First, run the command locale -a and find the appropriate code for your language in the list. Try Google if you're unsure of which one it is. 
 The system language then needs to be set by a script that runs every time the system starts up. On Gentoo Linux, the correct file is apparently called /etc/env.d/02locale. For a lot of systems, though, a quick and alomst certainly incorrect way is to enter the necessary codes into the startup script rc.local, which will unfortunately probably only be run near the very end of the bootup procedure. Assuming that our language of choice is the beautiful "Example Language", the code might be as follows: 
 export LC_CTYPE=example_LANGUAGE
export LANG=example_LANGUAGE
export LANGUAGE=example_LANGUAGE

 Et voila. Upon rebooting your machine a lot of applications should start appearing in the language of your choice. 
 Another neat feature is the ability to run just one program in another language without changing your settings. Simply specify the variables before your program name on a command line: 
 LANG=example_LANGUAGE LC_CTYPE=example_LANGUAGE LANGUAGE=example_LANGUAGE *my_program* 

  




from:
[http://home.no.net/david/i18n.php](http://home.no.net/david/i18n.php)

---

### Post by PryGuy on 2008-01-27
Thanks a lot. I couldn't find where the Gentoo's /etc/env.d/02locale alternative in Ubuntu is... :(

---

### Post by zvacet on 2008-01-27
Look in **/usr/share/i18n/locales**

---

### Post by PryGuy on 2008-01-27
What file should I look for there?

---

### Post by zvacet on 2008-01-28
Read [this](http://gramps-project.org/wiki/index.php?title=Howto:_Change_the_language_of_reports).I hope you find it helpfull.

---

