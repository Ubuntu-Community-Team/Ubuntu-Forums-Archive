---
title: "Just installed 7.10 gutsy - gcc and g++"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by DesiDude on 2007-11-29
Hi folks
I just installed kubuntu 7.10 gutsy today and I tried compiling a simple hello world program using gcc. 

=====
test.c
=====
#include <stdio>
int main(){
        printf("Hello World\n");
}

But i get the following errors: 
test.c:1:17: error: stdio: No such file or directory
test.c: In function âmainâ:
test.c:3: warning: incompatible implicit declaration of built-in function âprintfâ


I downloaded linux in the hope of learning posix pthread programming (doing it on windows is a pain and very non-standard). However, I seem to be stuck at hello world itself. One would expect that a linux distro would at least have gcc working right out of the box.  I did not have this problem with my previous kubuntu 6.04 (dapper drake).

---

### Post by logos34 on 2007-11-29
You likely need the **build-essential** pkg (for the life of me I don't know why it's not installed by default along with the base system).

---

### Post by brianborchers on 2007-11-29
Pretty basic:
 
#include <stdio.h>

The .h is necessary.

---

### Post by DesiDude on 2007-11-29
> **brianborchers said:**
> Pretty basic:
 
#include <stdio.h>

The .h is necessary.

No - the .h is no longer required when including between the <> brackets.  I just installed the build-essential package and now gcc is working fine.  :-)  Thanks to all those who responded and to the suggestion by logo34.

---

