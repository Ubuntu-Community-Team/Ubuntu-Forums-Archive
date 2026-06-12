---
title: "Compiling GXMAME"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by oshi on 2005-07-13
When I try to run 'Make' it spits this out:

```
make[2]: Entering directory `/home/mykel/files/gxmame-0.35beta1/po'
( if test 'x.' != 'x.'; then \
    posrcprefix='../'; \
  else \
    posrcprefix="../"; \
  fi; \
  rm -f POTFILES-t POTFILES \
    && (sed -e '/^#/d'                                          \
            -e "s/^\[.*\] +//"                                  \
            -e '/^[     ]*$/d'                          \
            -e "s@.*@   $posrcprefix& \\\\@" < ./POTFILES.in    \
        | sed -e '$s/\\$//') > POTFILES-t \
    && chmod a-w POTFILES-t \
    && mv POTFILES-t POTFILES )
mv: cannot move `POTFILES-t' to `POTFILES': File exists
make[2]: *** [POTFILES] Error 1
make[2]: Leaving directory `/home/mykel/files/gxmame-0.35beta1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mykel/files/gxmame-0.35beta1'
make: *** [all] Error 2

``` 

anyone know how to solve this error?

---

### Post by runenes on 2005-07-13
Have you tried make clean, or alt. delete the dir and start anew.

---

### Post by oshi on 2005-07-13
[QUOTE=runenes]Have you tried make clean, or alt. delete the dir and start anew.[/QUOTE]


Yes. Spits out the same stuff.

---

### Post by oshi on 2005-07-13
Well I gave up on trying to compile and added 

```
deb http://anarxia.dyndns.org/debian unstable main
deb-src http://anarxia.dyndns.org/debian unstable main
```

to /etc/apt/sources.list and it runs fine from that build.

---

