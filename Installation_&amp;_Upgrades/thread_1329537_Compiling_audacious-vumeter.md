---
title: "Compiling audacious-vumeter"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Doctor Drive on 2009-11-17
Hi guys, I'm trying to compile audacious-vumeter (got the source from [http://www.netswarm.net/](http://www.netswarm.net/)) for my Ubuntu Karmic (audacious 2.1) but I get this error:
[php]
main.c: In function 'vumeter_init':
main.c:257: error: 'struct _AudaciousFuncTableV1' has no member named 'get_dock_window_list'
main.c:259: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_add_window'
main.c:259: error: 'struct _AudaciousFuncTableV1' has no member named 'get_dock_window_list'
main.c: In function 'win_release':
main.c:424: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_is_moving'
main.c:425: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_move_release'
main.c: In function 'win_press':
main.c:452: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_move_press'
main.c:452: error: 'struct _AudaciousFuncTableV1' has no member named 'get_dock_window_list'
main.c: In function 'win_motion':
main.c:458: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_is_moving'
main.c:459: error: 'struct _AudaciousFuncTableV1' has no member named 'dock_move_motion'
main.c: In function 'vumeter_cleanup':
main.c:503: error: 'struct _AudaciousFuncTableV1' has no member named 'get_dock_window_list'
main.c:504: error: 'struct _AudaciousFuncTableV1' has no member named 'get_dock_window_list'
make[2]: *** [main.lo] Error 1
make[2]: Leaving directory `/home/doctor/Desktop/audacious-vumeter-0.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/doctor/Desktop/audacious-vumeter-0.8'
make: *** [all] Error 2

[/php]

Got any ideas?

---

### Post by audiomick on 2009-11-17
Can't help with the problem, sorry, but: isn't that in the repositories? I am pretty sure that it is on Ubuntu Studio. In fact, if you have use for a VU meter, maybe you should be using Ubuntu Studio anyway.

---

### Post by Doctor Drive on 2009-11-17
cannot fetch repositories
> 
doctor@Doctor:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.


---

### Post by audiomick on 2009-11-17
It looks like it can't find a key that it is happy with. Don't know how to fix that. sorry

---

### Post by Doctor Drive on 2009-11-17
yeap. it can't get anything
> 
W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/karmic/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/karmic/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.



allright, thanks 4 trying 2 help anyway...

---

