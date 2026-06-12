---
title: "glibc 2.11 compile problem"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by weishigoname on 2009-12-27
I am using ubuntu 9.10-amd64,my cpu is intel celceron dual-core cpu T3000 . I want to compile glibc2.11 into my computer for my programming .
 when I " ../glibc-2.11/configure --prefix=/usr --with-headers=/usr/src/linux_x86_64/include --enable-add-ons"
there is no error,but it seems can not recognize my cpu type --x86_64-unknow-linux-gnu.
 
when I "make"
got some problems:
            first one is for misc/syslog.c: 
error is unimplemented function syslog(), __vsyslog_chk() called syslog(),error was there,and I change 
syslog() to __syslog().
 
and that get through
 
             second one is for nptl/sysdeps/pthread/pt-longjmp.c :
error is "siglongjmp aliased to undefined longjmp" ( weak_alias(longjmp , siglongjmp) ),actually ,I do not know where weak_alias defined ,I search something and think weak_alias similars to #define ,so I change
 weak_alias(longjmp ,siglongjmp) to #define longjmp siglongjmp ,
and get through.
               third one if for debug/readlink_chk.c and readlinkat_chk.c 
error is  conflicting types of __readlink_chk ,__readlinkat_chk,
I change  
__readlink_chk() to _readlink_chk() in readlink_chk.c
__readlinkat_chk() to _readlink_chk() in readlinkat_chk.c
and get through
    and fourth is  in elf directory 
error is multiple definition of __libc_multiple_libcs  and _dl_addr_inside_object
the associated file dl-open.c dl-sysdep.c dl-addr.c dl-iteratephdr.c dl-sym.c 
for this, I have no idea,and for this error ,I  cleaned the glibc-build directory ,and compiled again ,but the error  just stay here ,I need some advices

---

