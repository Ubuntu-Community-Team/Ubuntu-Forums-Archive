---
title: "Problem with gcc compiler with matlab"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by raphael-cardinaux on 2013-09-26
Hei guys,

I have intalled the ACADO toolkit. I am now trying to install the matlab interface.

My problem is the following : Matlab doesn't seem to find my gcc compiler.

I have installed gcc-4.4 as recommanded for my matlab version (R2013a --> [http://www.mathworks.ch/support/compilers/R2013a/index.html?sec=glnxa64](http://www.mathworks.ch/support/compilers/R2013a/index.html?sec=glnxa64) ), though I don't see my compiler when typing "mex -setup" in matlab...

Here is the steps to build the interface, and how it should work : [http://sourceforge.net/p/acado/wiki/MATLAB%20Interface%20-%20Getting%20Started/](http://sourceforge.net/p/acado/wiki/MATLAB%20Interface%20-%20Getting%20Started/)

And here is what i get on matlab :

>> mex -setup

    Options files control which compiler to use, the compiler and link command
    options, and the runtime libraries to link against.

    Using the 'mex -setup' command selects an options file that is
    placed in /home/raphael/.matlab/R2013a and used by default for 'mex'. An options 
    file in the current working directory or specified on the command line 
    overrides the default options file in /home/raphael/.matlab/R2013a.
 
    To override the default options file, use the 'mex -f' command
    (see 'mex -help' for more information).

The options files available for mex are:

  1: /usr/local/MATLAB/R2013a/bin/mexopts.sh : 
      Template Options file for building MEX-files
 

  0: Exit with no changes



I don't know if I should install my gcc in a special location... please help if you have an idea!

Thanks

Raphaël

---

### Post by raphael-cardinaux on 2013-09-26
It seems that matlab is only looking for my compiler in my matlab directory... how come?

---

### Post by Topsiho on 2013-09-26
I don't know whether you have a special reason for using Matlab.

There is an open source very good clone of Matlab, which is in the repositories of Ubuntu, and which is called Octave.
Any incompatibility of Octave with Matlab is called a bug, which you can report.

With the rest of your question I am afraid I can't help you, sorry for this :)

Topsiho

---

### Post by steeldriver on 2013-09-26
Maybe this will help?

[http://blogs.bu.edu/mhirsch/2013/07/matlab-r2013a-mex-on-ubuntu-13-04-64-bit/](http://blogs.bu.edu/mhirsch/2013/07/matlab-r2013a-mex-on-ubuntu-13-04-64-bit/)

It looks like R2013a is a bit different from earlier versions in that 'mex -setup' chooses a config file *containing* the compiler choice, rather than locating/choosing the compiler directly. If you press '1' it will copy /usr/local/MATLAB/R2013a/bin/mexopts.sh to $HOME/.matlab/R2013a and you can edit that to specify gcc-4.4 and g++-4.4 (you will probably need to install g**++**-4.4 for ACADO if you have not already done so)

---

### Post by raphael-cardinaux on 2013-09-26
to Topsiho : This toolkit doesn't work on Octave, that's why I m using matlab :S

to steeldriver : I followed the instruction that are given on your website but it doesn't change a think :( moreover my mexopts.sh was empty which seems strange.. thank you though

---

### Post by Topsiho on 2013-09-26
"to Topsiho : This toolkit doesn't work on Octave, that's why I m using matlab :S"

OK, sorry to read that, I only wanted to mention Octave to you :) .

Topsiho

---

### Post by steeldriver on 2013-09-26
The website I linked is not mine - it just seemed relevant

Is your /usr/local/MATLAB/R2013a/bin/mexopts.sh also empty? how did you install matlab? Maybe the mex component did not get setup correctly at install time?

---

### Post by raphael-cardinaux on 2013-09-26
ok sorry about that.

No this file isn't empty, but the file that open when I follow the instruction on the website your recommanded is empty. And I can't modify the /usr/local/MATLAB/R2013a/bin/mexopts.sh .

---

### Post by steeldriver on 2013-09-26
Well if the mex -setup failed for some reason, you could try copying the mexopts.sh file manually from /usr/local/MATLAB/R2013a/bin to your $HOME/.matlab/R2013a directory

---

### Post by raphael-cardinaux on 2013-09-26
Thanks man it worked! I ve spent so much time on this problem, thx a lot!

---

### Post by steeldriver on 2013-09-26
You're welcome - glad that worked for you. I haven't used mex for a couple of years and things appear to have changed a bit (the whole R2013a UI is quite a lot different as well).

---

