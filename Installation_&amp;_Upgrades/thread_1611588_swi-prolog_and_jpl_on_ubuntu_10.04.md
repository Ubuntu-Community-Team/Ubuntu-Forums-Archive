---
title: "swi-prolog and jpl on ubuntu 10.04"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by ubuaverill on 2010-11-02
Hi,

On Ubuntu 10.04 I installed swipl-5.10.1 from the source code. All the
prolog examples that access jpl work from the command line. However, the
java examples that access prolog give this error:

java: symbol lookup
error: /home/bka/lib/swipl-5.10.1/lib/i686-linux/libjpl.so: undefined
symbol: PL_is_initialised

Others who have reported this problem suggest it is due to incorrect
data in some of the 'path' variables, particularly with
java.library.path. Below I have printed the environment variables used
in the env.sh script. From these data the cause of the problem escapes
me. I have done something amiss but what?

PLBASE is /home/bka/lib/swipl-5.10.1
PLARCH is i686-linux
PLLIBDIR is /home/bka/lib/swipl-5.10.1/lib/i686-linux
JPLJAR is /home/bka/lib/swipl-5.10.1/lib/jpl.jar
LD_LIBRARY_PATH
is /home/bka/lib/swipl-5.10.1/lib/i686-linux:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/home/bka/lib/swipl-5.10.1/lib/i686-linux
CLASSPATH
is .:/home/bka/lib/swipl-5.10.1/lib/jpl.jar:/home/bka/lib/swipl-5.10.1/lib/jpl.jar

I hope someone in the swi-prolog community can make me a happy camper.

thanks  --brian

---

