---
title: "Is sun-java6-plugin 64-bit on 64-bit install?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-10-03
A discussion started on a local Ubuntu Forum and I am not sure about the answer on the above question ... I'm accustomed on installing that plug-in from early releases of java-plug-in and have slept during all the development of that package in Karmic. Any ideas?

---

### Post by FrancoNero on 2009-10-03
in my opinion, if one were to install a 64bit operating system, the software (including plugins) on that system should all be 64bit, which is also why I'm furious over flash32bit (in the damn ndispluginwrapper thingy) comes delivered with Karmic still....

why is nobody taking 64bit seriously I wonder....

---

### Post by dinxter on 2009-10-03
either icedtea6-plugin or sun-java6-plugin are installable on 64 bit

---

### Post by zika on 2009-10-03
> **dinxter said:**
> either icedtea6-plugin or sun-java6-plugin are installable on 64 bitThe question is not if they were installable, the question is about that libnpjp2.so is or is not 64-bit in sun-java6-plugin. I think it is not. I have 64-bit libnpjp2.so installed separately ... It is not clearly written anywhere that I could find.

---

### Post by zika on 2009-10-03
> **FrancoNero said:**
> in my opinion, if one were to install a 64bit operating system, the software (including plugins) on that system should all be 64bit, which is also why I'm furious over flash32bit (in the damn ndispluginwrapper thingy) comes delivered with Karmic still....
why is nobody taking 64bit seriously I wonder....You can, always, install 64-bit alpha flash plugin separately and uninstall all that 32-bit-to-64-bit patches ...
Update: From Your other post I realized that You already know this. Sorry.

---

### Post by DougieFresh4U on 2009-10-03
> **zika said:**
> The question is not if they were installable, the question is about that libnpjp2.so is or is not 64-bit in sun-java6-plugin. I think it is not. I have 64-bit libnpjp2.so installed separately ... It is not clearly written anywhere that I could find.

I think I understand what you are asking, and I have wondered the same.
If I have 64 bit Karmic installed, and I go to Synaptic or the new Software Center and check the Sun Java and click to install, is IT installing a 64 bit version? :confused:

---

### Post by Keyper7 on 2009-10-03
The answer is [yes](http://java.sun.com/javase/6/webnotes/6u12.html) since [Jaunty](http://packages.ubuntu.com/fr/jaunty/sun-java6-plugin).

If you need proof:

```

$ file /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not stripped

```

---

### Post by zika on 2009-10-04
> **Keyper7 said:**
> The answer is [yes]("http://java.sun.com/javase/6/webnotes/6u12.html") since [Jaunty]("http://packages.ubuntu.com/fr/jaunty/sun-java6-plugin").

If you need proof:

```

$ file /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not stripped

```Thank You very much. It solved my dilemma.

---

### Post by FrancoNero on 2009-10-04
I would love a tool that I could run in Karmic that would tell me if i really am running a 64bit OS or if I am tricked and by default lots of 32bit stuff is installed (like flash)

---

### Post by Keyper7 on 2009-10-04
> **FrancoNero said:**
> I would love a tool that I could run in Karmic that would tell me if i really am running a 64bit OS or if I am tricked and by default lots of 32bit stuff is installed (like flash)

Try to remove the libc6-i386 package and see which other packages would be removed as a consequence.

Since libc is the mother of all dependencies, I believe this would cover all cases except for non-repository ones.

---

### Post by nanog on 2009-10-04
> Try to remove the libc6-i386 package and see which other packages would be removed as a consequence.

Oh my. If you are not running 64 bit and press Y...**[COLOR="Red"]KABOOM[/COLOR]**

The safer thing to do would be to remove ia32libs (bloated piece of cr*p).

---

### Post by Keyper7 on 2009-10-04
> **nanog said:**
> Oh my. If you are not running 64 bit and press Y...**[COLOR="Red"]KABOOM[/COLOR]**

The safer thing to do would be to remove ia32libs (bloated piece of cr*p).

If he's running a 32-bit system the risk lies in removing libc, not libc-i386. I think.

And ia32-libs is a metapackage that includes libc-i386 and other things. There's always the possibility that a 32-bit program installed libc-i386 as a dependency before the user installed ia32-libs, so removing ia32-libs would not remove such program.

---

### Post by tuxxy on 2009-10-04
Yes and you can check which it is by the package name

---

### Post by FrancoNero on 2009-10-05
I run a 64bit system. my question was how do i found out which things i've running that aren't (ex. java, codecs, etc..)

I think it's time for operating systems to make the step to 64bit, even Microsoft is gearing up to making the step (you only get the windows 7 certificate if your software is also 64bit-compatible, etc...)

---

### Post by Keyper7 on 2009-10-05
> **FrancoNero said:**
> I run a 64bit system. my question was how do i found out which things i've running that aren't (ex. java, codecs, etc..)

Well, have you tried what I suggested?

At least for repository packages, it probably works.

> **FrancoNero said:**
> I think it's time for operating systems to make the step to 64bit, even Microsoft is gearing up to making the step (you only get the windows 7 certificate if your software is also 64bit-compatible, etc...)

Operating systems have made this step a long time ago.

It's companies like Adobe and Skype that didn't.

---

### Post by zika on 2009-10-14
I'll mark this thread [SOLVED] even though I do not use at this moment the solution proposed since it is a bit old version in Ubuntu repositories and a very new one is available ... (speaking just about plug-in).

---

