---
title: "Can't &quot;make&quot; Wine"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Ryupower on 2006-12-06
hey there, I tried configuring and installing wine from source ( need to use a special patch ) but whenever I type in "make" at the end I get:

[I]> ppl.l:234: error: syntax error before ‘YYSTYPE’
ppl.l: In function ‘ppy_lex’:
ppl.l:316: error: ‘tINCLUDE’ undeclared (first use in this function)
ppl.l:316: error: (Each undeclared identifier is reported only once
ppl.l:316: error: for each function it appears in.)
ppl.l:318: error: ‘tERROR’ undeclared (first use in this function)
ppl.l:319: error: ‘tWARNING’ undeclared (first use in this function)
ppl.l:320: error: ‘tPRAGMA’ undeclared (first use in this function)
ppl.l:321: error: ‘tPPIDENT’ undeclared (first use in this function)
ppl.l:322: error: ‘tUNDEF’ undeclared (first use in this function)
ppl.l:323: error: ‘tIFDEF’ undeclared (first use in this function)
ppl.l:324: error: ‘tIFNDEF’ undeclared (first use in this function)
ppl.l:325: error: ‘tIF’ undeclared (first use in this function)
ppl.l:326: error: ‘tELIF’ undeclared (first use in this function)
ppl.l:327: error: ‘tELSE’ undeclared (first use in this function)
ppl.l:328: error: ‘tENDIF’ undeclared (first use in this function)
ppl.l:329: error: ‘tLINE’ undeclared (first use in this function)
ppl.l:330: error: ‘tGCCLINE’ undeclared (first use in this function)
ppl.l:332: error: ‘tNL’ undeclared (first use in this function)
ppl.l:340: error: ‘ppy_lval’ undeclared (first use in this function)
ppl.l:368: error: ‘tDEFINED’ undeclared (first use in this function)
ppl.l:369: error: ‘tLSHIFT’ undeclared (first use in this function)
ppl.l:370: error: ‘tRSHIFT’ undeclared (first use in this function)
ppl.l:371: error: ‘tLOGAND’ undeclared (first use in this function)
ppl.l:372: error: ‘tLOGOR’ undeclared (first use in this function)
ppl.l:373: error: ‘tEQ’ undeclared (first use in this function)
ppl.l:374: error: ‘tNE’ undeclared (first use in this function)
ppl.l:375: error: ‘tLTE’ undeclared (first use in this function)
ppl.l:376: error: ‘tGTE’ undeclared (first use in this function)
ppl.l:389: error: ‘tIDENT’ undeclared (first use in this function)
ppl.l:420: error: ‘tLITERAL’ undeclared (first use in this function)
ppl.l:429: error: ‘tMACRO’ undeclared (first use in this function)
ppl.l:430: error: ‘tDEFINE’ undeclared (first use in this function)
ppl.l:449: error: ‘tMACROEND’ undeclared (first use in this function)
ppl.l:453: error: ‘tELIPSIS’ undeclared (first use in this function)
ppl.l:462: error: ‘tCONCAT’ undeclared (first use in this function)
ppl.l:463: error: ‘tSTRINGIZE’ undeclared (first use in this function)
ppl.l:559: error: ‘tDQSTRING’ undeclared (first use in this function)
ppl.l:579: error: ‘tSQSTRING’ undeclared (first use in this function)
ppl.l:589: error: ‘tIQSTRING’ undeclared (first use in this function)
ppl.l:641: error: ‘tRCINCLUDE’ undeclared (first use in this function)
ppl.l:686: error: ‘tRCINCLUDEPATH’ undeclared (first use in this function)
ppl.l: At top level:
ppl.l:789: error: syntax error before ‘YYSTYPE’
ppl.l: In function ‘make_number’:
ppl.l:797: error: ‘str’ undeclared (first use in this function)
ppl.l:797: error: ‘len’ undeclared (first use in this function)
ppl.l:832: error: ‘val’ undeclared (first use in this function)
ppl.l:832: error: ‘radix’ undeclared (first use in this function)
ppl.l:833: error: ‘tULONGLONG’ undeclared (first use in this function)
ppl.l:838: error: ‘tSLONGLONG’ undeclared (first use in this function)
ppl.l:847: error: ‘tULONG’ undeclared (first use in this function)
ppl.l:852: error: ‘tSLONG’ undeclared (first use in this function)
ppl.l:857: error: ‘tUINT’ undeclared (first use in this function)
ppl.l:862: error: ‘tSINT’ undeclared (first use in this function)
make[2]: *** [ppl.yy.o] Error 1
make[2]: Leaving directory `/home/claudia/wine-0.9.26/libs/wpp'
make[1]: *** [wpp] Error 2
make[1]: Leaving directory `/home/claudia/wine-0.9.26/libs'
make: *** [libs] Error 2[/I]

