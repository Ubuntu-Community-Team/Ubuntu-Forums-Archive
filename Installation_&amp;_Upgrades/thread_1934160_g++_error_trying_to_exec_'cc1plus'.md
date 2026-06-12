---
title: "g++: error trying to exec 'cc1plus'"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by kakila on 2012-03-01
Hi,
I am using Ubuntu 11.10 64-bit Desktop

I searched for this problem everywhere. The solution that is mostly given is to resintall build-essential or the compilers. This doesn't work for me, listen to my story.

I installed build-essential and all the dependencies of Octave 3.6.1.
I run ./configure and make and everything went well.
Now I wanted to install but using checkinstall
So I installed checkinstall
everything went well Octave is running

Now, I start doing my usual installs.. among them I did the ubuntu-restricted-extras

After this and that I tried to recompile Octave to check the time it took. whenI try to make I get the error
gcc: error trying to exec 'cc1': execvp: No such file or directory
and 
g++: error trying to exec 'cc1plus': execvp: No such file or directory

I tried all reinstallation, purges and removals I could find. nothing solves the problem.

I noticed the following
```
gcc -print-search-dirs
```
returns
> programs: =/usr/lib/gcc/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/bin/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/bin/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/bin/
libraries: =/usr/lib/gcc/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/lib/x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/lib/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../x86_64-linux-gnu/4.6.1/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/:/lib/x86_64-linux-gnu/4.6.1/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/4.6.1/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../x86_64-linux-gnu/lib/:/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../:/lib/:/usr/lib/


```
ls /usr/lib/gcc/x86_64-linux-gnu/
```
gives
> 4.6  4.6.1

And here comes the curious part. Inside 4.6 there are all the needed programs
> cc1          crtendS.o      libgcc.a      liblto_plugin.so        libstdc++.so
cc1plus      crtfastmath.o  libgcc_eh.a   liblto_plugin.so.0      libsupc++.a
collect2     crtprec32.o    libgcc_s.so   liblto_plugin.so.0.0.0  lto1
crtbegin.o   crtprec64.o    libgcov.a     libquadmath.a           lto-wrapper
crtbeginS.o  crtprec80.o    libgomp.a     libquadmath.so
crtbeginT.o  include        libgomp.so    libssp_nonshared.a
crtend.o     include-fixed  libgomp.spec  libstdc++.a

While inside 4.6.1 only
> collect2  crtbeginS.o  crtendS.o  liblto_plugin.so  lto-wrapper

[COLOR="DarkRed"]How can I solve my problem?[/COLOR] 
What caused this problem? 
Why are this folders not removed when I uninstall gcc g++ gfortran and build-essential?

Thank you very much for your help!

---

