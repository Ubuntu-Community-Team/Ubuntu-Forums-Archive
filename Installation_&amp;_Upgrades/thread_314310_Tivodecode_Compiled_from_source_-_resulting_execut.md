---
title: "Tivodecode: Compiled from source - resulting executable reports 'command not found'"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by robconscient on 2006-12-07
Hi all,

I downloaded and compiled [tivodecode]("http://tivodecode.sourceforge.net/"), but when I try to run the executable from the command line, I get the error 'command not found'.

I have:
[LIST]
[*]downloaded and installed 'build-essential'
[*]run 'make' to compile the program
[*]checked permissions
[/LIST]
and yet still I cannot get the tivodecode executable to run. 

Here is the output I get:

> me @UbuntuLaptop:~/tivodecode-0.1.3/objects.dir$ ls

getopt_long.o  hexlib.o    tivodecode    TuringFast.o
getopt.o       sha1.o      tivodecode.o  turing_stream.o
happyfile.o    stdin.TiVo  tivo-parse.o

me @UbuntuLaptop:~/tivodecode-0.1.3/objects.dir$ tivodecode

bash: tivodecode: command not found


In the README, it says to **first check the Makefile setting CC, CFLAGS and LDFLAGS as appropriate for your platform**. I have no idea what that means, but do wonder if that is part of my problem.

Any ideas? Thanks :)

BTW, I got it to work on my XP machine using the Win32 download, so I know it isn't *totally* user error :???:

---

### Post by wilderness wanderer on 2006-12-08
In order to run an executable from the current directory, you must specifically tell the shell to look there (put a ./ in front of the filename).  So, from the directory which contains the file you enter:

```
./tivodecode -m (your MAK) -o outputfile.mpg inputfile.tivo
```

I've just used the program and it works great.

---

### Post by lloyd_b on 2006-12-08
Typically, after you finish with the make, you can run "sudo make install", which will move the files from the compilation directory out into locations where the shell will find them by itself.

As for running in the current directory, the previous poster has it nailed - you have to specify "./tivodecode" rather than just "tivodecode".

FYI: CC, CFLAGS and LDFLAGS are values that tell the compiler how to handler certain parts of the compile.  If it's compiled cleanly, you don't need to worry about these.

Lloyd B.

---

### Post by robconscient on 2006-12-08
Added the ./ to the command and bingo, that did it!

So it was my user error after all. :p 

Thanks all.

Rob

---

