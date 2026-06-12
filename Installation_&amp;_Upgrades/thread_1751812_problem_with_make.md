---
title: "problem with make"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by priyamvaidya on 2011-05-07
hi

i have downloaded the source package of vim by apt-get source vim.  When i try to compile this by doing [FONT=&quot]/Desktop/vim73/src# make, it is giving the following error 

[/FONT][FONT=&quot]/bin/sh: ./configure: Permission denied  

i am unable to resolve this error.  i am performing  all the commands by su and still i am having error.

the full steps i performed and error i got is depicted below 
[/FONT][HTML]root@maddivenkataraviprasad-Not-Specified:/home/maddivenkataraviprasad# cd Desktop/ 
root@maddivenkataraviprasad-Not-Specified:/home/maddivenkataraviprasad/Desktop# cd vim73 
root@maddivenkataraviprasad-Not-Specified:/home/maddivenkataraviprasad/Desktop/vim73# cd src 
root@maddivenkataraviprasad-Not-Specified:/home/maddivenkataraviprasad/Desktop/vim73/src# make 
rm -f auto/config.status auto/config.cache config.log auto/config.log 
rm -f auto/config.h auto/link.log auto/link.sed auto/config.mk 
touch auto/config.h 
cp config.mk.dist auto/config.mk 
GUI_INC_LOC="" GUI_LIB_LOC="" \ 
CC="" CPPFLAGS="" CFLAGS="" \ 
LDFLAGS="" srcdir="." \ 
./configure \ 
\ 
\ 
\ 
\ 
\ 
\ 
\ 
\ 

/bin/sh: ./configure: Permission denied 
make: *** [config] Error 126 
root@maddivenkataraviprasad-Not-Specified:/home/maddivenkataraviprasad/Desktop/vim73/src# 
 
 [/HTML]please guide me in this.

---

### Post by dino99 on 2011-05-07
bad idea to log as root; and sudo might be help

'sudo apt-get build-dep vim' to get whatever packages are required to compile
vim.


[https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)

---