I tried " make clean" and " make clean dist" after configuring it as well as after "making" ( *make depend && make*; or trying one after the other ), but it still gives me all these errors....HELP!

---

### Post by Henry Rayker on 2006-12-06
do you have build-essential installed?

I know there has been a discussion and that discussion ended retardedly, so I just don't know why they don't install that by default.

---

### Post by Ryupower on 2006-12-06
No I don't! Thanks! 
But what does build essential do? It talks about debian packages, but I'm trying to install from source....does it turn it into a .deb package? Must I use a special command?

---

### Post by Henry Rayker on 2006-12-06
build-essential is required to compile packages from source. It contains the make package, the c compiler and the c++ compiler, as well as other things. From what I have learned, if you EVER want to install something by building it using the "make" command, you probably need this package.

No special command is needed. This will just enable the make command to function properly.

I have to warn you, though, supposedly this isn't installed by default because of a security risk whereby, if someone gains access of your system, they will be able to compile code (if they gain access to your system, they can just install the package, though, right? :D ).......but the security concerns seem pretty foolish (and I install this package on every installation I do, because I have to install from source)...

---

### Post by Ryupower on 2006-12-06
I tried it! and it still doesn't work! :(

---

### Post by Henry Rayker on 2006-12-06
Same errors or new ones?

An alternative you could take is using Automatix2 to install Wine.

---

### Post by Ryupower on 2006-12-06
> **Henry Rayker said:**
> Same errors or new ones?

An alternative you could take is using Automatix2 to install Wine.


The same ones.
I have no clue what automatix does, does it install from source ( I really need a special file for this that can only be found in the source packages )
Also, I tried a different version of wine: it still gives me the same errors!

---

### Post by Henry Rayker on 2006-12-06
Well, automatix will install wine, but I don't believe it will be from source. I'm fairly certain it will install a .deb from someplace.

My resourcefulness in this area has dried up, and I have no more suggestions. Hopefully someone smarter than I will come and chime in.

---

### Post by claydoh on 2006-12-06
The latest wine directly from [winehq]("http://www.winehq.com/") can be very easily installed via Synaptic by [adding their repository]("http://www.winehq.com/site/download-deb") to your sources.list. Much much simpler than compiling, which can take a very long time, depending on your system.

But if you wish to do so, wine is normally built a little differently from most linux applications. If you look in the wine source directory, you will see a [README]("http://source.winehq.org/source/README") with instructions on how to compile wine from source. You will also need to install other dependencies besides build-essential in order to build this. the easiest way is to have apt install all the build dependencies like this:
```
sudo apt-get build-dep wine
```then in the top source directory you just need to type:
```
./tools/wineinstall
```

---

### Post by Ryupower on 2006-12-06
> **claydoh said:**
> The latest wine directly from [winehq]("http://www.winehq.com/") can be very easily installed via Synaptic by [adding their repository]("http://www.winehq.com/site/download-deb") to your sources.list. Much much simpler than compiling, which can take a very long time, depending on your system.

