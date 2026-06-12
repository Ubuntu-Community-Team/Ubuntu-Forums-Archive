---
title: "problems installing .run file!?"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by doh224 on 2007-07-03
hi all... 

I have a problem with this file: doom3-linux-1.3.1.1304.x86.run
I can't get it running with the command: 

sudo sh /path/to/doom3-linux-1.3.1.1304.x86.run

any help would be be good. ;) 

-doh

---

### Post by rapolas on 2007-07-03
And that's the problem, what error are you getting?

---

### Post by doh224 on 2007-07-04
> **rapolas said:**
> And that's the problem, what error are you getting?

when type: 

sudo sh path/to/filename.run it says:

sh: Can't open /desktop/doom3-linux-1.3.1.1304.x86.run

??

:(

-doh

---

### Post by scxtt on 2007-07-04
is it executable?

chmod +x doom3-linux-1.3.1.1304.x86.run

---

### Post by doh224 on 2007-07-04
> **scxtt said:**
> is it executable?

chmod +x doom3-linux-1.3.1.1304.x86.run

chmod +x doom3-linux-1.3.1.1304.x86.run
No such file or directory:
then it says it can't find the directory... 
and if I write a directory:
desktop:~$ chmod +x /Desktop/doom3-linux-1.3.1.1304.x86.run
desktop:~$ 
it says nothing??

-akaran

---

### Post by scxtt on 2007-07-04
is this a simple case of not understanding directory structure?

try: **chmod +x ~/Desktop/doom3-linux-1.3.1.1304.x86.run**

~/Desktop and /Desktop are 2 entirely different "places" ...

---

### Post by doh224 on 2007-07-04
> **scxtt said:**
> is this a simple case of not understanding directory structure?

try: **chmod +x ~/Desktop/doom3-linux-1.3.1.1304.x86.run**

~/Desktop and /Desktop are 2 entirely different "places" ...
then is says:

-desktop:~$ chmod +x ~/Desktop/doom3-linux-1.3.1.1304.x86.run
-desktop:~$ 

??

---

### Post by scxtt on 2007-07-04
#-o

the chmod ONLY adds executable permissions to the script you're trying to RUN - you don't get any output and it doesn't actually run the .run file ...

now try: sudo sh ~/Desktop/doom3-linux-1.3.1.1304.x86.run

also, is this file in /Deskop or ~/Desktop?

---

### Post by doh224 on 2007-07-04
> **scxtt said:**
> #-o

the chmod ONLY adds executable permissions to the script you're trying to RUN - you don't get any output and it doesn't actually run the .run file ...

now try: sudo sh ~/Desktop/doom3-linux-1.3.1.1304.x86.run

also, is this file in /Deskop or ~/Desktop?

hey thanks I got it running...

---

