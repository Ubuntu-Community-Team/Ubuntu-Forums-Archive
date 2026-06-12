---
title: "No sound with flash in Konqueror"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-02-26
Basically just migrated from gnome to kde, only to find out i cant get sound from flash, all other sounds work, just flash

anyone got any ideas?

thanks
Will

---

### Post by XArgentum on 2010-03-25
same here

i cant get any sound out of flash nor from vlc but any other app works just fine

HW macbook pro 5,5 
SW Only os kubuntu LL beta 1 amd64

hope this gets fixed for the final release 

regards

---

### Post by iscreamatpink on 2010-03-25
try flash 10.1

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz)

---

### Post by XArgentum on 2010-03-28
hi all

thanks iscreamatpink but i had no luck with flash 10.1 beta 3,
i bet this is an ALSA/pulse/phonon issue 
ill just wait for the LL beta 2 or maybe ror the rc

thanks any way

---

### Post by in-dust-rial on 2010-04-16
hi all,
same here:
2.6.32-21-generic #31-Ubuntu SMP 
Tue Apr 13 20:37:36 UTC 2010       (i.e. generic)
x86_64 GNU/Linux

installed via aptitude (installer and nonfree package)
both did not help.

however, workaround:
load flash in browser
open folder /tmp/ 
open file called Flash* with videoplayer (which can handle flv)

thats very fine also to save recources on older machines, since flash is a pain in the ***.
I also use this technique to load videos in advance to watch them offline.

would be nice to have a script :)

big issue:
vlc just plays until the position of the movie, which was alredy loaded, when file was opened by vlc.



@doerayme: enjoy your KDE :)

---

### Post by in-dust-rial on 2010-04-16
sorry for dbl posting!

BUT i do want to make this a quick to read answer and solution:
(please set the topic to solved :)

I just remembered, that i had the same issue two years ago...



[B][U]```
solution:
-go to "mixer" (the kde sound-switch) 
-enable PCM channel 
-give it some juice

```[/U][/B]


worked for me,
now the second year ( and on a different platform ... )


p.s.: if its not the PCM try some other channels ...

---

