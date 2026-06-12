---
title: "C compilation errors!!"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by chandu.ncbs on 2007-09-26
Hi Everyone,
I recently installed ubuntu in my system. I have been struggling to compile a simple c program. It is giving the following error. I am giving both program and error message.

My program

#include <stdio.h>
int main ()
{
   printf ( "chandu\n" );
   return 0;
}//main

Error message 
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

How can I get rid of this problem?

Thanks in advance

Chandu

---

### Post by Lord Illidan on 2007-09-26
You have to install build-essentials from the repositories.

```
sudo apt-get install build-essential
```

---