But if you wish to do so, wine is normally built a little differently from most linux applications. If you look in the wine source directory, you will see a [README]("http://source.winehq.org/source/README") with instructions on how to compile wine from source. You will also need to install other dependencies besides build-essential in order to build this. the easiest way is to have apt install all the build dependencies like this:
```
sudo apt-get build-dep wine
```then in the top source directory you just need to type:
```
./tools/wineinstall
```

I just tried the ./tools/wineinstall.
And it STILL gives me:

make[2]: Entering directory `/home/claudia/Desktop/Programs/wine-0.9.24/libs/wpp'
bison  -p ppy_ -o ppy.tab.c -d ppy.y
ppy.y:138 parser name defined to default :"parse"
bison  -p ppy_ -o ppy.tab.c ppy.y
ppy.y:138 parser name defined to default :"parse"
gcc -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o ppy.tab.o ppy.tab.c
gcc -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o ppl.yy.o ppl.yy.c
ppl.l:167:21: error: ppy.tab.h: No such file or directory
ppl.l:234: error: syntax error before &#8216;YYSTYPE&#8217;
ppl.l: In function &#8216;ppy_lex&#8217;:
ppl.l:316: error: &#8216;tINCLUDE&#8217; undeclared (first use in this function)
ppl.l:316: error: (Each undeclared identifier is reported only once
ppl.l:316: error: for each function it appears in.)
ppl.l:318: error: &#8216;tERROR&#8217; undeclared (first use in this function)
ppl.l:319: error: &#8216;tWARNING&#8217; undeclared (first use in this function)
ppl.l:320: error: &#8216;tPRAGMA&#8217; undeclared (first use in this function)
ppl.l:321: error: &#8216;tPPIDENT&#8217; undeclared (first use in this function)
ppl.l:322: error: &#8216;tUNDEF&#8217; undeclared (first use in this function)
ppl.l:323: error: &#8216;tIFDEF&#8217; undeclared (first use in this function)
ppl.l:324: error: &#8216;tIFNDEF&#8217; undeclared (first use in this function)
ppl.l:325: error: &#8216;tIF&#8217; undeclared (first use in this function)
ppl.l:326: error: &#8216;tELIF&#8217; undeclared (first use in this function)
ppl.l:327: error: &#8216;tELSE&#8217; undeclared (first use in this function)
ppl.l:328: error: &#8216;tENDIF&#8217; undeclared (first use in this function)
ppl.l:329: error: &#8216;tLINE&#8217; undeclared (first use in this function)
ppl.l:330: error: &#8216;tGCCLINE&#8217; undeclared (first use in this function)
ppl.l:332: error: &#8216;tNL&#8217; undeclared (first use in this function)
ppl.l:340: error: &#8216;ppy_lval&#8217; undeclared (first use in this function)
ppl.l:368: error: &#8216;tDEFINED&#8217; undeclared (first use in this function)
ppl.l:369: error: &#8216;tLSHIFT&#8217; undeclared (first use in this function)
ppl.l:370: error: &#8216;tRSHIFT&#8217; undeclared (first use in this function)
ppl.l:371: error: &#8216;tLOGAND&#8217; undeclared (first use in this function)
ppl.l:372: error: &#8216;tLOGOR&#8217; undeclared (first use in this function)
ppl.l:373: error: &#8216;tEQ&#8217; undeclared (first use in this function)
ppl.l:374: error: &#8216;tNE&#8217; undeclared (first use in this function)
ppl.l:375: error: &#8216;tLTE&#8217; undeclared (first use in this function)
ppl.l:376: error: &#8216;tGTE&#8217; undeclared (first use in this function)
ppl.l:389: error: &#8216;tIDENT&#8217; undeclared (first use in this function)
ppl.l:420: error: &#8216;tLITERAL&#8217; undeclared (first use in this function)
ppl.l:429: error: &#8216;tMACRO&#8217; undeclared (first use in this function)
ppl.l:430: error: &#8216;tDEFINE&#8217; undeclared (first use in this function)
ppl.l:449: error: &#8216;tMACROEND&#8217; undeclared (first use in this function)
ppl.l:453: error: &#8216;tELIPSIS&#8217; undeclared (first use in this function)
ppl.l:462: error: &#8216;tCONCAT&#8217; undeclared (first use in this function)
ppl.l:463: error: &#8216;tSTRINGIZE&#8217; undeclared (first use in this function)
ppl.l:559: error: &#8216;tDQSTRING&#8217; undeclared (first use in this function)
ppl.l:579: error: &#8216;tSQSTRING&#8217; undeclared (first use in this function)
ppl.l:589: error: &#8216;tIQSTRING&#8217; undeclared (first use in this function)
ppl.l:641: error: &#8216;tRCINCLUDE&#8217; undeclared (first use in this function)
ppl.l:686: error: &#8216;tRCINCLUDEPATH&#8217; undeclared (first use in this function)
ppl.l: At top level:
ppl.l:789: error: syntax error before &#8216;YYSTYPE&#8217;
ppl.l: In function &#8216;make_number&#8217;:
ppl.l:797: error: &#8216;str&#8217; undeclared (first use in this function)
ppl.l:797: error: &#8216;len&#8217; undeclared (first use in this function)
ppl.l:832: error: &#8216;val&#8217; undeclared (first use in this function)
ppl.l:832: error: &#8216;radix&#8217; undeclared (first use in this function)
ppl.l:833: error: &#8216;tULONGLONG&#8217; undeclared (first use in this function)
ppl.l:838: error: &#8216;tSLONGLONG&#8217; undeclared (first use in this function)
ppl.l:847: error: &#8216;tULONG&#8217; undeclared (first use in this function)
ppl.l:852: error: &#8216;tSLONG&#8217; undeclared (first use in this function)
ppl.l:857: error: &#8216;tUINT&#8217; undeclared (first use in this function)
ppl.l:862: error: &#8216;tSINT&#8217; undeclared (first use in this function)
make[2]: *** [ppl.yy.o] Error 1
make[2]: Leaving directory `/home/claudia/Desktop/Programs/wine-0.9.24/libs/wpp'make[1]: *** [wpp] Error 2
make[1]: Leaving directory `/home/claudia/Desktop/Programs/wine-0.9.24/libs'
make: *** [libs] Error 2


I can't use that version you get from the repositories. I need to delete a line in shell_main.c, otherwise the program will keep on crashing ( right after installing ). After deleting that line I need to recompile it.

why is it giving me this?

---

### Post by claydoh on 2006-12-06
I cannot find a solution for this 
Why exactly do you need to patch wine, and where did you find what you needed to edit/patch?

Also, have you tried some of the slightly older wine versions, say 0.9.18 or so and up? from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Ryupower on 2006-12-07
> **claydoh said:**
> I cannot find a solution for this 
Why exactly do you need to patch wine, and where did you find what you needed to edit/patch?

Also, have you tried some of the slightly older wine versions, say 0.9.18 or so and up? from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

This is why I need it:
[http://bugs.winehq.org/show_bug.cgi?id=6078](http://bugs.winehq.org/show_bug.cgi?id=6078)

I can't find that file in .deb packages. :(
and you need to "recompile" it afterwards

---

### Post by Revery on 2007-11-19
Too late to help you I bet, but not other googlers!  I had the same problems you were decribing.  When it told me I needed bison I went to the package manager and saw that I had it already, so I installed bison++.  It went past that error message and got to the errors described here.
To solve this I re-installed regular bison (which uninstalled bison++) but I also installed bison-1.3.5, which you can apparently install in parallel with the regular bison package, and it fixed it for me.

---

