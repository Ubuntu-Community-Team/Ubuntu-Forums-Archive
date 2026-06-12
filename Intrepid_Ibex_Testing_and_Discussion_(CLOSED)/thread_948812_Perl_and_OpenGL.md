---
title: "Perl and OpenGL"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by d34dh0r53 on 2008-10-15
I'm trying to get opengl libs to work with perl and I'm running into a couple of problems.  Using the test script from [here]("http://graphcomp.com/opengl/test.txt") I get the following error with the libopengl-perl package:

```
Can't locate auto/OpenGL/glGenBuffer.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at pogl-test.pl line 262
```

When I try to build the OpenGL module from CPAN I get the following:

```
# make && make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" test.pl
Can't load 'blib/arch/auto/OpenGL/OpenGL.so' for module OpenGL: /usr/lib/xorg/modules/extensions/libglx.so: undefined symbol: GetTimeInMillis at /usr/lib/perl/5.10/DynaLoader.pm line 196.
 at test.pl line 9
Compilation failed in require at test.pl line 9.
BEGIN failed--compilation aborted at test.pl line 9.
make: *** [test_dynamic] Error 2
```

libglx.so is a symlink to libglx.so.177.80 which I assume comes from the nvidia-glx package.

TIA

---

### Post by Naddiseo on 2008-10-15
Is there a -dev package you need to install?

---

### Post by d34dh0r53 on 2008-10-15
I just tried installing nvidia-glx-177-dev and still no love.

---

