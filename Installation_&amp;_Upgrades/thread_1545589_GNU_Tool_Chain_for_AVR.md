---
title: "GNU Tool Chain for AVR"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Gouz on 2010-08-04
Greetings all

I am trying to install the Tool chain for avr
following this link:[http://www.nongnu.org/avr-libc/user-manual/install_tools.html]("http://www.nongnu.org/avr-libc/user-manual/install_tools.html")

I get an error that I need gmp and other things so I try to install them as pointed out in the same web page lower:

Build GMP for MinGW

    * Version 4.2.3
    * <http://gmplib.org/>
    * Build script:

              ./configure  2>&1 | tee gmp-configure.log
              make         2>&1 | tee gmp-make.log
              make check   2>&1 | tee gmp-make-check.log
              make install 2>&1 | tee gmp-make-install.log


the point is that I have no idea in which directory to install the gmp.
Any idea?

thanks :)

---

### Post by Gouz on 2010-08-04
I found it an easy, very easy and nice way to do things

is AVR Plug in from Eclipse

---

