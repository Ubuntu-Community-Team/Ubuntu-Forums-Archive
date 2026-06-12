---
title: "wrong libc.so.6 installed by default?"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by patiobarbecue on 2008-05-05
(1) installed 7.10 i386 on my Dell XPS M1210
(2) sudo apt-get install build-essentials
(3) compiled temp.c using gcc -Wall -g -O2 temp.c
(4) ./a.out shows 
    hello, world again!
    Segmentation fault (core dumped)
(5) gdb shows 0xb7e52d53 in strcat () from /lib/tls/i686/cmov/libc.so.6

temp.c file content:
#include <stdio.h>
#include <string.h>

int main(int argc, char **argv){
  printf("hello, world again!\n");
  printf("%s\n",strcat(argv[1],argv[2]));
}

what's wrong? thanks!

---

### Post by patiobarbecue on 2008-05-05
oh, it works after I reinstalled the build-essential. I close this thread. Thanks.

---

