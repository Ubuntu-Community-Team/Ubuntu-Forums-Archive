---
title: "Problem with MATLAB mex files with Ubuntu 11.04"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by doctor max on 2011-05-02
Hi everybody.

I just upgraded to Ubuntu 11.04 and I have a problem with a MATLAB mex file: I receive this error

```
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl.so.7)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl.so.7)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libgmpxx.so.4)

```With 10.10, it worked perfectly. I tried to reinstall MATLAB without success. What could the problem be and how can I resolve it?

Thank u :-)

Bye

---

### Post by lechien73 on 2011-05-02
Hi and welcome to the forums!

This thread might help you. It's due to the fact that MATLAB appears to change the path to the GLIBC libraries:

[http://uri.tl/2a](http://uri.tl/2a)

Probably due to a newer version of GCC in 11.04

---

### Post by xandey on 2011-05-06
Matlab is picky about which compiler you use:

[http://www.mathworks.com/support/compilers/R2011a/glnxa64.html](http://www.mathworks.com/support/compilers/R2011a/glnxa64.html)
(you can change the version in the address bar)

I find that I have to get the right gcc 4.3 or 4.2.

Natty dropped support for 4.3, so you probably need to compile 4.3 from source. I wasn't able to find any binary package for this or a howto. If anyone knows I'd love to avoid compiling gcc just for matlab.

---

### Post by PrinceXV on 2011-05-11
Please excuse the selfless self promotion, but I think I covered what you're looking for in my [blog]("http://morganbye.net/blog/2011/05/matlab-ubuntu-1104").

Basically, Ubuntu in the update seemingly updates your libraries but doesnt completely remove them. Creating a link back to them seems to keep MATLAB happy

---

### Post by xandey on 2011-05-11
So I can't speak for the OP, but I did see your blog and it allowed me to run Matlab, but it does nothing for me to do with compiling mex files.

---

### Post by PrinceXV on 2011-05-17
I dont personally know about MEX files, but I imagine they use libraries just like everything else in MATLAB. Since, the Ubuntu 11 upgrade I've been having massive problems with some of my applications that previously had no problems.

I've done another [blog post]("http://morganbye.net/blog/2011/05/ubuntu-1104-and-matlab-x64-c-c-and-fortran-libraries") about it. But it basically boiled down to MATLAB trying to use 32 bit libraries when Ubuntu (by default) gives you x64 and installing 32 bit (if you're not careful) replaces the 64 bit libraries.

And of course the 64 ones dont work with 32 code. And the 32 doesnt want to work without the 64 present...

---

### Post by dog.bytes on 2011-05-19
Hello Ubuntu MATLAB users.

I too observed the issue below, and I was able to reproduce it with several versions of MATLAB under Ubuntu 11.04. I have a workaround that does not require more than editing a file in your home directory:
[LIST]
[*]Run 'mex -setup' at the command line in either bash or MATLAB and select either option
[*]Edit the file ~/.matlab/mexopts.sh using your favorite text editor and change each instance of gcc to gcc-4.4; each instance of g++ to g++-4.4; each instance of gfortran to gfortran-4.4
[*]Install gcc-4.4, g++-4.4, and gfortran-4.4
[/LIST]
Note that the gcc in Ubuntu 10.10 which worked was version 4.4.x, so this approach seems to work. I also tried installing gcc-4.3 and did not get MEX files to compile without error, so this method was most effective.

I posted a slightly more detailed version on [my new blog]("http://blog.syrus.us/2011/05/compiling-mex-files-on-ubuntu-1104.html").


> **doctor max said:**
> Hi everybody.

I just upgraded to Ubuntu 11.04 and I have a problem with a MATLAB mex file: I receive this error

```
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl.so.7)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl.so.7)
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/cc1: /usr/local/MATLAB/R2010b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libgmpxx.so.4)

```With 10.10, it worked perfectly. I tried to reinstall MATLAB without success. What could the problem be and how can I resolve it?

Thank u :-)

Bye

---

### Post by stuck_tom on 2011-05-20
I don't mean to hijack the thread, but I'm also having a problem mexing with Ubuntu 11.04 and was wondering if this is related or is a new problem. I am using Matlab 2008a and gfortran/gcc 4.4 (I receive a warning that this isn't officially supported by Matlab, but I don't think that is the cause of the message). I receive the following when I try to mex a file:

```
as: /usr/local/Matlab/R2008a/bin/glnxa64/libz.so.1: no version information available (required by /usr/lib/libbfd-2.21.0-system.20110327.so)
/usr/bin/ld: /usr/local/Matlab/R2008a/bin/glnxa64/libz.so.1: no version information available (required by /usr/lib/libbfd-2.21.0-system.20110327.so)
```

Thank you!

---

### Post by dog.bytes on 2011-05-20
Were you able to do everything in Ubuntu 10.10? If so, the issue might well be related.

---

### Post by stuck_tom on 2011-05-23
> **dog.bytes said:**
> Were you able to do everything in Ubuntu 10.10? If so, the issue might well be related.

Yes, sorry I should've said that. I have been able to mex things no problem with this version of Matlab with the last 4 releases of Ubuntu (9.04-10.10).

---

### Post by cparmer on 2011-07-19
I updated the mexopts.sh file, and I was able to compile my file. However, I'm still getting an error with the .mexa64 file: 
```
??? Invalid MEX-file '/home/cparmer/VarietyPack/Programming/Lessons/Mex/
.mexa64':

/home/cparmer/MATLAB/R2011a/bin/glnxa64/../../sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by
/home/cparmer/VarietyPack/Programming/Lessons/Mex/import_matrix.mexa64)
```

ideas?

---

### Post by mohammadul on 2011-09-18
$ cd matlab/sys/os/glnx86

$ sudo mv libgcc_s.so.1 libgcc_s.so.1.back
$ sudo ln -s /lib/libgcc_s.so.1 libgcc_s.so.1
$ sudo rm libstdc++.so.6 (this was already a symbolic link)
$ sudo ln -s /usr/lib/libstdc++.so.6.0.9 libstdc++.so.6

version numbers may differ

---

### Post by nguyentp on 2011-11-06
Hello,
I have a similar problem with mex in ubuntu 11.4, Matlab 2009a. I have changed mexopts.sh file, and replaced g++ by g++-4.2, gcc by gcc-4.2. The warning about gcc compiler doesn't appear, but there is still error message as follows when I tried to compiled:
>> make
DT.c:27:1: warning: "INFINITY" redefined
In file included from /usr/include/math.h:40,
                 from DT.c:24:
/usr/include/bits/inf.h:27:1: warning: this is the location of the previous definition
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

    mex: link of ' "DT.mexglx"' failed.

Any one can show me how to fix this error? Thanks.

---

### Post by trendymoniker on 2012-07-01
mohammadul, your solution works.

---

