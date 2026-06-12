---
title: "GREP is broken?"
date: 2008-07-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-07-14
How It Should Be
```
tim@server:~$ grep --version
grep (GNU grep) 2.5.1

Copyright 1988, 1992-1999, 2000, 2001 Free Software Foundation, Inc.
Dit is vrije programmatuur; zie de broncode voor kopieervoorwaarden.
Er is GEEN garantie; zelfs niet voor VERKOOPBAARHEID of GESCHIKTHEID
VOOR EEN BEPAALD DOEL.

tim@server:~$ echo Test | grep Test
Test
tim@server:~$ echo Test | grep test -i
Test
tim@server:~$ 
```

How Ubuntu Does It
```
tim@desktop:~$ grep --version
GNU grep 2.5.3

Copyright (C) 1988, 1992-2002, 2004, 2005  Free Software Foundation, Inc.
Dit is vrije software; zie de programmatekst voor de kopieervoorwaarden.
Er is GEEN garantie; zelfs niet voor VERKOOPBAARHEID of GESCHIKTHEID
VOOR EEN BEPAALD DOEL.

tim@desktop:~$ echo Test | grep Test
Test
tim@desktop:~$ echo Test | grep test -i
tim@desktop:~$ 
```


Hmm :-k doesn't this break like 75% of all scripts?

---

### Post by psyke83 on 2008-07-14
> **MALEADt said:**
> How It Should Be
```
tim@server:~$ grep --version
grep (GNU grep) 2.5.1

Copyright 1988, 1992-1999, 2000, 2001 Free Software Foundation, Inc.
Dit is vrije programmatuur; zie de broncode voor kopieervoorwaarden.
Er is GEEN garantie; zelfs niet voor VERKOOPBAARHEID of GESCHIKTHEID
VOOR EEN BEPAALD DOEL.

tim@server:~$ echo Test | grep Test
Test
tim@server:~$ echo Test | grep test -i
Test
tim@server:~$ 
```

How Ubuntu Does It
```
tim@desktop:~$ grep --version
GNU grep 2.5.3

Copyright (C) 1988, 1992-2002, 2004, 2005  Free Software Foundation, Inc.
Dit is vrije software; zie de programmatekst voor de kopieervoorwaarden.
Er is GEEN garantie; zelfs niet voor VERKOOPBAARHEID of GESCHIKTHEID
VOOR EEN BEPAALD DOEL.

tim@desktop:~$ echo Test | grep Test
Test
tim@desktop:~$ echo Test | grep test -i
tim@desktop:~$ 
```


Hmm :-k doesn't this break like 75% of all scripts?

I noticed this too... we should see if a bug exists, or else open a new one.

---

### Post by sisco311 on 2008-07-14
works here

> grep --version 
GNU grep 2.5.3

Copyright (C) 1988, 1992-2002, 2004, 2005  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
> cat /etc/issue
Ubuntu 8.04.1 \n \l > uname -a
Linux *xyz* 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
> echo Test | grep Test
Test
> echo Test | grep test -i
Test


---

### Post by Stunts on 2008-07-14
Works fine in here too...

---

### Post by forger on 2008-07-14
you have an older version or gutsy?

This is on hardy heron:
```
$ grep --version
GNU grep 2.5.3

Copyright (C) 1988, 1992-2002, 2004, 2005  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ echo Test | grep Test
Test
$ echo Test | grep test -i
Test
```

---

### Post by brokenLockpick on 2008-07-14
works for me as well

Edit: on Hardy

---

### Post by psyke83 on 2008-07-14
No, it doesn't work on Intrepid:
```
conn@dimension:~$ echo Test | grep test -i
conn@dimension:~$ 
```

---

### Post by MALEADt on 2008-07-14
On intrepid too, comparing with an ancient debian install.

---

### Post by sisco311 on 2008-07-14
```
echo Test | grep test --ignore-case
```or
```
echo Test | grep -i test
```works?

---

### Post by MALEADt on 2008-07-14
Doesn't work either:
```
tim@desktop:~$ echo Test | grep test -i
tim@desktop:~$ echo Test | grep -i test
tim@desktop:~$ echo Test | grep --ignore-case test
tim@desktop:~$ echo Test | grep test --ignore-case
```

However...
(suspensful music)
```
tim@desktop:~$ echo test | grep Test -i
test
```

Grep really went haywire :)
I'll make a launchpad entry tomorrow, if none exist already.

---

### Post by sisco311 on 2008-07-14
interesting...
it's a grep bug, echo bug, bash or the pipe....???

did you try to avoid the echo command:
```
grep -i test ./filename
```

---

### Post by mattduckman on 2008-07-14
it's a grep bug. check this out

```

$ cat file 
Test1
test2
tEST3
$ grep -i test file
test2
$ grep -i Test file
test2
$ grep -i tEST file
test2

```

the 'i' flag is messing up normal pattern matches too.

---

### Post by sisco311 on 2008-07-14
ok. 

from the man page:> 
 -y     Obsolete synonym for -i.

can somebody test if the -y option works?

looks like the pattern is converted to lowercase but the text in the file is not.

---

### Post by mattduckman on 2008-07-14
the 'y' flag produces the exact same output as above

---

