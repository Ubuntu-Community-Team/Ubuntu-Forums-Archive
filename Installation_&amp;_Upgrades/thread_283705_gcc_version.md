---
title: "gcc version"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by meskalin on 2006-10-24
i get this message when i want to run make: 
> /usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Kommando nicht gefunden


i have gcc version 4.0.2 when i test it with gcc -v why this stupid message about 3.4 ](*,) 

gcc.version.sh: 
> compiler="$*"

MAJOR=$(echo __GNUC__ | $compiler -E -xc - | tail -n 1)
MINOR=$(echo __GNUC_MINOR__ | $compiler -E -xc - | tail -n 1)
printf "%02d%02d\\n" $MAJOR $MINOR 

---

### Post by taurus on 2006-10-24
Maybe whatever you try to compile requires an older version of gcc!!!  You still can install version 3.4 with synaptic if you want...

---

