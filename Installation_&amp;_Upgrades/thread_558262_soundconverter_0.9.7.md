---
title: "soundconverter 0.9.7?"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by underworld288 on 2007-09-23
I am trying to install the newest version of soundconverter, the one mentioned in the title. The problem is that every time I try to configure it it gives me an error message.

```
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
```

Can someone please give some advice?

---

### Post by Pumalite on 2007-09-23
sudo apt-get install build-essential
Make sure your headers match your kernel version

---

### Post by underworld288 on 2007-09-23
thanks for the quick reply back. that helped fix that problem but the new problem is when running the make command. 

```
Making all in po
make[1]: Entering directory `/home/underworld288/Desktop/soundconverter-0.9.7/po'
file=`echo fr | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file fr.po
/bin/sh: -o: not found
make[1]: *** [fr.gmo] Error 127
make[1]: Leaving directory `/home/underworld288/Desktop/soundconverter-0.9.7/po'
make: *** [all-recursive] Error 1

```

it gives me that output when running the make command. can someone help me?

---

### Post by Pumalite on 2007-09-23
Make sure that 'automake' and 'autoconf' are installed.

---

### Post by underworld288 on 2007-09-23
ok i have installed both of those programs and the problem is still their, what now?

---

### Post by Pumalite on 2007-09-23
Beats me.

---

