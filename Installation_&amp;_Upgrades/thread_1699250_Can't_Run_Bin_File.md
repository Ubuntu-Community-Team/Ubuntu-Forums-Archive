---
title: "Can't Run Bin File"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Tom Ace on 2011-03-03
I'm trying to install ClientAccess.  I just installed Ubuntu a couple days ago.  There is a "setup5250.bin" file.  I go to the directory it's in in Terminal.  I run the command "sudo chmod +x setup.bin", and some other variations.  It asks for the sudo password, and I enter it.  Then it gives me:

chmod: cannot access 'setup5250.bin': No such file or directory

When I do ls or dir, it shows the file in the directory.

Any ideas would be greatly appreciated.

---

### Post by apmcd47 on 2011-03-03
can you show us the result of ```
ls -lb
```please?

Andrew

---

### Post by Tom Ace on 2011-03-03
> **apmcd47 said:**
> can you show us the result of ```
ls -lb
```please?

Andrew

I don't know whether you want all of the results, but here you go:

total 3088
-r-xr-xr-x 1 matt matt  111124 2011-03-03 10:03 colormapper
-r-xr-xr-x 1 matt matt   30820 2011-03-03 10:03 cwbcopwr
-r-xr-xr-x 1 matt matt   36000 2011-03-03 10:03 cwblmsrv
-r-xr-xr-x 1 matt matt   12816 2011-03-03 10:03 cwbmedic
-r-xr-xr-x 1 matt matt    6536 2011-03-03 10:03 cwbnltbl
-r-xr-xr-x 1 matt matt   36752 2011-03-03 10:03 cwbping
-r-xr-xr-x 1 matt matt   31432 2011-03-03 10:03 cwbrunsql
-r-xr-xr-x 1 matt matt   26724 2011-03-03 10:03 cwbtrc
-r-xr-xr-x 1 matt matt  100800 2011-03-03 10:03 helpviewer
-r-xr-xr-x 1 matt matt 1658532 2011-03-03 10:03 ibm5250
-r-xr-xr-x 1 matt matt  338300 2011-03-03 10:03 keymapper
-r-xr-xr-x 1 matt matt  236636 2011-03-03 10:03 keypad
-r-xr-xr-x 1 matt matt   61784 2011-03-03 10:03 miscpref5250
-r-xr-xr-x 1 matt matt  196252 2011-03-03 10:03 playedit
-r-xr-xr-x 1 matt matt   36744 2011-03-03 10:03 printapp
-r-xr-xr-x 1 matt matt   20740 2011-03-03 10:03 rmtcmd
-r-xr-xr-x 1 matt matt   55500 2011-03-03 10:03 rmtodbc
-r-xr-xr-x 1 matt matt  132320 2011-03-03 10:03 setup5250

Does that help?  Thank you for your response.

---

### Post by apmcd47 on 2011-03-03
> **Tom Ace said:**
> I don't know whether you want all of the results, but here you go:

total 3088

[COLOR="Red"]-r-xr-xr-x 1 matt matt  132320 2011-03-03 10:03 setup5250[/COLOR]

Does that help?  Thank you for your response.

There doesn't seem to be a .bin file so the one highlighted above is probably what you need. It is already executable so you can move onto the next step.

It is probably a shell-script, but running```
file setup5250
```will tell you what it is. You should get something like
```
setup5250:       Bourne-Again shell script text executable
```
The shell may not be the same as above. It could be a binary in which case the first word of the description will probably be "ELF". In either case it should be safe to run```
./setup5250
```If it says "ASCII text" or "Commands text" you may need to list it to guess the scripting language, although it is probably a shell-script. If it is, run it with```
bash setup5250
```If it is another scripting language replace the "bash" with the name of the interpreter. If you don't recognise the language paste 20 or so lines here, so other can help. 

Andrew

---

### Post by Tom Ace on 2011-03-03
> **apmcd47 said:**
> There doesn't seem to be a .bin file so the one highlighted above is probably what you need. It is already executable so you can move onto the next step.

It is probably a shell-script, but running```
file setup5250
```will tell you what it is. You should get something like
```
setup5250:       Bourne-Again shell script text executable
```The shell may not be the same as above. It could be a binary in which case the first word of the description will probably be "ELF". In either case it should be safe to run```
./setup5250
```If it says "ASCII text" or "Commands text" you may need to list it to guess the scripting language, although it is probably a shell-script. If it is, run it with```
bash setup5250
```If it is another scripting language replace the "bash" with the name of the interpreter. If you don't recognise the language paste 20 or so lines here, so other can help. 

Andrew

OK, after running the "file setup5250", it gave me:

setup5250: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.4, stripped

When I try running the ./setup5250 command, it gives me:

./setup5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

So, it seems it has to do with a shared library.  I really appreciate your help.  I'm sorry, but I'm very new to all things Linux.  I can try looking for an answer to this particular error message at this point, unless you have an idea.

---

### Post by apmcd47 on 2011-03-03
> **Tom Ace said:**
> OK, after running the "file setup5250", it gave me:


When I try running the ./setup5250 command, it gives me:

```
./setup5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
```

So, it seems it has to do with a shared library.  I really appreciate your help.  I'm sorry, but I'm very new to all things Linux.  I can try looking for an answer to this particular error message at this point, unless you have an idea.

Looks like the *Motif* library to me. You could try installing *openMotif* or *lesstif* (both in the repositories) and try again. The documentation for the application you are trying to install should tell you of any dependencies.

Install with:```
sudo apt-get install libmotif3
```or ```
sudo apt-get install lesstif2
```

Are you trying to install *tn5250*? That is also in the repositories.

Andrew

---

### Post by n8bounds on 2011-05-10
[SIZE="4"]Updated for Natty: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")[/SIZE]

---

