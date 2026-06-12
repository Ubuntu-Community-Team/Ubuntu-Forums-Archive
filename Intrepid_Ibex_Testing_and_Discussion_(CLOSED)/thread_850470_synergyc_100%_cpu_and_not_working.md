---
title: "synergyc 100% cpu and not working"
date: 2008-07-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by coder_cotton on 2008-07-05
Has anyone had any luck getting the Synergy client working on the new 2.2.26 kernel?  It immediately consumes 100% cpu and while it connects, it never accepts any input and quickly disconnects from the server machine.

```
NOTE: accepted client connection
NOTE: new client is unresponsive
```

Thanks,
Cotton

---

### Post by klange on 2008-07-26
Guess this is a bit of a bump.

I can confirm having the same problems.

Server machine is running Hardy and displays (pretty much) the same output: 

```
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,272: new client is unresponsive
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,272: new client is unresponsive
NOTE: CClientProxyUnknown.cpp,272: new client is unresponsive
```

Client machine is running Ibex and is unresponsive to repeated attempts to close it with Ctrl+C (running with -f argument to collect output). End up having to kill -9 it.

---

### Post by tumult on 2008-09-15
Same problem here. I'm guessing there's still no fix?

---

### Post by Nullack on 2008-09-15
Wheres the bug report?

---

### Post by tumult on 2008-09-15
ok, I have a fix. as per this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029)

1. get synergy 1.3.1 sources
2. apply this patch [http://svn.pardus.org.tr/pardus/devel/applications/network/synergy/files/synergy-1.3.1-gcc43.patch](http://svn.pardus.org.tr/pardus/devel/applications/network/synergy/files/synergy-1.3.1-gcc43.patch) which will allow synergy to build in newer gcc (stricter includes now)
3. apply this patch [http://launchpadlibrarian.net/15571785/synergy-hang-fix.patch](http://launchpadlibrarian.net/15571785/synergy-hang-fix.patch)
4. do ./configure -x-libraries /usr/lib -x-xincludes /usr/include, make sure you have libxtst-dev if you get an error about missing XTest
5. edit your cxxflags (i think? can't remember) in the lib/arch and lib/platform Makefiles to not include -Werror if you're getting errors running make

it should make and make install properly, and synergyc should work mostly ok. i did this on intrepid alpha 5, on an intel atom 230 board (i386 kernel, not x64)

---

### Post by damoxc on 2008-09-15
Orrr,

Go grab the package from Debian Sid which works perfectly anyway :p

[http://packages.debian.org/sid/synergy](http://packages.debian.org/sid/synergy)

---

### Post by NotQuiteSonic on 2008-09-15
I created a bug here for a similar problem with synergys.

[https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/270575](https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/270575)

---

### Post by dro0g on 2008-09-20
> **damoxc said:**
> Orrr,

Go grab the package from Debian Sid which works perfectly anyway :p

[http://packages.debian.org/sid/synergy](http://packages.debian.org/sid/synergy)

Thank you, that worked great!

---

### Post by UbuWu on 2008-09-25
Synergy in intrepid has been updated and works perfectly now.

---

