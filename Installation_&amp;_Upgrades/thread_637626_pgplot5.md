---
title: "pgplot5"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by vankampen92 on 2007-12-11
I have installed pgplot5 with synaptic.

Just to see whether the library works, I wanted to compile a demo. I am interested in calling  this library from C, so I try to compile cpgdemo.c and link it as it is explained in the same cpgdemo.c file.

It seems that the installation of pgplot5 does not work out of the box from the last Ubuntu 7.10 relaese, doesn't it?

I have got linking errors. Why? 

Linking errors:
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libfrtbegin.a(frtbegin.o): In function `main':
(.text+0x35): undefined reference to `MAIN__'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_set_PLTE'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_init_io'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_set_text'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_set_tRNS'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_write_info'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_create_write_struct'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_set_IHDR'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_write_end'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_write_row'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libpgplot.so: undefined reference to `png_destroy_write_struct'
collect2: ld returned 1 exit status

Any help??

---

### Post by vankampen92 on 2007-12-12
Let me reply myself!

Although it is true that the compilation of pgplot programs may not work out of the box
in Ubuntu 7.10, the problem it is very easy to solve: some dev libraries should  be added first.

Look at this and you will find help to install pgplot from source, in different distributions, examples of make files and so on:

[http://www.linuxquestions.org/questions/linux-software-2/pgplot-383433/](http://www.linuxquestions.org/questions/linux-software-2/pgplot-383433/)

[http://mypaper.pchome.com.tw/news/yylo/](http://mypaper.pchome.com.tw/news/yylo/)

[http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html](http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html)

This should solve all your pgplot problems concerning installation and compilation of 
the examples. 

Good luck!!

---

### Post by vrangforestillinger on 2008-04-08
Great. Thank you!

---

