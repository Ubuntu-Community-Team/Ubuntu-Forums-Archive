---
title: "Change compiler for a single shell"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by venturax on 2010-02-11
Hi,

I have upgraded my machine to Karmic, and thereby getting gcc/g++ 4.4 in the process. I have some code that requires gcc/g++ 4.3.

I can change the compiler system wide by redirecting the symbolic link from 4.4 to 4.3
```
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc
``` but i would like to have it done per session instead.

Any ideas?

---

### Post by stumbleUpon on 2010-02-11
In the terminal do

```
 alias gcc='/usr/bin/gcc-4.3' 
```

This survives only as long as you have that terminal session open. It does not work in a new tab or a new terminal window

Does this help...?

---

### Post by gmargo on 2010-02-11
Use the CC environment variable and write your makefiles correctly to use CC instead of a hardcoded gcc.

---

### Post by venturax on 2010-02-11
> **gmargo said:**
> Use the CC environment variable and write your makefiles correctly to use CC instead of a hardcoded gcc.
The makefile is already given, since its google's android :-) its the donut release i try to build on karmic

@stumbleUpon: I'll try it asap

---

### Post by stumbleUpon on 2010-02-11
If its a makefile then it might be better to change the CC environment variable as gmargo mentioned

In the terminal you can do

alias CC='/usr/bin/gcc-4.3'

or change the CC variable in the Makefile

---

### Post by gmargo on 2010-02-11
> **stumbleUpon said:**
> alias CC='/usr/bin/gcc-4.3'

I think you meant
```

export CC='/usr/bin/gcc-4.3'

```

---

### Post by venturax on 2010-02-11
> **gmargo said:**
> I think you meant
```

export CC='/usr/bin/gcc-4.3'

```
a dumb question is if there is a variable for g++ as well?

---

### Post by stumbleUpon on 2010-02-11
> **gmargo said:**
> I think you meant
```

export CC='/usr/bin/gcc-4.3'

```

No, i meant alias in the terminal

If you do export, you would have to use $CC and not CC to get /usr/bin/gcc-4.3

In the Makefile, of course it would be export as you say

---

### Post by venturax on 2010-02-11
Neither of the solutions work. It seems there's more to it, than just using an alias. I think its because the various makefiles scattered throughout the project is calling the compilers themselves, causing it not to work. I'm not sure. I can just see the problem is still there. If i change the link system wide it works fine..
I'm out of ideas at this point, besides making a seperate directory with links to the correct compiler and then inserting this into my $PATH, but its just a guess :-(

---

### Post by gmargo on 2010-02-11
> **venturax said:**
> ... variable for g++ as well?

"CXX" is the standard C++ compiler variable, set to g++ by default.  "CXXFLAGS" for options.

You can see make's built-in rules and variables with "make -p".

---

### Post by gmargo on 2010-02-11
> **venturax said:**
> The makefile is already given, since its **google's android** :-) its the donut release i try to build on karmic

Exactly what source code are you trying to compile?  Is it the 2.1GB source code from [http://source.android.com/download]("http://source.android.com/download?")

---

### Post by gmargo on 2010-02-11
> **venturax said:**
> 
I'm out of ideas at this point, besides making a seperate directory with links to the correct compiler and then inserting this into my $PATH, but its just a guess :-(

That's a good idea, but try this first: with your CC environment variable, run "make -e" so that make gives environment variables precedence over variables from makefiles.

---

### Post by venturax on 2010-02-12
> **gmargo said:**
> Exactly what source code are you trying to compile?  Is it the 2.1GB source code from [http://source.android.com/download]("http://source.android.com/download?")

Its the Android Donut release I try to compile in Ubuntu 9.10. As of now I have just changed the two CPP files, which caused the error. Cupcake and Eclair releases work fine with gcc/g++ 4.4, but the Donut release fail.

Many ways can circumvent the error, but I lack a simple and session based solution to change gcc/g++ from 4.4 to 4.3 :-)

Thanks for all your help so far!!

---

