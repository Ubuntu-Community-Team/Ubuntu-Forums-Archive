---
title: "some errors while updating via apt-get"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by robgr85 on 2008-01-05
Hi!

There is some problem while updating my ubuntu edgy eft. apt-get displays the following errors after apt-get upgrade command. here is something, that I believe causes the rest of the errors. How to fix that

```

Konfigurowanie ttf-opensymbol (2.0.4-0ubuntu7) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/home/rob/.fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning

```

and the rest of the apt-get info printed on screen, sorry that it is in my native language.
```

dpkg: b&#322;&#261;d przetwarzania ttf-opensymbol (--configure):
 podproces post-installation script zwróci&#322; kod b&#322;&#281;du 5
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-core:
 openoffice.org-core zale&#380;y od ttf-opensymbol; jednak&#380;e:
  Pakiet ttf-opensymbol nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-core (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-draw:
 openoffice.org-draw zale&#380;y od openoffice.org-core (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-draw (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-impress:
 openoffice.org-impress zale&#380;y od openoffice.org-core (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
 openoffice.org-impress zale&#380;y od openoffice.org-draw (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-draw nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-impress (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-kde:
 openoffice.org-kde zale&#380;y od openoffice.org-core (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-kde (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie python-uno:
 python-uno zale&#380;y od openoffice.org-core (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania python-uno (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-writer:
 openoffice.org-writer zale&#380;y od openoffice.org-core (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
 openoffice.org-writer zale&#380;y od python-uno (>= 2.0.4); jednak&#380;e:
  Pakiet python-uno nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-writer (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-common:
 openoffice.org-common zale&#380;y od openoffice.org-core (>> 2.0.4~rc3) | openoffice.org-core-experimental (>> 2.0.4~rc3); jednak&#380;e:
  Pakiet openoffice.org-core nie jest jeszcze skonfigurowany.
  Pakiet openoffice.org-core-experimental nie jest zainstalowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-common (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-java-common:
 openoffice.org-java-common zale&#380;y od openoffice.org-common; jednak&#380;e:
  Pakiet openoffice.org-common nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-java-common (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-style-default:
 openoffice.org-style-default zale&#380;y od openoffice.org-common (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-common nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-style-default (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie openoffice.org-style-crystal:
 openoffice.org-style-crystal zale&#380;y od openoffice.org-common (= 2.0.4-0ubuntu7); jednak&#380;e:
  Pakiet openoffice.org-common nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania openoffice.org-style-crystal (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-default
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code (1)
rob@rob-laptop:~$                                                 

```

---

### Post by PmDematagoda on 2008-01-05
Try:-
```
sudo dpkg --configure -a
```

One more thing, I had difficulty understanding your error message and the solution I gave is based on what it looks like, the solution would be more accurate if you could please post an English version of the error. But the command I gave is not very harmful and can be used even if there is no problem without much harm.

---

### Post by robgr85 on 2008-01-06
it would take time to translate everything, so I will try to translate shortly what is on, the first one translated:

```

Configuring ttf-opensymbol (2.0.4-0ubuntu7) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/home/rob/.fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning

```

the rest is all the same through any of the package, so I will translate only info from the first one

```

dpkg: error while processing ttf-opensymbol (--configure):
 subthread post-installation script returned error code 5  //subthread can be (I think) subprocess, minor process/thread, can't find apropriate word now
dpkg: problems with dependencies  preclude configuring openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; but:
  Package ttf-opensymbol is not configured yet.

```

Hope that it is enough. I think that the problem exists because of first part (code listning)... but have no idea how to solve it.

dpkg --configure -a didn't helped. Output is the same.

---

