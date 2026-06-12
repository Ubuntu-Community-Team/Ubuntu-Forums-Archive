---
title: "Trying to install pgplot"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Tyson D on 2010-01-13
im using these instructions on how to install pgplot on linux, g77_gcc

[http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html](http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html)

im stuck at the  **""**Use `make' to compile the code""  step because i dont really understand what it is telling me to do.


ive tried typing:

make
make makefile

while in both the source and target directory and nothing happens just some error messages, im not sure at all on what to do, please help.

---

### Post by ajmorris on 2010-01-13
hi there,
can you please post the contents of the Makefile from the source code you're trying to compile. For better legibility, could you please paste it in [code] envelops, or alternatively via pastebin. (at a quick glance of that installation doc you're using, the command 'makemake' in the "Create a makefile" stage should have created the Makefile for use with the compile.)


AJ

---

### Post by Tyson D on 2010-01-13
i have written 

makemake

 and it did in fact create the makefile for the compiler, as for showing you what it is, its rather lengthy and i dont know how to envelop code or even know what pastebin is.

---

### Post by ajmorris on 2010-01-13
> **Tyson D said:**
> i have written 

makemake

 and it did in fact create the makefile for the compiler, as for showing you what it is, its rather lengthy and i dont know how to envelop code or even know what pastebin is.

pastebin is a tool to paste large amounts of text. Its primarily used for places like IRC, but is useful also in situations such as this. go to [http://pastebin.ca]("http://pastebin.ca/").  This will enable you to paste the contents of your Makefile, then you can paste the pastebin link in a reply to this thread.

Also, can you please paste here the error message you receive when running make?

AJ

---

### Post by Tyson D on 2010-01-16
ok the url for my makefile is
 
[http://pastebin.ca/1753233](http://pastebin.ca/1753233)

im guessing putting the makefile in a code envelop would be more efficent then using pastebin so if someone could point me in the right direction on how to do that it would be much appreciated.

---

### Post by Tyson D on 2010-01-16
also this is the error message that appears when i type 

make

g77 -c -u -Wall -fPIC -O /usr/local/src/pgplot/src/pgarro.f
make: g77: Command not found
make: *** [pgarro.o] Error 127

---

### Post by ajmorris on 2010-01-16
> **Tyson D said:**
> also this is the error message that appears when i type 

make

g77 -c -u -Wall -fPIC -O /usr/local/src/pgplot/src/pgarro.f
make: g77: Command not found
make: *** [pgarro.o] Error 127

ah, you need to have the g77 runtime packages installed for gcc.
First make sure you have all the required packages installed for compiling in ubuntu:
```
sudo apt-get install build-essential automake checkinstall
```

also, im not sure whether the g77 runtime libraries are provided as part of the gcc install, if the make still fails with the same error after installing the above, try installing the gfortran package.


However, is there any reason you're using a custom compiled version of pgplot? there is one in the repositories.

> im guessing putting the makefile in a code envelop would be more efficent then using pastebin so if someone could point me in the right direction on how to do that it would be much appreciated.

For code envelops, press the "#" button in the WYSIWYG post editor, or put "CODE" BCC tags around your code, i.e with square brackets.

---

### Post by Tyson D on 2010-01-16
i already have gfortran installed

also this //usr/local/pgplot/src/pgarro.f does not exist on my sytem, if that helps any............

---

### Post by Tyson D on 2010-01-18
bump

---

