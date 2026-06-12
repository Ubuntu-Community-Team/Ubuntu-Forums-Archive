---
title: "error in &quot;making&quot; scientific software:: portability issue(??)"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by jaind on 2006-11-26
hello,

I am trying to install a scientific software written in 1988-1990 on my laptop running Ubuntu 6.10. I have gcc-2.95 and g++-2.95. 
The name of the package is "sparse"(if it helps!!).

However, when i do a "make" inside the software's directory(which is what the instructions tell) i get the following error:

gcc -c   -Dnotdef\
        spallocate.c -o spallocate.o
gcc: No input files
make: *** [spallocate.o] Error 1

However, I am able to sucessfully "make" the package on an old solaris machine which we have in our department. i dont think its a gcc issue. 

So its probably a portability issue. I might need to install some additional softwares but am lost on this!! Can anyone suggest something??

Thanks!!

---

### Post by taurus on 2006-11-26
Didn't you post the same error message not that long ago (couple of hours)???  Please don't double post and if you have to, wait for 24 hours and bump your thread instead of creating a new one!!!  

What's the output of this command in the directory where the source is?

```
ls -la
```

---

### Post by jaind on 2006-11-26
I apologize for the double post. I earlier posted on the "general help" support category and then realized there was a "installation & Upgrades catgory" also...and then i didnt know how to delete the earlier post...:-? 

the output of "ls -la" is:
---------------------------------------------------------
total 416
drwxr-xr-x  4 divyanshu divyanshu   4096 2006-11-17 20:07 .
drwxr-xr-x 13 divyanshu divyanshu   4096 2006-11-26 15:33 ..
drwxr-xr-x  2 divyanshu divyanshu   4096 2006-11-17 20:07 CVS
-rwxr-xr-x  1 divyanshu divyanshu   1091 2003-12-02 00:53 Makefile
-rwxr-xr-x  1 divyanshu divyanshu  22173 2003-12-02 00:53 spallocate.c
-rwxr-xr-x  1 divyanshu divyanshu  32339 2003-12-02 00:53 spbuild.c
-rwxr-xr-x  1 divyanshu divyanshu  21992 2003-12-02 00:53 spconfig.h
-rwxr-xr-x  1 divyanshu divyanshu  33055 2003-12-02 00:53 spdefs.h
-rwxr-xr-x  1 divyanshu divyanshu 102041 2003-12-02 00:53 spfactor.c
-rwxr-xr-x  1 divyanshu divyanshu  12622 2003-12-02 00:53 spmatrix.h
-rwxr-xr-x  1 divyanshu divyanshu  23434 2003-12-02 00:53 spoutput.c
-rwxr-xr-x  1 divyanshu divyanshu  22848 2003-12-02 00:53 spsolve.c
-rwxr-xr-x  1 divyanshu divyanshu  39721 2003-12-02 00:53 sptest.c
-rwxr-xr-x  1 divyanshu divyanshu  68291 2003-12-02 00:53 sputils.c
drwxr-xr-x  3 divyanshu divyanshu   4096 2006-11-17 20:07 util
--------------------------------------------------------------

---

### Post by taurus on 2006-11-26
If you need to move a thread from one area to another, just PM one of the staffers and he/she will be more than happy to move it for you.

Now back to your problem.  Looks like there is a Makefile so what happens if you run the make command at the prompt?

```
make
```

---

### Post by jaind on 2006-11-26
when i run "make" i get as output:
-------------------------------------
gcc -c   -Dnotdef\
        spallocate.c -o spallocate.o
gcc: No input files
make: *** [spallocate.o] Error 1
----------------------------------------

--however if i run the same "make" command on an old solaris machine i have in my department, the package runs and the (correct) output is:
-------------------------------------------
gcc -c   -Dnotdef\
spallocate.c -o spallocate.o
gcc -c   -Dnotdef\
spbuild.c -o spbuild.o
gcc -c   -Dnotdef\
spoutput.c -o spoutput.o
gcc -c   -Dnotdef\
spsolve.c -o spsolve.o
gcc -c   -Dnotdef\
sputils.c -o sputils.o
gcc -c   -Dnotdef\
spfactor.c -o spfactor.o
rm -f ./libsparse.a
ar cr ./libsparse.a spallocate.o spbuild.o spoutput.o spsolve.o sputils.o spfactor.o
---------------------------------------------------

--but i want to be able to install it on my laptop. i have gcc-2.95.4 on my laptop and the solaris machine has gcc-2.95.3. I dont think it a gcc issue.

Thanks again!!

---

### Post by taurus on 2006-11-26
I'm afraid I may have to look at your Makefile!!!  :-|

---

### Post by jaind on 2006-11-27
Hey,

One of my profs was able to solve my problem. it was a portability issue in the makefile. It seems the definition of the symbol '\' was somehow different. 

Thank you very much for your help! :D ;)

---

### Post by taurus on 2006-11-27
I figured something like that; that's why I asked to see your Makefile!  ;)

---

