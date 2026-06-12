---
title: "Error installing TCL in Ubuntu 10.10"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by Lewke on 2010-09-24
Hi, I&#7743; trying to install TCL 8.0.5 onto my machine, if i type ¨wish¨ it tells me there are already these programs: 
```
 The program 'wish' can be found in the following packages:
 * tk
 * tk8.4
 * tk8.5
 * tk8.3
Try: sudo apt-get install <selected package> 
```

The error trace is here: 
```

luke@luke-laptop:~/Downloads/tcl8.0.5/unix$ ./configure
loading cache ./config.cache
checking for ranlib... ranlib
checking whether cross-compiling... no
checking for getcwd... yes
checking for opendir... yes
checking for strstr... yes
checking for strtol... yes
checking for tmpnam... yes
checking for waitpid... yes
checking for strerror... yes
checking for getwd... yes
checking for wait3... yes
checking for uname... yes
checking for sin... no
checking for -lieee... no
checking dirent.h... yes
checking how to run the C preprocessor... cc -E
checking for errno.h... yes
checking for float.h... yes
checking for values.h... yes
checking for limits.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for sys/wait.h... yes
checking for dlfcn.h... yes
checking for unistd.h... yes
checking termios vs. termio vs. sgtty... termios
checking fd_set and sys/select... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking tm_tzadj in struct tm... no
checking tm_gmtoff in struct tm... yes
checking long timezone variable... yes
checking for st_blksize in struct stat... yes
checking proper strstr implementation... yes
checking for strtoul... yes
checking for strtod... yes
checking for strtod... (cached) yes
checking for Solaris strtod bug... ok
checking for ANSI C header files... yes
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for opendir... (cached) yes
checking union wait... yes
checking matherr support... yes
checking return type of signal handlers... void
checking for vfork... yes
checking vfork/signal bug... ok
checking for strncasecmp... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for gettimeofday declaration... present
checking for -linet... no
checking for net/errno.h... no
checking whether char is unsigned... no
checking signed char declarations... yes
checking for connect... yes
checking for gethostbyname... yes
checking system version (for dynamic loading)... ./configure: 1: Syntax error: Unterminated quoted string


```Really not sure whats wrong, I´m horrible with linux if I´m honest, tried a couple of google searches but didn´t make very much progress. It´s for my final year project so any help would be greatly appreciated.

Thanks :)

---

### Post by mörgæs on 2010-09-24
This is a better forum for 10.10-questions:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Lewke on 2010-09-24
Not sure why it would make a difference with old software but ok. I&#314;l try.

---

