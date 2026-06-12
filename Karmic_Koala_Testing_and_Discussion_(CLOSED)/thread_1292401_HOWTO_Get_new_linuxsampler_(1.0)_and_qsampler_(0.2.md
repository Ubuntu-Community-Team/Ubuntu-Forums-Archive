---
title: "HOWTO: Get new linuxsampler (1.0) and qsampler (0.2.2-1) work"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by barisurum on 2009-10-15
Hey, rejoice ubuntu studio users!

I've been struggling to get linuxsampler, qsampler to work for some time. I tried many things from compiling to installing them under wine (yes a shame but I was curious :)) and believe me it was a disaster!) and finally I found this ppa archive by David Konsumer:

[https://launchpad.net/~david-konsumer/+archive/konsumer](https://launchpad.net/~david-konsumer/+archive/konsumer)

Brand new linuxsampler, qsampler stuff there including amd64 builds! downloaded them all and tried to install liblinuxsampler (1.0) 

But there were dependency problems with libjack in liblinuxsampler package and there's no package like that in our repos so I searched virtually all the web (just joking) and found this solution, guess where? Of course in our beloved ubuntu forums again:

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

using the second script I found there (use the script with gedit as the editor its easier) I was able to change the debian control file inside the liblinuxsampler deb and removed the libjack dependency on the depends line. I also changed the libgig (with version number) to libgig6 to look like: libgig6 (>= 3.3.0) and removed the other unneeded libgig6 entry. And after that liblinuxsampler installed no problem. 

There was another depends problem with linuxsampler package (libgig problem) so I edited that with the script to change libgig to libgig6. Installed it too without problems.

The rest is easy, just install qsampler and start rocking :) :guitar:

I would like to thank David Konsumer for his excellent (ok maybe not excellent but efficient enough) ppa archive, loevborg for this wonderful videbcontrol script and motin for modifying it to work with gedit.

Cheers :popcorn:

---

### Post by barisurum on 2009-10-17
Update: Jsampler (fantasia 0.9) works with this setup too so no need to use the buggy qsampler. I experienced some nasty bugs and recommend using fantasia instead. Hope qsampler gets better soon because java is a bloated resource hungry monster.

---

