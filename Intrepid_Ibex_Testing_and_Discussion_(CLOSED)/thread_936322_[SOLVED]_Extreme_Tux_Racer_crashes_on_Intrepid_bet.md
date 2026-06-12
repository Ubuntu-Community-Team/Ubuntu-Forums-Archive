---
title: "[SOLVED] Extreme Tux Racer crashes on Intrepid beta"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shane19174 on 2008-10-02
When I try to run Extreme Tux Racer on Ibex beta, upgraded from 8.04.1, I get the following:

[INDENT]shane@shane-desktop:~$ etracer
Extreme TuxRacer SVN Development --  [http://www.extremetuxracer.com](http://www.extremetuxracer.com) 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

 error evalating language-settings file /usr/share/games/etracer/translations/languages.tcl : falsecouldn't read file "/usr/share/games/etracer/translations/languages.tcl": no such file or directory
error evalating language file /usr/share/games/etracer/translations/en_GB.tcl : falsecouldn't read file "/usr/share/games/etracer/translations/languages.tcl": no such file or directorycouldn't read file "/usr/share/games/etracer/translations/en_GB.tcl": no such file or directory
 error evalating model list file /usr/share/games/etracer/models.tcl : falsecouldn't read file "/usr/share/games/etracer/translations/languages.tcl": no such file or directorycouldn't read file "/usr/share/games/etracer/translations/en_GB.tcl": no such file or directorycouldn't read file "/usr/share/games/etracer/models.tcl": no such file or directory
*** etracer error: error evalating /usr/share/games/etracer/etracer_init.tcl: falsecouldn't read file "/usr/share/games/etracer/translations/languages.tcl": no such file or directorycouldn't read file "/usr/share/games/etracer/translations/en_GB.tcl": no such file or directorycouldn't read file "/usr/share/games/etracer/models.tcl": no such file or directorycouldn't read file "etracer_init.tcl": no such file or directory
Please check the value of `data_dir' in ~/.etracer/options and make sure it
points to the location of the latest version of the ETRacer-data files.
shane@shane-desktop:~$ 
[/INDENT]

I've tried reinstalling etracer and the data package, but the result is the same. Any ideas?

Thanks,
shane

---

### Post by shane19174 on 2008-10-03
OK, I realize that Extreme Tux Racer is not the highest priority, but I'm trying to figure out what the upgrade did to cause this problem, as it may be sympomatic of other problems elsewhere.

Any suggestions?

---

### Post by shane19174 on 2008-10-06
Just to close this off: the issue was solved by purging and then reinstalling etracer.

---

