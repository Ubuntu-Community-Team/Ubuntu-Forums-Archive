---
title: "Batari emulator"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by SpitfireSMS on 2009-11-23
So for one of my classes we are making an atari game, using the Batari emulator.
I have the install files, it just wont work.

I tried cd'ing into the source dir and doing ./configure make make install, but it came back with errors and didnt install anything.

The instructions are located here:
[http://bataribasic.com/install.html](http://bataribasic.com/install.html)

Im not sure if thats for a (much) older ubuntu, but it doesnt help me at all.

Does anyone know how to install this emu properly?
Or alternatively, could somebody download and get it working and then let me know what you did?

---

### Post by prshah on 2009-11-23
> **SpitfireSMS said:**
> it came back with errors and didnt install anything.

Can you post the errors?

Maybe you need to install the basic building tools. Open a terminal and give the command```
sudo apt-get install build-essential
```

Maybe someone can offer more relevant help if the errors are posted.

---

### Post by SpitfireSMS on 2009-11-23
Looks to me like an its errors with the installation script provided by the website.

```
ste@ste-laptop:~/Desktop/batari/source$ sudo make
cc -O2 -o 2600basic 2600bas.c statements.c keywords.c
2600bas.c: In function &#8216;main&#8217;:
2600bas.c:109: error: too few arguments to function &#8216;getline&#8217;
statements.c: In function &#8216;create_includes&#8217;:
statements.c:826: warning: format not a string literal and no format arguments
statements.c:827: warning: format not a string literal and no format arguments
statements.c: In function &#8216;getline&#8217;:
statements.c:1131: error: number of arguments doesn&#8217;t match prototype
/usr/include/stdio.h:651: error: prototype declaration
statements.c: In function &#8216;let&#8217;:
statements.c:2761: warning: too few arguments for format
statements.c:2770: warning: too few arguments for format
make: *** [2600basic] Error 1

```


I didnt have the build essentials installed, but installing them didnt help =(

---

### Post by dddanmar on 2009-11-24
So I tried it using the following on 9.10:
 
$ wget [http://bataribasic.com/bB_Linux_binaries_version_1.0.zip](http://bataribasic.com/bB_Linux_binaries_version_1.0.zip)
$ wget [http://bataribasic.com/batari_Basic_version_1.0.zip](http://bataribasic.com/batari_Basic_version_1.0.zip)
$ unzip batari_Basic_version_1.0.zip
$ unzip bB_Linux_binaries_version_1.0.zip
$  export bB=`pwd` 
$   export PATH=$PATH:$bB
$./2600basic.sh  samples/zombie_chase.bas 

Starting build of samples/zombie_chase.bas
2600 Basic compilation complete.
DASM V2.20.09, Macro Assembler (C)1988-2003
      bytes of ROM space left
      65 bytes of ROM space left
      65 bytes of ROM space left
Complete.
Build complete.

$ stella samples/zombie_chase.bas.bin

Works, and a fun game too :)

The binaries seem to work OK.


---------------------------------

{edit} For building, the error is getline() exists as a function and is conflicting, but in the source directory, 

$ grep getline *
2600bas.c:    if (j>40) fprintf(stderr,"(%d) Warning: long line\n"[COLOR=Red],getline()[/COLOR]);
statements.c:[COLOR=Red]int[/COLOR] [COLOR=Red]getline()[/COLOR]

So.... let's just get rid of it because all its there for is a warning. Instead, it will just print out "Warning: long line\n". Sorry, it won't give you the line mentioned but eh... 

Remove in your favourite text editor
,getline()

from 2600bas.c (note the comma)

and 
int getline()
{
  return line;
}

from statements.c

$ make
cc -O2 -o 2600basic 2600bas.c statements.c keywords.c
2600bas.c: In function &#8216;main&#8217;:
2600bas.c:109: warning: too few arguments for format
statements.c: In function &#8216;create_includes&#8217;:
statements.c:826: warning: format not a string literal and no format arguments
statements.c:827: warning: format not a string literal and no format arguments
statements.c: In function &#8216;let1&#8217;:
statements.c:2757: warning: too few arguments for format
statements.c:2766: warning: too few arguments for format
lex -t<preprocess.lex>lex.yy.c
cc -O2 -o preprocess lex.yy.c
rm -f lex.yy.c
cc -O2 -o postprocess postprocess.c
lex -t<optimize.lex>lex.yy.c
cc -O2 -o optimize lex.yy.c
rm -f lex.yy.c

$ cp 2600basic ..
$ cp optimize ..
$ cp postprocess ..
$ cp preprocess ..
$ cp dasm ..
$ cd ..
$ ./2600basic.sh samples/zombie_chase.bas 
$ stella samples/zombie_chase.bas.bin 

Huzzah!

---

### Post by dddanmar on 2009-11-24
Actually, I've just read your post again and thought I'd make sure its clarified:

batari: the basic atari 2600 compiler
stella: the atari 2600 emulator

So, you are writing your code in a text editor, compiling it with batari and playing it with stella (or similar) emulator.

> , using the Batari emulator.

---

