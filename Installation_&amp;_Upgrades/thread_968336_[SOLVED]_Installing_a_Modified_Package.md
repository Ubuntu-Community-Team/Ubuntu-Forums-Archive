---
title: "[SOLVED] Installing a Modified Package"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by NewWorld on 2008-11-02
Hi I'm trying to install a modified version of the 'pdftohtml' utility found in the 'poppler' package, which as the name suggests converts PDF files into the HTML format.

The modified version I am trying to install is found [**_here_**]("http://minnie.tuhs.org/Programs/Pdftohtml/index.html"), and is differenet from the original utility packaged with poppler, because it outputs to HTML files optimised for eBook reading on the PDA.

I tried overwriting the original pdftohtml util with the common './configure', 'make', 'make install' commands, but it wouldn't work. Untarred the [**_.tar.gz_**]("http://minnie.tuhs.org/Programs/Pdftohtml/wkt_pdftohtml-20081008.tar.gz"). Changed directory to the program folder, and had a go at installing the program.

NOTE: If it's any help, the 'Makefile' file contains the 'Compile flags' for installing...

```
**danb@danb-laptop:~/**Documents/wkt_pdftohtml$ dir
config.h      HtmlFonts.h   HtmlOutputDev.cc  parseargs.c  pdftohtml.cc
DCTStream.h   HtmlLinks.cc  HtmlOutputDev.h   parseargs.h  pdftozip
HtmlFonts.cc  HtmlLinks.h   Makefile          pdftohtml.1
**danb@danb-laptop:~**/Documents/wkt_pdftohtml$ ./configure
bash: ./configure: No such file or directory
**danb@danb-laptop:~**/Documents/wkt_pdftohtml$ sudo ./Makefile
[sudo] password for danb:
sudo: ./Makefile: command not found
**danb@danb-laptop:~**/Documents/wkt_pdftohtml$ make
g++ -O2 -Wall -I. -I/usr/include/poppler   -c -o pdftohtml.o pdftohtml.cc
make: g++: Command not found
make: *** [pdftohtml.o] Error 127
**danb@danb-laptop:~**/Documents/wkt_pdftohtml$ make install
make: *** No rule to make target `install'. Stop.
**danb@danb-laptop:~**/Documents/wkt_pdftohtml$
```

As you can see I totally failed, can anyone help me install this?

Btw, at the bottom of the program's homepage it says:

> The changes to the main poppler tree have been returned as diffs to the maintainers of poppler. So, use this version until the changes get absorbed back into the main poppler tree. 

Does anyone know what this means?


Thanks all for reading this :)

---

### Post by Partyboi2 on 2008-11-02
It looks like you don't have to run ./configure, so just run make, but it also looks like you haven't got g++ installed, so try
```
sudo apt-get install build-essential
``` then run make again.

---

### Post by chrisdeckard on 2008-11-02
Read this for general info on compiling a package.  Since Ubuntu is somewhat Debian-ish, this will still apply.

[http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)

-Chris

---

### Post by NewWorld on 2008-11-04
> **Partyboi2 said:**
> It looks like you don't have to run ./configure, so just run make, but it also looks like you haven't got g++ installed, so try
```
sudo apt-get install build-essential
``` then run make again.

I installed 'build-essential' and ran 'make' again, but spewed out pages and pages of errors :( It seems that I'm missing a library(s) that prevents me from successfully compiling this program, trouble is **I don't know how to find out which libraries I need** :S

@Chris: I read the relevant parts of the article you linked, and now I know more about the process. THank you :)

EDIT: Here you can see the errors I get when I run 'make': [http://nopaste.info/dea2a49a3f.html](http://nopaste.info/dea2a49a3f.html)

---

### Post by Partyboi2 on 2008-11-04
Looks like you need to install  libpoppler-dev package
```
sudo apt-get install  libpoppler-dev
```

---

### Post by NewWorld on 2008-11-04
Yay, I've solved! I went on IRC and a person named **Striek** has kindly helped me from start to finish. It took about 1-2 hours to figure it all out. So a great big cheer to him.

The reason I couldn't compile was that I didn't have the required libraries. All in all I had to run these commands:

```
sudo apt-get install gimp
sudo apt-get build-dep poppler-utils
sudo apt-get install libpoppler-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install xulrunner-1.9-dev
```

NOTE: I installed the poppler and poppler-utils packages too, they're certainly neccessary for the whole thing to work.

This installed the required libraries for the compile to take place. When it compiles you might get a lot of warning, but as long as there no **errors** it'll compile. Once successful, a new file called "pdftohtml" (no extension) will be created in the directory where your source is.

Now you need to replace the original "pdftohtml" with the newly-compiled one. Go to /usr/bin and make a backup of the "pdftohtml" there (copy paste somewhere else), just in case. Next replace the file in terminal:

```
sudo cp LOCATIONOFNEWFILE LOCATIONOFOLDFILE
```

All done! I had best success with the -noframes and -reflow paramaters, but play around with it and hopefully it'll work ):P

Thanks a lot **Partyboi** for trying to help me <3

---

